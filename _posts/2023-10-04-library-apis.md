---
title:      Library APIs
layout:     post
date:       2023-10-04 00:00:00
author:     "pkiraly"
customjs:
 - http://code.jquery.com/jquery-1.4.2.min.js
 - http://pkiraly.github.io/js/table.js
---

Libraries provide different application programming interfaces (APIs) that allow users to access library data programmatically, e.g. via a script. The APIs can be implementation of widely used specifications, which are available in many libraries, or custom interfaces which are available in particular institutions. APIs have three important layers: 

<!-- more -->

1. the specification of the service. It describes how the data can be accessed (in some cases also how to create, modify or delete), whether the particular _call_ (an individual functionality of the service) requires authentication and authorization.
2. client libraries for particular language and tools that work on the command line or have a graphical user interface
3. the access points and terms of use at a particular library. 

Some of the most important standardised APIs are:

* [Open Archives Initiative Protocol for Metadata Harvesting](https://www.openarchives.org/pmh/) (OAI-PMH) provides a mechanism to iterate over predefined sets of records. The sets are created by the libraries. It does not provide searches, but the implementation might provide information of the changes of the database. In the jargon the activity of using OAI-PMH is called "harvesting".
* [Information Retrieval (Z39.50): Application Service Definition and Protocol Specification](https://www.loc.gov/z3950/agency/) is an older standard, and implemented in almost all cataloguing systems, however its access point is not always public. Most of the libraries set some limitations, so one can not download an arbitrary number of records. It provides search possibilities via a peculiar query language.
* [SPARQL Protocol and RDF Query Language](https://www.w3.org/TR/sparql11-overview/), a communication protocol and a query language for RDF graphs (linked data). We live in a transition period from MARC-based or MARC-like pre-coordinated metadata schemas to post-coordinated and open linked data graphs. SPARQL defines how these graphs can be searched and retrieved. 
* [Cool URIs for the Semantic Web](https://www.w3.org/TR/cooluris/) is a simple API describing how to access different representations of the resource.
* [Signposting](https://signposting.org/) provides a mechanism to specify links between scholarly papers, its metadata, landing page, authors, and different formats.

Most of the library cataloguing system vendors include API to their products, but sometimes mainly for helping the work of librarians, not created for end users. The large libraries and library consortia also provide custom APIs, such like [Europeana](https://pro.europeana.eu/page/apis), [Digital Public Library of America](https://dp.la/guides/for-developers), [Library of Congress](https://www.loc.gov/apis/), [OCLC WorldCat](https://developer.api.oclc.org/wcv2)