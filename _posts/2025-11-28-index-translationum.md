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

* for authors: `'https://www.unesco.org/xtrans/bsresult.aspx?a=[author]`, where the `[author]` should contain the URL encoded name of the author in `family name, first name` format (e.g. _William Shakespeare_ should be encoded as `Shakespeare,%20William`)
* for source language: `https://www.unesco.org/xtrans/bsresult.aspx?sl=[language code]&tie=a`, where the `[language code]` should be substitute with a concrete language code, such as `hun` for Hungarian 

You can play at the user interface to find the good initial query term, then you can start with the code (note: the URL encoding is done by the web form, but if you do it programmatically you have to take care with your programming language).

A note on terminology: in translation study the language from which the work has been written is called the _source language_, and the translation is written in the _target language_. Sometime the translator does not work from the source language, but from another tranlation, the language of which is called the _intermediate language_.

The result is a HTML page that you have to parse and extract data. The first thing we extract now is pagination. You receive only 10 result for a single query. The next set can be accessed by clicking on the right arrow icon representing the link to the next page. Fortunately IT applies the `class` attribute of the HTML element to inject some semantics into the page, and we will utilize this feature. Here is how the next link is formatted:

```html
<td class="next">
<a href="bsresult.aspx?lg=0&amp;a=Shakespeare, William&amp;fr=10"><img border="0" src="Images/cy_r_arr.gif" alt="prev"></a>
</td>
```

The `class="next"` part is unique in the page, however on the last page it is empty, since there are no more hits. Thus we should parse it in two step: first get the content of the `<td>` element, then we should find inside the `<a>` element's `href` attribute. Since it contains a relative link, in order to fetch it, we should add _https://www.unesco.org/xtrans/_ to the beginning. We can continue the iteration until the _td_ element becomes empty.

The next thing is to parse the content, the individual bibliographical description. The result are stored in a table structure, where the table has the following structure (for easier understanding I add some line break and spaces):

```html
<table class="restable">
  <tr>
    <td class="res1">1/4380</td>
    <td class="res2">[bibliographical description]</td>
  </tr>
  <tr>
    <td class="res1">2/4380</td>
    <td class="res2">[bibliographical description]</td>
  </tr>
  ...
</table>
```

So we should find the table with `class="restable"`, then inside we should process the bibliographical descriptions, which are always take place in a cell (`<td>` element) with `class="res2"`.

Thanks to the unknown software designers and developers behind IT, all elements of the bibliographical description are in a semantically identifiable `<span>` element. Here is an example (again, formatted a bit):

```html
<td class="res2">
  <span class="sn_auth_name">Shakespeare</span>, <span class="sn_auth_firstname">William</span>:
  <span class="sn_target_title">König Lear: Tragödie</span> 
  [<span class="sn_target_lang">German</span>]
  / <span class="sn_transl_name">Baudissin</span>, <span class="sn_transl_firstname">Wolf Heinrich</span>
  / <span class="sn_pub"><span class="place">Stuttgart</span>: 
  <span class="publisher">Reclam</span>
  [<span class="sn_country">Germany</span>]</span>,
  <span class="sn_year">1979</span>.
  <span class="sn_pagination">112 p.</span>
  <span class="sn_orig_title">King Lear</span> [<span class="sn_orig_lang">English</span>]
</td>
```

IT records comes with the following vocabulary:

* place: publication place
* publisher: publisher
* sn_auth_name: author's family name
* sn_auth_firstname: author's first name
* sn_target_title: the title in the target language
* sn_target_lang: the target language
* sn_country: country of the publication place
* sn_year: publication year
* sn_pagination: pagination
* sn_orig_lang: original (or source) langue
* sn_transl_name: translator's family name
* sn_transl_firstname: translator's first name
* sn_orig_title: title in source languge 
* sn_editionstat: edition statement
* sn_interm_title: title in intermediate language
* sn_interm_lang: intermediate language
* sn_isbn: ISBN
* sn_auth_quality: quality indicator for the author
* sn_transl_quality: quality indicator for the translator

There are number of technical possibilities to parse HTML. Since IT's HTML pages are seemingly transformed from a database with strict rules, one can apply regular expressions, which is a risky approach in lots of other cases. There are more advanced HTML parser libraries however. Since Python is the most popular language among Digital Humanists (and I guess in general as well), I can recommend a Python library BeautifulSoap. Here is the [documentation](https://www.crummy.com/software/BeautifulSoup/bs4/doc/), and Programming Historian also has a tutorial: Jeri Wieringa, "Intro to Beautiful Soup," Programming Historian 1 (2012), https://doi.org/10.46430/phen0008 - which unfortunatelly a retired one, because the HTML page on which the author demonstrate the strength of the tool is no longer available, but still a good introduction, and one can apply the methods on IT.
