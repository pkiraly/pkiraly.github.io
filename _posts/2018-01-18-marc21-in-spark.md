---
title:      Running MARC21 analysis in Spark
layout:     post
date:       2018-01-18 00:00:00
author:     "pkiraly"
customjs:
 - http://code.jquery.com/jquery-1.4.2.min.js
 - http://pkiraly.github.io/js/table.js
---

So far I have worked with MARC21 files in a standalone manner. Now it is time to run MARC analysis in Apache Spark.

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
From the user's perspect the important thing is to know how to run it:

```bash
spark-submit \
  --class de.gwdg.metadataqa.marc.cli.spark.ParallelValidator \
  --master local[*] \
  target/metadata-qa-marc-0.2-SNAPSHOT-jar-with-dependencies.jar \
  /path/to/\*-line-separated.mrc \
  output.txt
```
