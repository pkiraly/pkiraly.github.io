---
title:      Report Number Three (Cassandra, Spark and Solr)
layout:     post
date:       2016-01-15 09:50:00
author:     "pkiraly"
customjs:
 - http://code.jquery.com/jquery-1.4.2.min.js
 - http://pkiraly.github.io/js/table.js
---

Changing from Hadoop to Spark, refining mandatory calculation, adding field statistics, storing records 
in Cassandra, indexing with Solr and calculating uniqueness.

<!-- more --> 

## Changing to Spark

Last year I did some Coursera courses on Big Data and Data Science (I recommend you Bill Howe's course 
from the University of Washington if you like to understand theoretical background behind relational databases and
data science, and I don't recommend the courses provided by the University of California San Diego) where I have learnt
about Spark. Spark's big promise is that it is quicker than Hadoop's MapReduce and more memory effective. For me it
was even more important, that I really don't use the "reduce" part of MapReduce, and Spark is fine with that.
The change was not hard at all, since the business logic is separated in different classes to which Hadoop was 
just a client (the only existing client actually, but I planned to add other interfaces). For the same functionality Spark
ran 4 times faster than Hadoop (1.5 hours versus 6 hours). It was a real gain, it means that I can change the codes and
run it again several times a day if I want to implement something new.

## Refining mandatory calculation

Thanks to the feedbacks from the Europeana Data Quality Comittee we improved the mandatory dimension of the 
completeness measure. This tell us how a record fit to the basic Europeanaa Data Model (EDM) schema requirements. Previously
I calculated each field individually, but that was bad: some fields are alternative to each other, so a record is valid if
either dc:title, dcterms:alternative or dc:description is present. Now the mandatory score gives what is expected, and it 
is a real discriminator of bad records.

## Adding field statistics

Now the program assigns 1 if a field is existing and 0 if not for 30+ fields. The R script creates record sets summary
of it, and on the interface I introduces the d3.js data visualization library to display those values. I also introduces 
some filters in the UI: the user can hide those collections which doesn't have a particular field, those in which
every records have it, and those in which some records have it. The user can investigate each fields.

Here is an [example](http://144.76.218.178/europeana-qa/field.php?field=proxy_dcterms_alternative&type=data-providers&exclusions%5B%5D=0&exclusions%5B%5D=1) 
about the dcterms:alternative across data providers.

## Storing records in Apache Cassandra

So far it was a problem, that in the record view of the UI I was nat able to extract an individual record from the 
huge JSON files I stored the data. After sime investigation I choosed Apache Cassandra, which has an interface for 
both Java and PHP. I imported every records to it, but now I still use thhe JSON files stored in HDFS (Hadoop Distributed 
File System) in the Spark analysis. It is on my TODO list to compare the performance if using files and interating over 
every Cassandra records -- my hipothesis is that file based iteration is quicker. Now only the ID and the JSON content is
stored in Cassandra, I am thinking about to store the measurements as well: it would be good if I would like to search for 
each record having a score between say 0.2 and 0.4.

## Uniqueness calculation

I have started investigating the uniqueness or entropy of some selected fields (dc:title, dcterms:alternative 
and dc:description). The basic idea is that if the terms in these fields are frequent accross the records, then 
it is less unique, so less important. If a term is frequent in the same field it is more important than terms 
appear only once. This is called information entropy or in the search engive world TF-IDF formula (term frequency, 
inverse document frequency) -- see [tf-idf](https://en.wikipedia.org/wiki/Tf%E2%80%93idf) Wikipedia article.

The Solr search engine's relevancy ranking mostly based on this formula (however there are lots of tuning 
possibilities, such as give fields weights etc.), but Solr doesn't provide an interface by default for 
extracting the terms TF-IDF score. There is a Term Vector Component however which provides this interface 
given that you apply some additional indexing rules. It is not available in the ordinary Europeana Solr 
setup so I have created a new Solr instance with this special settings, and created a brand new index with 
limited fieldset. (If you want to check how to setup Solr and what interface you can use, check this 
[wiki page](https://cwiki.apache.org/confluence/display/solr/The+Term+Vector+Component).

When the index were created (it took five days, but it is improvable) the scores of a field (in this case the dc:title "Fleming/Mair wedding, Slaithwaite, Huddersfield" -- from the record  [/2022320/3F61C612ED9C42CCB85E533B47367…](http://www.europeana.eu/portal/record/2022320/3F61C612ED9C42CCB85E533B4736795E8BDC7E77.html)) can be read from Solr API in the following form:

      "dc_title_txt":{
        "fleming":{
          "tf":1,
          "df":1073,
          "tf-idf":9.319664492078285E-4
        },
        "huddersfield":{
          "tf":1,
          "df":12073,
          "tf-idf":8.282945415389712E-5
        },
        "mair":{
          "tf":1,
          "df":178,
          "tf-idf":0.0056179775280898875
        },
        "slaithwaite":{
          "tf":1,
          "df":477,
          "tf-idf":0.0020964360587002098
        },
        "wedding":{
          "tf":1,
          "df":10226,
          "tf-idf":9.778994719342852E-5
        }
      ]

Note: I removed some properties Solr reports but irrelevant from our current perspective.

I have extracted these info for the above mentiond three fields, and created two scores: a cumulative 
score which summarizes the all terms in the field, and an average, which is the average of 
the terms' tf-idf score. Those records which don't have the field get 0 for both.

I run the basic statistical analytics (the generation of graphs are on the way), so you can access them 
in the usual web interface:

http://144.76.218.178/europeana-qa/

Select one of the last six dimension to get the results.

