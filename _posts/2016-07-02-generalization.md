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

Now we have a top level (software) project: [Metadata Quality Assurance Framework API](http://github.com/pkiraly/metadata-qa-api) 
