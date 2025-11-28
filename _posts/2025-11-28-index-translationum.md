---
title:      Fetching Index Translationum
layout:     post
date:       2025-11-28 00:00:00
author:     "pkiraly"
customjs:
 - http://code.jquery.com/jquery-1.4.2.min.js
 - http://pkiraly.github.io/js/table.js
---

This is a very short introduction how to fetch data from UNESCO's Index Translationum (IT) programmatically, however without too much software code. IT does not provide an API, so one has to mimic the clicks, and analyse the HTML content of the page. IT neither provides browse functionalities, so one should start with a query.

<!-- more -->

In my practice I worked with two cases: looking for translations of an author, or translations from a particular languge (specifying the _source language_). The search query looks like these:

* for authors: `'https://www.unesco.org/xtrans/bsresult.aspx?a=[author]`, where the `[author]` should contain the URL encoded name of the author (e.g. William Shakespeare should be encoded as `Shakespeare,%20William`)
* for source language: `https://www.unesco.org/xtrans/bsresult.aspx?sl=[language code]&tie=a`, where the `[language code]` should be substitute with a concrete language code, such as `hun` for Hungarian 
