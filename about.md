---
title: About
layout: post
---

## The project
The Metadata Quality Assurance Framework is a research project on figuring out how can we decide in an algorithmical way whether a metadata record in a cultural heritage database is "good" or "bad". During the project I will create a general framework, which lets metadata repositories and digital libraries (such as [Europeana](http://europeana.eu), [TextGrid](http://textgrid.de) or [Digital Public Library of America](http://dp.la)) to run a range of measurements on the collection, and get suggestion where they should improve the quality of their metadata.

These pages are about the process of the research -- my early findings, results, codes, talks.

## Important links

The first version of the web interface: [http://144.76.218.178/europeana-qa](http://144.76.218.178/europeana-qa)

### <a name="source-code"></a><a name="source-codes"></a> Source code

* Harvester client: [https://github.com/pkiraly/europeana-oai-pmh-client](https://github.com/pkiraly/europeana-oai-pmh-client)
* General Metadata QA API: 
  - Source repository: [https://github.com/pkiraly/metadata-qa-api](https://github.com/pkiraly/metadata-qa-api)
  - Maven artifact: [http://mvnrepository.com/artifact/de.gwdg.metadataqa/metadata-qa-api](http://mvnrepository.com/artifact/de.gwdg.metadataqa/metadata-qa-api)
* The Europeana-specific Europeana QA API: 
  - Source repository: [https://github.com/pkiraly/europeana-qa-api](https://github.com/pkiraly/europeana-qa-api)
  - Maven artifact: [http://mvnrepository.com/artifact/de.gwdg.metadataqa/europeana-qa-api](http://mvnrepository.com/artifact/de.gwdg.metadataqa/europeana-qa-api)
* Measurement with Spark: [https://github.com/pkiraly/europeana-qa-spark](https://github.com/pkiraly/europeana-qa-spark)
* Analysis with R: [https://github.com/pkiraly/europeana-qa-r](https://github.com/pkiraly/europeana-qa-r)
* Web interface: [https://github.com/pkiraly/europeana-qa-web](https://github.com/pkiraly/europeana-qa-web)
* REST and command line interface: [https://github.com/pkiraly/europeana-qa-client](https://github.com/pkiraly/europeana-qa-client)
* Solr connector: [https://github.com/pkiraly/europeana-qa-solr](https://github.com/pkiraly/europeana-qa-solr)
* Cassandra connector: [https://github.com/pkiraly/europeana-qa-cassandra](https://github.com/pkiraly/europeana-qa-cassandra)
* Measurement with Hadoop: [https://github.com/pkiraly/europeana-qa](https://github.com/pkiraly/europeana-qa)
* MARC measurement
  - Backend [https://github.com/pkiraly/metadata-qa-marc](https://github.com/pkiraly/metadata-qa-marc)
  - Frontend [https://github.com/pkiraly/metadata-qa-marc-web](https://github.com/pkiraly/metadata-qa-marc-web)

<a id="publications"/>
## Publications

2017

Juliane Stiller, and Péter Király. “Multilinguality of Metadata Measuring the Multilingual Degree of Europeana’s Metadata.” In M. Gäde, V. Trkulja, V. Petras (Eds.): *Everything Changes, Everything Stays the Same? Understanding Information Spaces.* Proceedings of the 15th International Symposium of Information Science (ISI 2017), Berlin, 13th—15th March 2017. Glückstadt: Verlag Werner Hülsbusch, pp. 164—176. URL (whole book): [http://isi2017.ib.hu-berlin.de/ISI_17_ONLINE_FINAL.pdf](http://isi2017.ib.hu-berlin.de/ISI_17_ONLINE_FINAL.pdf) (this paper): [https://www.researchgate.net/publication/314879735_Multilinguality_of_Metadata_Measuring_the_Multilingual_Degree_of_Europeana%27s_Metadata](https://www.researchgate.net/publication/314879735_Multilinguality_of_Metadata_Measuring_the_Multilingual_Degree_of_Europeana%27s_Metadata)

Péter Király. “Towards an extensible measurement of metadata quality.” In *Second International Conference on Digital Access to Textual Cultural Heritage.* Conference Proceedings. Göttingen, June 1-2, 2017. Published by ACM 2017. ISBN 978-1-4503-5265-9. pp. 111-115. DOI [10.1145/3078081.3078109](https://doi.org/10.1145/3078081.3078109)
URL: [http://dl.acm.org/citation.cfm?doid=3078081.3078109](http://dl.acm.org/citation.cfm?doid=3078081.3078109)

Péter Király. “Measuring completeness as metadata quality metric in Europeana.” In *Digital Humanities 2017. Conference Abstracts.* McGill University & Université de Montréal, Montréal, Canada, August 8–11, 2017. Prepared by Rhian Lewis and the DH2017 Local Organizers: Cecily Raynor, Dominic Forest, Michael Sinatra and Stéfan Sinclair. pp. 291-293. URL (whole book): [https://dh2017.adho.org/abstracts/DH2017-abstracts.pdf](https://dh2017.adho.org/abstracts/DH2017-abstracts.pdf), URL (the abstract): [https://dh2017.adho.org/abstracts/458/458.pdf](https://dh2017.adho.org/abstracts/458/458.pdf).

2018

Valentine Charles, Juliane Stiller, Péter Király, Werner Bailer, and Nuno Freire. "Data Quality Assessment in Europeana: Metrics for Multilinguality." In *Joint Proceedings of the 1st Workshop on Temporal Dynamics in Digital Libraries (TDDL 2017), the (Meta)-Data Quality Workshop (MDQual 2017) and the Workshop on Modeling Societal Future (Futurity 2017) (TDDL MDQual Futurity 2017) co-located with 21st International Conference on Theory and Practice of Digital Libraries (TPLD 2017)* (Grand Hotel Palace, Thessaloniki, Greece, 21 September 2017), edited by A. Caputo, N. Kanhabua, P. Basile, S. Lawless, D. Gavrilis, Ch. Papatheodorou, D. Trandabat. (CEUR Workshop Proceedings Volume 2038. ISSN 1613-0073.), Published by CEUR, 2018. [http://ceur-ws.org/Vol-2038/paper6.pdf](http://ceur-ws.org/Vol-2038/paper6.pdf).

2019

Péter Király and Marco Büchler. “Measuring completeness as metadata quality metric in Europeana.” In *2018 IEEE International Conference on Big Data (Big Data).* Published by IEEE, 2019. pp. 2711–2720. DOI [10.1109/BigData.2018.8622487](https://doi.org/10.1109/BigData.2018.8622487)

Péter Király, Juliane Stiller, Valentine Charles, Werner Bailer, and Nuno Freire. “Evaluating Data Quality in Europeana: Metrics for Multilinguality.” In *Metadata and Semantic Research 2019. 12th International Conference, MTSR 2018, Limassol, Cyprus, October 23-26, 2018, Revised Selected Papers* (Communications in Computer and Information Science, volume 846) Published by Springer, 2019. pp. 199–211. DOI [10.1007/978-3-030-14401-2_19](https://doi.org/10.1007/978-3-030-14401-2_19)

cited by:
 * Freire, Nuno, and Antoine Isaac. "Technical usability of Wikidata’s linked data." In International Conference on Business Information Systems, pp. 556-567. Springer, Cham, 2019.

Péter Király. “Adat a könyvtárban” (Data in the library -- paper in Hungarian about the changing status of data in LAM). In *Hagyomány és újítás a 21. századi könyvtárban (Erdélyi Évszázadok. A Kolozsvári Magyar Történeti Intézet Évkönyve. III.)* eds. Rüsz-Fogarasi Enikő, Monok István. Kolozsvár (Romania), 2018. ISBN 978-606-8886-1. pp. 49-74. [http://real.mtak.hu/92256/1/ErdEvsz_tordelt_nyomdaba.pdf](http://real.mtak.hu/92256/1/ErdEvsz_tordelt_nyomdaba.pdf)

Péter Király. “Measuring metadata quality”. PhD dissertation. DOI [10.13140/RG.2.2.33177.77920](http://doi.org/10.13140/RG.2.2.33177.77920) (ResearchGate), [Göttingen eDiss repository](http://hdl.handle.net/21.11130/00-1735-0000-0003-C17C-8), [Academia.edu](https://www.academia.edu/40176196/Measuring_Metadata_Quality).

Péter Király. “Validating 126 million MARC records”. In *DATeCH2019 Proceedings of the 3rd International Conference on Digital Access to Textual Cultural Heritage* Brussels, Belgium — May 08-10, 2019. Published by ACM, 2019. ISBN: 978-1-4503-7194-0. pp. 161-168. DOI [10.1145/3322905.3322929](https://doi.org/10.1145/3322905.3322929)

Péter Király and Marco Büchler. “A teljesség minőségjelzőként való mérése az Europeanában”. (Hungarian translation of “Measuring completeness as metadata quality metric in Europeana”) In *Digitális Bölcsészet* 2, 2019. pp. 57-76. DOI [10.31400/dh-hun.2019.2.388](https://doi.org/10.31400/dh-hun.2019.2.388)

2020

Péter Király. "Empirical evaluation of library catalogues". In *EuropeanaTech Newsletter* 15, 2020. [https://pro.europeana.eu/page/issue-15-swib-2019#empirical-evaluation-of-library-catalogues](https://pro.europeana.eu/page/issue-15-swib-2019#empirical-evaluation-of-library-catalogues). In Spanish: “Evaluación empírica de los catálogos de las bibliotecas” (translator unkown - send me a message if you know the translator). Blog de la biblioteca de Traducción y Documentación de la Universidad de Salamanca, 2020. https://universoabierto.org/2020/06/01/evaluacion-empirica-de-los-catalogos-de-las-bibliotecas/

2021

Péter Király, and Jan Brase. "Qualitätsmanagement". In Praxishandbuch Forschungsdatenmanagement. Berlin, Boston: De Gruyter Saur. doi: https://doi.org/10.1515/9783110657807-020, pp. 357–380.

## About me
My name is Péter Király, and I am a software developer, analyst. My main interests are publishing and searching large text corporas in the web, and the new ways of web presence of cultural heritage (mainly library and archival materials with special focus on semantic web technologies). You can reach me via the methods listed in the [contact page](/contact).

## Sponsors

Thanks to [GWDG](http://gwdg.de) for supporting my research in different ways, to [Europeana](https://europeana.eu) and [eTRAP](https://www.etrap.eu/) research group for using their computers, to JetBrains s.r.o. for [IntelliJ IDEA](https://www.jetbrains.com/idea/) community licence, to developers of Open Source software packages, and infrastructure services I used in the research, and to Open Data publishers for their data.
