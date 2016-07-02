---
title:      Making General
layout:     post
date:       2016-07-02 12:25:00
author:     "pkiraly"
customjs:
 - http://code.jquery.com/jquery-1.4.2.min.js
 - http://pkiraly.github.io/js/table.js
---

In the last weeks I was working on making the framework really general and reusable
in other project.  The initiative came from Europeana.  They would like to build in
the measurement into their ingestion service.  It was a good occasion to separate
different concerns of the source code.

<!-- more --> 

## Reorganization of the software

Now we have a top level (software) project: [Metadata Quality Assurance Framework API](http://github.com/pkiraly/metadata-qa-api). It contains the actual measurements,
and definition of the workflow. It also contains examples of metadata schema
abstractions. It is called API, because it is a Java API, and other projects use
this API in different context (for example in Apache Spark, command line interface,
or a REST API).

The second project is the [Europeana Quality Assurance API](http://github.com/pkiraly/europeana-qa-api).
It contains Europeana-related extension to the Metadata QA API.  Similar projects
will be writen to handle other cultural heritage metadata schemas, such as MARC,
DPLA schema, EAD and others.  I have started working with records come from an
OAI-PMH service, and now I have to work with records stored in MongoDB. Thes have
the same big structure, but have different naming conventions: OAI-PMH uses
qualified XML names, such as dc:title, while the MongoDB records follow the
camel-case naming convention, such as dcTitle.

