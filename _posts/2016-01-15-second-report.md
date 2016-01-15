---
title:      Report Number Two (Finishing harvest)
layout:     post
date:       2016-01-15 09:50:00
author:     "pkiraly"
---

The second report describing the process of harvest with tricks and tips, the running 
of full 'completeness' analyses, and the first visible results.

<!-- more --> 

## Harvesting

During the autumn Europeana launched its OAI-PMH server, and I started usingit intensively. I have created a [client project](https://github.com/pkiraly/europeana-oai-pmh-client) for harvesting all records. Soon it turned out, that sometimes the server is not responsive because it losts connection to the Solr server behind. Once the connection is lost we can not really continue the harvest. I modified the client to give another tries, so it tries 4 times in case of errors. It turned out, that it is not enough, there are cases when even the 4th try were failed. With this approach I were able to harvest about 10 million record the maximum, and it took several days. Even it it would have gone smoothly the total harvest would have taken about 13 days. It turned out however that the OAI-PMH service supports sets, and each OAI-PMH set correcpond to a Europeana dataset or collection, which is a unit of ingestion. (Europeana has a roughly monthly cycle of data ingestion where it collects the data from the intermediate level data aggregators. The data aggregators collect data from data providers - the institutions who own or curate the digitized objects and create theirs metadata records.)

I followed a new approach: harvesting by sets instead of the whole database. It has the advantage that if it fails, you don't loose everything, and another one: it can be run parallely, harvesting different datasets in different threads. I have implemented it in a very simple way. A text file contained all the dataset names one in a line. There were a dispatcher script which were called in every minute by cron, which checked how many harvester is running (`ps aux | grep "[o]ai2json.php" | wc -l`), and if it is less than the maximum slots available, it picked up the top line, and launched a new harvester with the name of the dataset. It worked well, but not perfectly. It turned out, that when the client almost reached the supposed end of harvest (unfortunatelly the OAI-PMH server doesn't tell you the total number of records, but you can figure it out with the help of Europeana REST API by facetting for europeana_collectionName field [here](http://www.europeana.eu/api/v2/search.json?wskey=api2demo&query=*&facet=europeana_collectionName&profile=facets&rows=0)) it starts responding without giving back any record, but keep containing resumption tokens (which is the standard's signal denoting, that there are more record - if there is no resumption token in the response it means, that it is the end of the harvest). For each set there were thousands of so empty response before the actual ending of the harvest, and the harvested number of records did not correspond to the number reported by the API. And there were another problem as well: if a set name contains some special characters (space, ampresand or UTF-8 characters) the server gives back an error.

When I reported these problems to Europeana they were nice enough to send me the list of IDs of all Europeana records. The approach this time were to compare the IDs of the downloaded records with this ID list, and harvesting individual records by their identifiers. This went perfectly, but more slower than the previous methods.

At the end I had a bit more than 47 million records in JSON. JSON? How it comes, since OAI-PMH returns XML? Well, that's true, but JSON is a more compact format, requires less space, and since I started with the REST API, which produces JSON response and space is a critical issue for me, I decided not to save the XML response but transform each records to JSON files as one record per line, each file represents a dataset. The total size takes roughly 400 GB.

## Measuring completeness

## Statistical analyses

## Web interface

## Important links

* [Quality reports](http://141.5.103.129/europeana-qa/index.html)
* [Harvester client project](https://github.com/pkiraly/europeana-oai-pmh-client)
* [Measurement project](https://github.com/pkiraly/europeana-qa)
* [Analysis project](https://github.com/pkiraly/europeana-qa-r)
* [Web interface project](https://github.com/pkiraly/europeana-qa-web)
