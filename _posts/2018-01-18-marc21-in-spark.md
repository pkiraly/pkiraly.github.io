---
title:      Running MARC21 analysis in Spark
layout:     post
date:       2018-01-18 00:00:00
author:     "pkiraly"
customjs:
 - http://code.jquery.com/jquery-1.4.2.min.js
 - http://pkiraly.github.io/js/table.js
---

So far I have worked with MARC21 files in a standalone manner. Now it is time to run MARC analysis in Apache Spark. Here I describe only the first steps, the tool is not ready to run all the analysis which is possible with the standalone manner.

<!-- more --> 

If we the source of the Spark analysis is a file, Spark reads the file in a line-by-line manner. Unual MARC21 files
are big files with thousands or million records in one line. The record separator character is not a line ending character,
but the (in hexadecimal notation) `1d` character. The MARC validation tool so far accepts one or more file names as input.
In a Spark context we have to do two steps:

* change MARC files that they contain each record in a separate line
* change code to accept binary string instead of file name

The first step can be done with one line of Bash code:

```bash
sed 's/\x1d/\x1d\n/g' marc.mrc > marc-line-separated.mrc
```

If you have several files, put it into a loop:

```bash
FILE=*.mrc

for IN in $FILE; do
  OUT=$(echo $IN | sed 's/.mrc/-line-separated.mrc/')
  sed 's/\x1d/\x1d\n/g' $IN > $OUT
done
```

I don't describle the process of the second step, it took an hour or two to adapt the code to work in Spark environment.
From the user's perspect the important thing is to know how to run it.

## Runniing in a local file system

1) Make sure `HADOOP_CONF_DIR` is not set. If it is set Spark would like to communicate with Hadoop File System, 
and it is not running, the whole process will stop.

```bash
echo $HADOOP_CONF_DIR
```
if it returns anything else than an empty line, unset it:

```bash
unset HADOOP_CONF_DIR
```

2) Run analysis!

```bash
spark-submit \
  --class de.gwdg.metadataqa.marc.cli.spark.ParallelValidator \
  --master local[*] \
  target/metadata-qa-marc-0.2-SNAPSHOT-jar-with-dependencies.jar \
  /path/to/\*-line-separated.mrc \
  output
```

It is important to escape asteriks with the backslash character (`\*`), this guarantees, that the shell will 
not substitutes that line with the names of all the files matches the pattern.

3) Retrieve output:

The output is a directory, you can extract the results into a single file with the following command:

```bash
cat output/part-* > output.csv
```

## Running with Hadoop

1) Upload files to Hadoop file system:

```bash
hdfs dfs -put /path/to/\*-line-separated.mrc /marc
```
This will upload the files into the /marc directory of Hadoop FS.

2) Make sure that `HADOOP_CONF_DIR` is set (we unset it in the local file system example):

```bash
echo $HADOOP_CONF_DIR
```
if it return empty line, it means it is not set, so set it:

```bash
export HADOOP_CONF_DIR=$HADOOP_INSTALL/etc/hadoop
```

3) Run analysis!

```bash
unset 
spark-submit \
  --class de.gwdg.metadataqa.marc.cli.spark.ParallelValidator \
  --master local[*] \
  target/metadata-qa-marc-0.2-SNAPSHOT-jar-with-dependencies.jar \
  hdfs://localhost:54310/marc21/*-line-separated.mrc \
  hdfs://localhost:54310/output \
```

4) Retrieve output:

```bash
hdfs dfs -getmerge /marc21/* output.csv
```
