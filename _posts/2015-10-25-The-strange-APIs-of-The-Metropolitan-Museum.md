---
title:      The strange APIs of The Metropolitan Museum, New York
layout:     post
date:       2015-10-25 11:02:00
author:     "pkiraly"
---

<img src="https://lh3.googleusercontent.com/-YADBvaC2hUQ/AAAAAAAAAAI/AAAAAAAAAEg/_fr6798_2Uo/photo.jpg" align="center" alt="Logo of the Metropolitan Museum of Art" width="250" height="250" style="width: 250px; height: 250px; text-align: center; margin-left: 30%; margin-right: 30%"/>

Last Friday I heard a presentation of [Fernando Pérez](http://fperez.org/ "Fernando Pérez"), who is — among 
many other things — one of the founders of Berkeley Institute for Data Science (shortly BIDS). 
After his presentation I spent some time on the 
[BIDS website](http://bids.berkeley.edu/ "BIDS website"), investigating their projects. One of those is the 
[ROpenSci](https://ropensci.org/ "ROpenSci"), which is a community for „transforming science through open data”. 
They create R packages in several scientific domains.

<!-- more -->

I checked "musemeta", an [R Client for Scraping Museum Metadata](https://github.com/ropensci/musemeta "R Client 
for Scraping Museum Metadata") created by [Scott Chamberlain](http://scottchamberlain.info/ "Scott Chamberlain"). 
By the way, you can find all of their R packages in [GitHub](https://github.com/ropensci).

The `musemeta` package lets users to integrate metadata from different museums (The Metropolitan Museum of Art, 
The Canadian Science & Technology Museum Corporation, The National Gallery of Art, The Getty Museum, The Art 
Institute of Chicago, and The Asian Art Museum of San Francisco). For accessing MET data the package provides two 
alternative methods. The first one (called `mets()`) is based the good old web scrapping approach: the function 
gets the HTML source of a page wich contains the data of the museum object, and tries to extract all the 
valuable information — the metadata of the object. This method is a bit of fragile: if on the target side 
the institution introduces a technological change, the HTML layout will be changed by high chance, and 
you should modify your extracting code accordingly otherwise the result will be crap. The author of `musemeta` 
is aware of this problem, and he provides an alternative method: using an API dedicated to MET data. It is 
called ''scrapi'' (or scrAPI) a metropolitan museum collections api, and available at
[scrapi.org](http://scrapi.org/ "scrapi.org").

This API is also an Open Source software and its code is also available on 
[GitHub](https://github.com/jedahan/collections-api). I was curious how this API could connect to MET's database, 
and what kind of database MET uses, because if I were the API developer of MET I would choose a different API 
endpoint URL, which belong to my institution, so I suspected that there should be a second, low level API the 
scrapi makes use. I checked the source, and for my suprise it turned out, that scrapi also uses the same 
HTML extraction approach as the musedata's met() method, and for even bigger suprise it turned out, that MET 
supposedly blocks the user agent the scrapi originally made use in its HTTP request header when fetched the 
HTML from MET - so [Jonathan Dahan](http://jedahan.com "Jonathan Dahan"), the developer changed it to a 
somewhat undetectable random string. I though it is the end of the story, but not. 
I was curious why you have to create an API on 
your own at the first place if you want to access MET's metadata programmatically. It turned out, that there 
is a [Met Media Lab](http://www.metmuseum.org/about-the-museum/museum-departments/office-of-the-director/digital-media-department/medialab) 
entity within the museum, and they also have a [GitHub repository](https://github.com/metmuseum-medialab). 
And guess what: they forked the API which is blocked by the museum's web server.
