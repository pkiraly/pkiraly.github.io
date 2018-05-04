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

I will use R's famous `mtcars` dataset to show the process.

```R
library(tidyverse)
library(jsonlite)
df <- as.tibble(mtcars)
df

df %>% 
  select(1:6) %>% 
  write_csv("cars1.csv", col_names=T)

json <- df %>% 
  select(1,7:12) %>% 
  toJSON()

write(json, file = 'cars2.json')
```
