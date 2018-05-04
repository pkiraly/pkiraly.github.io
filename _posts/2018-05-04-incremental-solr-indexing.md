---
title:      Incremental Solr indexing
layout:     post
date:       2018-05-04 00:00:00
author:     "pkiraly"
customjs:
 - http://code.jquery.com/jquery-1.4.2.min.js
 - http://pkiraly.github.io/js/table.js
---

In the Metadata Quality Assurance Framework as a first step we create some CSV files.
The structure of the CSV (in case of Europeana) looks like this:

```
[record ID],[dataset ID],[data provider ID],metric1,metric2,...metricN
[record ID],[dataset ID],[data provider ID],metric1,metric2,...metricN
...
```

<!-- more -->

(Right now we have 5 such files.)

Then we run statistical analyses on these file and we present the result in a web UI. From the web UI it is 
not easy to go back to the records, or at least to figure it out which records have a give value (or range of values).
We get feedbacks from the Data Quality Committee members, that in some cases it would be necessary to check the
records itself.

So what we need is a Solr index which contains all metrics of all records. How to do that? A quick recipie follows.

I will use R's famous `mtcars` dataset to show the process. Solr supports reading from CSV as original data, but doesn't
support it as the source or updating existing records (or document in Solr-speak), so we create two files: one CSV and
a JSON:

```R
library(tidyverse)
library(jsonlite)
df <- as.tibble(mtcars)

df %>%
  select(1:6) %>%
  write_csv("cars1.csv", col_names=T)

json <- df %>%
  select(1,7:12) %>%
  toJSON()

write(json, file = 'cars2.json')
```

The first file contains the first 6 features (columns), the second contains the rest. Since it doesn't have ID, I 
manually added IDs to the files. The final version of the CSV looks like this:

```CSV
1,21,6,160,110,3.9
2,21,6,160,110,3.9
3,22.8,4,108,93,3.85
4,21.4,6,258,110,3.08
5,18.7,8,360,175,3.15
6,18.1,6,225,105,2.76
7,14.3,8,360,245,3.21
8,24.4,4,146.7,62,3.69
9,22.8,4,140.8,95,3.92
```

The final version of JSON looks like this:

```JSON
[{"id":1,"wt_f":{"set":2.62},"qsec_f":{"set":16.46},"vs_f":{"set":0},"am_f":{"set":1},"gear_f":{"set":4},"carb_f":{"set":4}},
{"id":2,"wt_f":{"set":2.875},"qsec_f":{"set":17.02},"vs_f":{"set":0},"am_f":{"set":1},"gear_f":{"set":4},"carb_f":{"set":4}},
{"id":3,"wt_f":{"set":2.32},"qsec_f":{"set":18.61},"vs_f":{"set":1},"am_f":{"set":1},"gear_f":{"set":4},"carb_f":{"set":1}},
{"id":4,"wt_f":{"set":3.215},"qsec_f":{"set":19.44},"vs_f":{"set":1},"am_f":{"set":0},"gear_f":{"set":3},"carb_f":{"set":1}},
{"id":5,"wt_f":{"set":3.44},"qsec_f":{"set":17.02},"vs_f":{"set":0},"am_f":{"set":0},"gear_f":{"set":3},"carb_f":{"set":2}},
{"id":6,"wt_f":{"set":3.46},"qsec_f":{"set":20.22},"vs_f":{"set":1},"am_f":{"set":0},"gear_f":{"set":3},"carb_f":{"set":1}},
{"id":7,"wt_f":{"set":3.57},"qsec_f":{"set":15.84},"vs_f":{"set":0},"am_f":{"set":0},"gear_f":{"set":3},"carb_f":{"set":4}},
{"id":8,"wt_f":{"set":3.19},"qsec_f":{"set":20},"vs_f":{"set":1},"am_f":{"set":0},"gear_f":{"set":4},"carb_f":{"set":2}},
{"id":9,"wt_f":{"set":3.15},"qsec_f":{"set":22.9},"vs_f":{"set":1},"am_f":{"set":0},"gear_f":{"set":4},"carb_f":{"set":2}}]
```

As you can see the JSON contains an array of document, where id is the record identifier. The rest of the fields have the following syntax

```
"[name]":{"[command]":[value]}
```

In our case the command is always `set` but there are number of other command of your use case is not to add a single value (consult the Solr manual [here](https://lucene.apache.org/solr/guide/7_2/updating-parts-of-documents.html)). We use `_f` suffix everywhere, which denotes a single float value dynamic field, this way we don't have to touch Solr's `schema.xml` file (or any other configuration).

We have the files prepared. its time to index:

```
curl 'http://localhost:8984/solr/qa-2018-03/update?commit=true&header=false&fieldnames=id,mpg_f,cyl_f,disp_f,hp_f,drat_f' \
  --data-binary @/path/to/cars1.csv \
  -H 'Content-type:application/csv'
```
We set `header` false to not take the first line of CSV as header, and put the field names explicitly in the `fieldnames` parameter.

```
curl http://localhost:8984/solr/qa-2018-03/update?commit=true \
  --data-binary @/path/to/cars2.json \
  -H 'Content-type:application/json'
```

So the task is (which is missing from this piece) is to transform the CSV files (except the one we are starting with) to Solr compatible JSON update files.

ps. I would like to thank to Mark Philips, who showed me the University of North Texas metadata management tool, in which
the metrics are stored in Solr alogside the original metadata values, so they can easily find examples for given 
metadata problems.