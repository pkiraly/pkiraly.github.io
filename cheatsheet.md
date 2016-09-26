---
title: How to run the analysis?
layout: post
---

# How to run the analysis? A cheat sheet

<img src="{{ site.url }}/img/process-workflow.png" class="big" title="Process workflow" alt="Process workflow" />


## Preparation

```
cd ~/git
git clone https://github.com/pkiraly/metadata-qa-api.git
git clone https://github.com/pkiraly/europeana-qa-api.git
git clone https://github.com/pkiraly/europeana-qa-spark.git
git clone https://github.com/pkiraly/europeana-qa-r.git
git clone https://github.com/pkiraly/europeana-qa-web.git /var/www/html/europeana-qa
```

## Build the sources

```
cd ~/git/europeana-qa-spark
./build
```

## Run normal analyses

```
nano run-all
	# edit output file resultXX.csv
nohup ./run-all &
```

## Run frequency and cardinality analyses

```
hdfs dfs -put result14.csv /join
cd scala
nano cardinality.sh
	# hdfs://localhost:54310/join/resultXX.csv
nohup ./cardinality.sh > cardinality.log
```

## Run language detection (~ 6 hours)

```
nano run-all-language-detection # edit output file resultXX.csv
nohup ./run-all &
nohup ./run-all-language-detection > nohup-result14-language.log &
hdfs dfs -put result14-language.csv /join
nohup ./language.sh > language.log
```

## Split files

```
cd ~/git/europeana-qa-r
rm resultXX
ln -s ~/git/europeana-qa-spark/resultXX.csv resultXX.csv
nano split.php
nohup php split.php &&
```

## Run R analysis

```
rm r-report.txt
rm launch-report.txt
cp master-setlist.txt setlist.txt
crontab -e
  */1 * * * * cd /path/to/europeana-qa-r && php launcher.php >> launch-report.log
```
