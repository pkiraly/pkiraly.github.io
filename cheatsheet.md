---
title: How to run the analysis?
layout: post
---

# How to run the analysis? A cheat sheet

<img src="{{ site.url }}/img/process-workflow.png" class="big" title="Process workflow" alt="Process workflow" />


## Preparation

### Get softwares

```
cd ~/git
git clone https://github.com/pkiraly/metadata-qa-api.git
git clone https://github.com/pkiraly/europeana-qa-api.git
git clone https://github.com/pkiraly/europeana-qa-spark.git
git clone https://github.com/pkiraly/europeana-qa-r.git
git clone https://github.com/pkiraly/europeana-qa-web.git /var/www/html/europeana-qa
```

### Build the codes

```
cd ~/git/europeana-qa-spark
./build
```

### Prepare data sources on HDFS

```
hdfs dfs -mkdir /europeana
hdfs dfs -mkdir /join
hdfs dfs -put /path/to/sources/*.json /europeana
```

## Measurement of main features

### Run record level measurement (~ 3:13)

```
cd ~/git/europeana-qa-spark
nohup ./run-all resultXX.csv > run-all.log &
```

### Upload result file to HDFS (~ 0:12)

```
cd ~/git/europeana-qa-spark
hdfs dfs -put resultXX.csv /join
```

### Run top level frequency and cardinality analyses (~ 0:08)

```
cd ~/git/europeana-qa-spark/scala
nohup ./cardinality.sh resultXX.csv > cardinality.log &
```

### Convert top level cardinality csv to json

```
cd ~/git/europeana-qa-spark/script
php cardinality-csv2json.php
cp cardinality.json ~/git/europeana-qa-r/json2
```

### Convert top level frequency .csv to .json

```
cd ~/git/europeana-qa-spark/script
php frequency-csv2json.php
cp frequency.json ~/git/europeana-qa-r/json2
```

### Split files result.csv to to collection level .csv files (~ 1:31)

```
cd ~/git/europeana-qa-r
rm resultXX
ln -s ~/git/europeana-qa-spark/resultXX.csv resultXX.csv
nohup php split.php resultXX.csv &
```

### Run collection level analysis (~ 17:17)

```
cd ~/git/europeana-qa-r
rm r-report.txt
rm launch-report.txt
cp master-setlist.txt setlist.txt
crontab -e
  */1 * * * * cd /path/to/europeana-qa-r && php launcher.php >> launch-report.log
```

## Measurement of multilinguality

### Run record level language detection (~ 5:14)

```
cd ~/git/europeana-qa-spark
nohup ./run-all-language-detection resultXX-language.csv > nohup-result14-language.log &
```

### Upload result file to HDFS (~ 0:16)

```
cd ~/git/europeana-qa-spark
hdfs dfs -put resultXX-language.csv /join
```

### Top level language measurement (~ 0:26)

```
cd ~/git/europeana-qa-spark/scala
nohup ./languages.sh resultXX-language.csv > languages.log &
```

### Collection level language measurement (~ 0:46)

```
cd ~/git/europeana-qa-spark/scala
nohup ./languages-per-collections.sh resultXX-language.csv > languages-per-collections.log &
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

## Measurement of multilingual saturation

### Run record level multilingual saturation (~ 8:41)

```
cd ~/git/europeana-qa-spark
nohup ./run-all-multilingual-saturation resultXX-multilingual-saturation.csv > multilingual-saturation.log &
```

### Upload result file to HDFS (~ 0:16)

```
cd ~/git/europeana-qa-spark
hdfs dfs -put resultXX-multilingual-saturation.csv /join
```

### Top level multilingual saturation measurement (~ 0:8)

```
cd ~/git/europeana-qa-spark/scala
nohup ./saturation.sh resultXX-multilingual-saturation.csv > resultXX-multilingual-saturation.log &
```

### Split files resultXX-multilingual-saturation.csv to to collection level .csv files (~ 1:31)

```
cd ~/git/europeana-qa-r
rm resultXX
ln -s ~/git/europeana-qa-spark/resultXX-multilingual-saturation.csv resultXX-multilingual-saturation.csv
nohup php split-saturation.php resultXX-multilingual-saturation.csv &
```

### Collection level multilingual saturation measurement (~ 7:29)

```
cd ~/git/europeana-qa-r
./prepare.sh saturation
crontab -e
  */1 * * * * cd /path/to/europeana-qa-r && php saturation-launcher.php >> launch-report.log
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

Total time: 29 hours 3 minutes.
