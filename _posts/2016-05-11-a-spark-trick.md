---
title:      A poor man's join in Apache Spark
layout:     post
date:       2016-05-11 09:50:00
author:     "pkiraly"
customjs:
 - http://code.jquery.com/jquery-1.4.2.min.js
 - http://pkiraly.github.io/js/table.js
---

There API functions for joining two CSV files in Apache Spark, but it turned out, they are requires more robust machines than I have access to, so I had to do some tricks to achive the goal.

<!-- more --> 

## The problem

In the project I measure different features of records in order to find a way to make distinction between the "good" and the "bad" records. The features are the existence of the fields, the cardinality, length, the uniqueness of the terms in the field, the existence of particular known problems. The field's term uniqueness measurement is based on the Term Frequency-Inverse Document Frequency algorithm and requires a special Solr instance and to measure 3 fields in all the records took 2 days. The rest of the measures took two hours. Since the records are not changing, however I constanly improve the measurement techniques and add new metrics, it would be a huge vaste of time to run the measurement for two days instead of 2 hours, I decided to skip the uniqueness measurement, and merge the new result with the fields from the old result.

The result is a CSV file, it contains a record ID, the numeric score of the metrics and some other fields used in the analization phase. With SQL it would be a simple `JOIN` command, and after some investigation I found that Spark also has a `join()` method, all you have to do is to is to turn the default Resilient Distributed Dataset (`RDD`) to a special subtype called `PairRDD`, where the pair means that it is a hash-table like structure: pairs of a key and a value. In our case the key is the record ID, and the value is what we would like to join: the full row from the new result, and the uniqueness metrics from the old result.

## Size matters

Theoretically this was a nice idea, but I run into a practical problem: when I joined the two RDDs I always run into out of memory exceptions. Each files have 46M rows, and the size of the raw CSV files are 12 GB. I've started to do some optimization. The first step was to extract the record identifier and the uniqueness scores from the old result, and saving into a new file (`tfidf.csv`). It became 4 GB, so I get rid of 8 GB, but the exception occured again. The IDs in the dataset has a nice feature: they are not random, and each ID starts with the caracters "0", "1", "2" or "9". This feature enables us to apply a  filter, and join smaller chunks. Unfortunatelly it did not helped, it worked only for very small chunks of records.

## Enters union() and groupByKey()

Since my problem is really a MapReduce problem, I tried the combination of `union()` and `groupByKey()` function. `union()` takes two `RDDs` and concatenates them. `groupByKey()` finds the identical keys, and group the individual values into a list. Then you should work on the elements of the list to create a single value again, and save the file.

This approach is more memory effective, but I was not able to run on more than 10 million records. I did not mentioned so far that this machine is not dedicated to Spark processes. It runs several other services, and the memory consumption of those affects the performance of Spark. At the end I had to play with the data to find the chuncks which do not throws out of memory errors. Since this process creates a number of smaller files instead of one big file, outside of Spark we have to merge them.

The final Scala code is here:

    # preprocessing the uniqueness file
    val tfidfFile = sc.textFile("hdfs://localhost:54310/join/tfidf.csv").filter(_.nonEmpty)
    val tfidf = tfidfFile.map(line => line.split(","))
                          # 0th element is the record identifier that will be the key
                          # the rest are the metrics, those will be the value
                          .map(x => (x(0), x(1) + "," + x(2) + "," + x(3) + "," + x(4) + "," + x(5) + "," + x(6)))
    tfidf.cache()

    # preprocessing the result file
    val csv = sc.textFile("hdfs://localhost:54310/join/result.csv").filter(_.nonEmpty)
    val data = csv.map(line => line.split(","))
                  # here the 2nd element is the record id
                  .map(x => (x(2), x.mkString(",")))
    data.cache()

    def selectAndSave(filt:String) = {
      val tfidfFiltered = tfidf.filter(x => x._1.startsWith(filt))
      val dataFiltered = data.filter(x => x._1.startsWith(filt))
      val united = dataFiltered.union(tfidfFiltered)
      val merged = united.groupByKey()
        .map(x => 
          if (x._2.toList.head.length > x._2.toList.last.length) {
            x._2.toList.mkString(",")
          } else {
            x._2.toList.last + "," + x._2.toList.head
          }
        )
      merged.saveAsTextFile("hdfs://localhost:54310/join/merged-" + filt + ".csv")
    }
