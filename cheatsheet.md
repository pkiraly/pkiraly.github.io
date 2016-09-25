---
title: How to run the analysis?
layout: post
---

# How to run the analysis? A cheat sheet

```
cd ~/git/europeana-qa-spark
./build
```

run normal analyses

```
nano run-all
	# edit output file resultXX.csv
nohup ./run-all &
```

run frequency and cardinality analyses

```
hdfs dfs -copyLocal result14.csv /join
cd scala
nano cardinality.sh
	# hdfs://localhost:54310/join/resultXX.csv
nohup ./cardinality.sh > cardinality.log
```

run language detection (~ 6 hours)

```
nano run-all-language-detection
	# edit output file resultXX.csv
nohup ./run-all &
nohup ./run-all-language-detection > nohup-result14-language.log &
hdfs dfs -copyLocal result14-language.csv /join
nohup ./language.sh > language.log
```

split files

```
cd ~/git/europeana-qa-r
rm resultXX
ln -s ~/git/europeana-qa-spark/resultXX.csv resultXX.csv
nano split.php
nohup php split.php &&
```

run R

```
rm r-report.txt
rm launch-report.txt
cp master-setlist.txt setlist.txt
crontab -e
	*/1 * * * * cd /path/to/europeana-qa-r && php launcher.php >> launch-report.txt
```
