---
title:      Report Number Three (Cassandra, Spark and Solr)
layout:     post
date:       2016-04-09 09:50:00
author:     "pkiraly"
customjs:
 - http://code.jquery.com/jquery-1.4.2.min.js
 - http://pkiraly.github.io/js/table.js
---

Changing from Hadoop to Spark, refining mandatory calculation, adding field statistics, storing records 
in Cassandra, indexing with Solr and calculating uniqueness.

<!-- more --> 

## Changing to Spark

Last year I did some Coursera courses on Big Data and Data Science (I recommend you [Bill Howe's course](https://www.coursera.org/learn/data-manipulation){:target="_blank"} 
from the University of Washington if you like to understand theoretical background behind relational databases and
data science, and I don't recommend [these courses](https://www.coursera.org/specializations/big-data){:target="_blank"}
provided by the University of California San Diego) where I have learnt
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

The usage of the fields accross all the records:

<img src="{{ site.url }}/assets/field-frequency.png" class="real" title="Field frequency" alt="Field frequency" />

The usage of dcterms:alternative in those data providers, which uses it in some of the records, but not in all:

<img src="{{ site.url }}/assets/field-alternative-per-data-providers.png" class="real" title="dcterms:alternative frequency" alt="dcterms:alternative frequency" />

An [example](http://144.76.218.178/europeana-qa/field.php?field=proxy_dcterms_alternative&type=data-providers&exclusions%5B%5D=0&exclusions%5B%5D=1){:target="_blank"}
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
inverse document frequency) -- see [tf-idf](https://en.wikipedia.org/wiki/Tf%E2%80%93idf){:target="_blank"} Wikipedia article.

The Solr search engine's relevancy ranking mostly based on this formula (however there are lots of tuning 
possibilities, such as give fields weights etc.), but Solr doesn't provide an interface by default for 
extracting the terms TF-IDF score. There is a Term Vector Component however which provides this interface 
given that you apply some additional indexing rules. It is not available in the ordinary Europeana Solr 
setup so I have created a new Solr instance with this special settings, and created a brand new index with 
limited fieldset. (If you want to check how to setup Solr and what interface you can use, check this 
[wiki page](https://cwiki.apache.org/confluence/display/solr/The+Term+Vector+Component){:target="_blank"}.

When the index were created (it took five days, but it is improvable) the scores of a field (in this case the dc:title "Fleming/Mair wedding, Slaithwaite, Huddersfield" -- from [this record](http://www.europeana.eu/portal/record/2022320/3F61C612ED9C42CCB85E533B4736795E8BDC7E77.html){:target="_blank"}) can be read from Solr API in the following form:

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
    }

Note: I did not applied truncation and other fancy Solr analyzes on the fields, it is only the lower case transformation
applied. The API returns the stored terms in alphabetical order. I removed some properties Solr reports but 
irrelevant from our current perspective.

I have extracted these info for the above mentiond three fields, and created two scores: a cumulative 
score which summarizes the all terms in the field, and an average, which is the average of 
the terms' tf-idf score. Those records which don't have the field get 0 for both.

<img src="{{ site.url }}/assets/uniquness.png" class="real" title="Uniqueness" alt="Uniquenes" />

The graphs visualize the average uniqueness of terms in the field. You can see that - as expected - there are lots of records where this value is quite low - it means that the words of the title are usually common words. There are however some titles which have unique words. If the value is higher than 1, it means that a unique word appears multiple times in this field (unique means that it appears in only one record). In this particularly record set there is no such an example, but there are others, such as "Doog, Doog, Doog, Doog" (an indian one) or "Csalo! Csalo!" (a Hungarian one). In this particular dataset the most unique title is "Iganteçtaco pronoua, eta hilen pronoua." in which "eta" is a common term, "hilen" and "Iganteçtaco" is unique, and "pronoua" is repeated unique.

In order to make comparision of the scores and the record, a two new features were added to the record view.

The first one is the term frequency viewer. Here you can see the terms stored, the term frequency (how many times the term appears in the current field instance), the document frequency (how many document has this term in this field) and the tf-idf scores Solr calculated.

<img src="{{ site.url }}/assets/term-frequencies.png" class="real" title="Term frequencies" alt="Term frequencies" />

The second one is a "naked" record view: it displays the non technical fields of the `ore:Aggregation` and `ore:Proxy` of the record. Those fields which are not analyzed in the current session (such as tableOfContents) are displayed in grey.

<img src="{{ site.url }}/assets/record-view.png" class="real" title="Record view" alt="Record view" />

You can access thhe UI in the usual web interface:

http://144.76.218.178/europeana-qa/

Select one of the last six dimension to get the results.

## Events, presentation, article

The big news is that the Europeana [Data Quality Committee](http://pro.europeana.eu/page/data-quality-committee){:target="_blank"} as a Europeana Network and EuropeanaTech Working Group is formed in March. It is a great honor, that I was involved. We have a quite active message board, a bi-weekly teleconference and a bi-yearly face-to-face meeting.

<img src="{{ site.url }}/assets/gwdg-nachrichten.png" class="real" title="GWDG Nachrichten" alt="GWDG Nachrichten" />

I wrote an [article for GWDG Nachrichten](https://www.gwdg.de/documents/20182/27257/GN_3-2016_www.pdf){:target="_blank"} about the metadata quality issues in Europeana covering the roles of the Data Quality Committee, and Mr Yahyapour, the director of GWDG wrote a recommendation in the editorial column. The GWDG Nachrichten is circulated in the Göttingen Campus and in Max Planck Institutes.

<img src="{{ site.url }}/assets/networkshop.png" class="real" title="networkshop" alt="networkshop" />

I presented the research in Networkshop 2016 conference at the end of March in my home town. It was exceptional for me that I talked at the Auditorium Maximum of the University of Debrecen where I saw soo many unforgottable concerts, movies and speachhes as a teenager. Unfortunatelly I was the very last speaker on that day, and there were no time left for discussions. Here you can see [the slides](http://www.slideshare.net/pkiraly/a-jk-s-a-rosszak-metaadatok-minsgellenrzse){:target="_blank"} (note: they are in Hungarian).
