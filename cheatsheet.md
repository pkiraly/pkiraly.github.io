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

## Build the codes

```
cd ~/git/europeana-qa-spark
./build
```

## Measurement of main features

### Run record level measurement (~ 7:40)

```
cd ~/git/europeana-qa-spark
nano run-all
	# edit output file resultXX.csv
nohup ./run-all > run-all.log &
```

### Run frequency and cardinality analyses

```
cd ~/git/europeana-qa-spark
hdfs dfs -put result14.csv /join

cd ~/git/europeana-qa-spark/scala
nano cardinality.sh
	# hdfs://localhost:54310/join/resultXX.csv
nohup ./cardinality.sh > cardinality.log
```

### Split files

```
cd ~/git/europeana-qa-r
rm resultXX
ln -s ~/git/europeana-qa-spark/resultXX.csv resultXX.csv
nano split.php
nohup php split.php &&
```

### Run R analysis

```
cd ~/git/europeana-qa-r
rm r-report.txt
rm launch-report.txt
cp master-setlist.txt setlist.txt
crontab -e
  */1 * * * * cd /path/to/europeana-qa-r && php launcher.php >> launch-report.log
```

## Measurement of multilinguality

### Run record level language detection (~ 6 hours)

```
cd ~/git/europeana-qa-spark
nano run-all-language-detection # edit output file resultXX.csv
nohup ./run-all-language-detection > nohup-result14-language.log &
hdfs dfs -put result14-language.csv /join
nohup ./language.sh > language.log
```

### Top level language measurement (~ 26 mins)

```
cd ~/git/europeana-qa-spark/scala
nano languages.sh
nohup ./languages.sh > languages.log &
```

### Collection level language measurement (~ 46 mins)

```
cd ~/git/europeana-qa-spark/scala
nano languages-per-collections.sh
nohup ./languages-per-collections.sh > languages-per-collections.log &
```

### Convert top level language results to JSON file

```
cd ~/git/europeana-qa-spark/scripts
php languages-csv2json.php
cp languages.json ~/git/europeana-qa-r/json2/
```

### Convert collection level language results to JSON files

```
cd ~/git/europeana-qa-spark/scripts
php lang-group-to-json.php 
```
