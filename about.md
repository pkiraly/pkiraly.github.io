---
title: About
layout: post
---

<style>
ul {
  margin-top: 0 0 0 20px;
  list-style: none;
  padding-left: 25px;
}
li {
  font-size: 90%;
  text-indent: 25px;
}
p {
  margin-top: 20px;
  margin-bottom: 0px;
  text-indent: 25px;
}
</style>

## The project

The Metadata Quality Assurance Framework is a research project on figuring out how can we decide in an algorithmical way whether a metadata record in a cultural heritage database is "good" or "bad". During the project I will create a general framework, which lets metadata repositories and digital libraries (such as [Europeana](http://europeana.eu), [TextGrid](http://textgrid.de) or [Digital Public Library of America](http://dp.la)) to run a range of measurements on the collection, and get suggestion where they should improve the quality of their metadata.

These pages are about the process of the research -- my early findings, results, codes, talks.

## Important links

The first version of the web interface: [http://144.76.218.178/europeana-qa](http://144.76.218.178/europeana-qa)

### <a name="source-codes"></a> Source code

* Metadata Quality Assessment Framework API: 
  - Source repository: [https://github.com/pkiraly/metadata-qa-api](https://github.com/pkiraly/metadata-qa-api)
  - Maven artifact: [http://mvnrepository.com/artifact/de.gwdg.metadataqa/metadata-qa-api](http://mvnrepository.com/artifact/de.gwdg.metadataqa/metadata-qa-api)
* MARC measurement
  - Backend [https://github.com/pkiraly/metadata-qa-marc](https://github.com/pkiraly/metadata-qa-marc)
  - Frontend [https://github.com/pkiraly/metadata-qa-marc-web](https://github.com/pkiraly/metadata-qa-marc-web)
* The Europeana-specific Europeana QA API: 
  - Source repository: [https://github.com/pkiraly/europeana-qa-api](https://github.com/pkiraly/europeana-qa-api)
  - Maven artifact: [http://mvnrepository.com/artifact/de.gwdg.metadataqa/europeana-qa-api](http://mvnrepository.com/artifact/de.gwdg.metadataqa/europeana-qa-api)
* Harvester client: [https://github.com/pkiraly/europeana-oai-pmh-client](https://github.com/pkiraly/europeana-oai-pmh-client)
* Measurement with Spark: [https://github.com/pkiraly/europeana-qa-spark](https://github.com/pkiraly/europeana-qa-spark)
* Analysis with R: [https://github.com/pkiraly/europeana-qa-r](https://github.com/pkiraly/europeana-qa-r)
* Web interface: [https://github.com/pkiraly/europeana-qa-web](https://github.com/pkiraly/europeana-qa-web)
* REST and command line interface: [https://github.com/pkiraly/europeana-qa-client](https://github.com/pkiraly/europeana-qa-client)
* Solr connector: [https://github.com/pkiraly/europeana-qa-solr](https://github.com/pkiraly/europeana-qa-solr)
* Cassandra connector: [https://github.com/pkiraly/europeana-qa-cassandra](https://github.com/pkiraly/europeana-qa-cassandra)
* Measurement with Hadoop: [https://github.com/pkiraly/europeana-qa](https://github.com/pkiraly/europeana-qa)


## <a name="publications"/>Publications

### 2017

Juliane Stiller, and Péter Király. “Multilinguality of Metadata Measuring the Multilingual Degree of Europeana’s Metadata.” In M. Gäde, V. Trkulja, V. Petras (Eds.): *Everything Changes, Everything Stays the Same? Understanding Information Spaces.* Proceedings of the 15th International Symposium of Information Science (ISI 2017), Berlin, 13th—15th March 2017. Glückstadt: Verlag Werner Hülsbusch, pp. 164—176. URL (whole book): [http://isi2017.ib.hu-berlin.de/ISI_17_ONLINE_FINAL.pdf](http://isi2017.ib.hu-berlin.de/ISI_17_ONLINE_FINAL.pdf) (this paper): [https://www.researchgate.net/publication/314879735_Multilinguality_of_Metadata_Measuring_the_Multilingual_Degree_of_Europeana%27s_Metadata](https://www.researchgate.net/publication/314879735_Multilinguality_of_Metadata_Measuring_the_Multilingual_Degree_of_Europeana%27s_Metadata)<br/>
cited by:<br/>

 * Fallert, Sarah. "Multilinguale Herausforderungen in der Sacherschließung." Master's thesis, Humboldt-Universität zu Berlin, 2020. [link](https://edoc.hu-berlin.de/handle/18452/22048)
 * August Wierling, Valeria Jana Schwanitz, Sebnem Altinci, Maria Bałazinska, Michael J. Barber, Mehmet Efe Biresselioglu, Christopher Burger-Scheidlin, Massimo Celino, Muhittin Hakan Demir, Richard Dennis, Nicolas Dintzner, Adel el Gammal, Carlos M. Fernández-Peruchena, Winston Gilcrease, Paweł Gładysz, Carsten Hoyer-Klick, Kevin Joshi, Mariusz Kruczek, David Lacroix, Małgorzata Markowska, Rafael Mayo-García, Robbie Morrison, Manfred Paier, Giuseppe Peronato, Mahendranath Ramakrishnan, Janeita Reid, Alessandro Sciullo, Berfu Solak, Demet Suna, Wolfgang Süß, Astrid Unger, Maria Luisa Fernandez Vanoni  and Nikola Vasiljevic. "FAIR Metadata Standards for Low Carbon Energy Research—A Review of Practices and How to Advance." _Energies_ 2021, 14, 6692. DOI [10.3390/en14206692](https://doi.org/10.3390/en14206692)


Péter Király. “Towards an extensible measurement of metadata quality.” In *Second International Conference on Digital Access to Textual Cultural Heritage.* Conference Proceedings. Göttingen, June 1-2, 2017. Published by ACM 2017. ISBN 978-1-4503-5265-9. pp. 111-115. DOI [10.1145/3078081.3078109](https://doi.org/10.1145/3078081.3078109)
URL: [http://dl.acm.org/citation.cfm?doid=3078081.3078109](http://dl.acm.org/citation.cfm?doid=3078081.3078109)<br/>
cited by:<br/>
 * Gustavo Candela, Pilar Escobar, María Dolores Sáez and Manuel Marco-Such. "A Shape Expression approach for assessing the quality of Linked Open Data in Libraries." _Semantic Web_ pp. 1--21. DOI [10.3233/SW-210441](https://doi.org/10.3233/SW-210441)

Péter Király. “Measuring completeness as metadata quality metric in Europeana.” In *Digital Humanities 2017. Conference Abstracts.* McGill University & Université de Montréal, Montréal, Canada, August 8–11, 2017. Prepared by Rhian Lewis and the DH2017 Local Organizers: Cecily Raynor, Dominic Forest, Michael Sinatra and Stéfan Sinclair. pp. 291-293. URL (whole book): [https://dh2017.adho.org/abstracts/DH2017-abstracts.pdf](https://dh2017.adho.org/abstracts/DH2017-abstracts.pdf), URL (the abstract): [https://dh2017.adho.org/abstracts/458/458.pdf](https://dh2017.adho.org/abstracts/458/458.pdf).

### 2018

Valentine Charles, Juliane Stiller, Péter Király, Werner Bailer, and Nuno Freire. "Data Quality Assessment in Europeana: Metrics for Multilinguality." In *Joint Proceedings of the 1st Workshop on Temporal Dynamics in Digital Libraries (TDDL 2017), the (Meta)-Data Quality Workshop (MDQual 2017) and the Workshop on Modeling Societal Future (Futurity 2017) (TDDL MDQual Futurity 2017) co-located with 21st International Conference on Theory and Practice of Digital Libraries (TPLD 2017)* (Grand Hotel Palace, Thessaloniki, Greece, 21 September 2017), edited by A. Caputo, N. Kanhabua, P. Basile, S. Lawless, D. Gavrilis, Ch. Papatheodorou, D. Trandabat. (CEUR Workshop Proceedings Volume 2038. ISSN 1613-0073.), Published by CEUR, 2018. [http://ceur-ws.org/Vol-2038/paper6.pdf](http://ceur-ws.org/Vol-2038/paper6.pdf).<br/>
cited by:<br/>
 * Matteo Lorenzini, Rospocher Marco, and Sara Tonelli. "Proposta per una valutazione automatica della completeness dei metadati nel contesto delle biblioteche digitali." _DigItalia_ 2. (2020). pp. 159-167. DOI [10.36181/digitalia-00023](https://doi.org/10.36181/digitalia-00023)

### 2019

Péter Király and Marco Büchler. “Measuring completeness as metadata quality metric in Europeana.” In *2018 IEEE International Conference on Big Data (Big Data).* Published by IEEE, 2019. pp. 2711–2720. DOI [10.1109/BigData.2018.8622487](https://doi.org/10.1109/BigData.2018.8622487)<br/>
cited by:<br/>
 * Nadim Akhtar Khan, S. M. Shafi, and Humma Ahangar. "Digitization of cultural heritage: Global initiatives, opportunities and challenges." _Journal of Cases on Information Technology (JCIT)_ 20, no. 4 (2018): 1-16. [link](https://www.igi-global.com/article/digitization-of-cultural-heritage/212621)
 * Jongwook Lee. "Analysis and Suggestions of Digital Heritage Policy." _Journal of The Korea Society of Computer and Information_ 24, no. 10 (2019): 71-78. [link](https://www.koreascience.or.kr/article/JAKO201931765018680.page)
 * Klara Martha Wanderley Freire. "A curadoria digital nas instituições culturais: possibilidades de reuso de dados de Arte." (2019). [link](https://repositorio.ibict.br/handle/123456789/1050)
 * Jussi Pajari. "Tutkimusaineistojen metatiedot: Metatietojen laatu data-ja metatietoarkistoissa." Master's thesis, 2019. [link](https://trepo.tuni.fi/handle/10024/120079)
 * Mohammadreza Tavakoli, Mirette Elias, Gábor Kismihók, and Sören Auer. "Quality prediction of open educational resources a metadata-based approach." In _2020 IEEE 20th International Conference on Advanced Learning Technologies (ICALT)_, pp. 29-31. IEEE, 2020. [link](https://ieeexplore.ieee.org/abstract/document/9155928/)
 * Kristen Schuster, and Stuart Dunn, eds. _Routledge International Handbook of Research Methods in Digital Humanities_. Routledge, 2020. [link](https://books.google.com/books?hl=en&lr=&id=VmLyDwAAQBAJ&oi=fnd&pg=PT7&ots=3VJbMtiXVc&sig=KwdribufDLXFuw33mYcCOXbkK-Y)
 * Mohammadreza Tavakoli, Ali Faraji, Stefan T. Mol, and Gábor Kismihók. "OER Recommendations to Support Career Development." In _2020 IEEE Frontiers in Education Conference (FIE)_, pp. 1-5. IEEE, 2020. [link](https://ieeexplore.ieee.org/abstract/document/9274175/)
 * A. J. Million "Information Communication Technologies, Infrastructure, and Research Methods in the Digital Humanities." In _Routledge International Handbook of Research Methods in Digital Humanities_, pp. 190-202. Routledge, 2020. [link](https://www.taylorfrancis.com/chapters/edit/10.4324/9780429777028-15/information-communication-technologies-infrastructure-research-methods-digital-humanities-million)
 * Mark Edward Phillips, Oksana L. Zavalina, and Hannah Tarver. "Exploring the utility of metadata record graphs and network analysis for metadata quality evaluation and augmentation." _International Journal of Metadata, Semantics and Ontologies_ 14, no. 2 (2020): 112-123. [link](https://www.inderscienceonline.com/doi/abs/10.1504/IJMSO.2020.108326)
 * Yalemisew Abgaz, Amelie Dorn, José Luis Preza Díaz, and Gerda Koch. "Towards a Comprehensive Assessment of the Quality and Richness of the Europeana Metadata of food-related Images." In _Proceedings of the 1st International Workshop on Artificial Intelligence for Historical Image Enrichment and Access_, pp. 29-33. 2020. [link](https://www.aclweb.org/anthology/2020.ai4hi-1.5/)
 * Johann Eder and Vladimir A. Shekhovtsov. "Data Quality for Medical Data Lakelands." In _International Conference on Future Data and Security Engineering_, pp. 28-43. Springer, Cham, 2020. [link](https://link.springer.com/chapter/10.1007/978-3-030-63924-2_2)
 * Matteo Lorenzini, Marco Rospocher, and Sara Tonelli. "Proposta per una valutazione automatica della completeness dei metadati nel contesto delle biblioteche digitali." _DigItalia_ 2. (2020). pp. 159-167. DOI [10.36181/digitalia-00023](https://doi.org/10.36181/digitalia-00023)
 * Johann Eder and Vladimir A. Shekhovtsov. "Data quality for federated medical data lakes." _International Journal of Web Information Systems_ (2021). [link](https://www.emerald.com/insight/content/doi/10.1108/IJWIS-03-2021-0026/full/html)
 * Mark Edward Phillips and Hannah Tarver. "Investigating the use of metadata record graphs to analyze subject headings in the digital public library of America." _The Electronic Library_ (2021). [link](https://www.emerald.com/insight/content/doi/10.1108/EL-11-2020-0317/full/html)
 * Susan A. Barrett "Participatory Description and Metadata Quality in Rapid Response Archives." _Collections_ (2021): 1550190620981038. [link](https://journals.sagepub.com/doi/abs/10.1177/1550190620981038)
 * Matteo Lorenzini, Marco Rospocher, and Sara Tonelli. "Automatically evaluating the quality of textual descriptions in cultural heritage records." _International Journal on Digital Libraries_ 22, no. 2 (2021): 217-231. [link](https://link.springer.com/article/10.1007/s00799-021-00302-1)
 * Lisa Wenige, Claus Stadler, Michael Martin, Richard Figura, Robert Sauter, and Christopher W. Frank. "Open Data and the Status Quo--A Fine-Grained Evaluation Framework for Open Data Quality and an Analysis of Open Data portals in Germany." _arXiv preprint_ arXiv:2106.09590 (2021). [link](https://arxiv.org/abs/2106.09590)
 * Mohammadreza Tavakoli, Mirette Elias, Gábor Kismihók, and Sören Auer. "Metadata Analysis of Open Educational Resources." In _LAK21: 11th International Learning Analytics and Knowledge Conference_, pp. 626-631. 2021. [link](https://dl.acm.org/doi/abs/10.1145/3448139.3448208)
 * Lisandra Díaz de la Paz, Francisco N. Riestra Collado, Juan L. García Mendoza, Luisa M. González González, Amed A. Leiva Mederos, and Alberto Taboada Crispi. "Weights Estimation in the Completeness Measurement of Bibliographic Metadata." Computación y Sistemas 25, no. 1. 2021. pp. 47–65. DOI [10.13053/CyS-25-1-3355](https://doi.org/10.13053/CyS-25-1-3355)

Péter Király, Juliane Stiller, Valentine Charles, Werner Bailer, and Nuno Freire. “Evaluating Data Quality in Europeana: Metrics for Multilinguality.” In *Metadata and Semantic Research 2019. 12th International Conference, MTSR 2018, Limassol, Cyprus, October 23-26, 2018, Revised Selected Papers* (Communications in Computer and Information Science, volume 846) Published by Springer, 2019. pp. 199–211. DOI [10.1007/978-3-030-14401-2_19](https://doi.org/10.1007/978-3-030-14401-2_19)<br/>
cited by:<br/>
 * Nuno Freire and Antoine Isaac. "Technical usability of Wikidata’s linked data." In International Conference on Business Information Systems, pp. 556-567. Springer, Cham, 2019. DOI [10.1007/978-3-030-36691-9_47](https://doi.org/10.1007/978-3-030-36691-9_47)
 * Mark E. Phillips, Oksana L. Zavalina, and Hannah Tarver. "Using metadata record graphs to understand digital library metadata." In International Conference on Dublin Core and Metadata Applications, pp. 49-58. 2020. [link](https://dcpapers.dublincore.org/pubs/article/view/4237)
 * Nuno Freire, and Antoine Isaac. "Wikidata's linked data for cultural heritage digital resources: an evaluation based on the Europeana data model." In International Conference on Dublin Core and Metadata Applications, pp. 59-68. 2020. [link](https://dcpapers.dublincore.org/pubs/article/view/4239)
 * Sarantos Kapidakis. "Consistency and Interoperability on Dublin Core Element Values in Collections Harvested using the Open Archive Initiative Protocol for Metadata Harvesting." In KEOD, pp. 181-188. 2020. [link](https://www.scitepress.org/Papers/2020/101120/101120.pdf)
 * Yalemisew Abgaz, Amelie Dorn, José Luis Preza Díaz, and Gerda Koch. "Towards a Comprehensive Assessment of the Quality and Richness of the Europeana Metadata of food-related Images." In Proceedings of the 1st International Workshop on Artificial Intelligence for Historical Image Enrichment and Access, pp. 29-33. 2020. [link](https://aclanthology.org/2020.ai4hi-1.5/)
 * Н. С. Редькина "ЕВРОПЕАНА: ЦИФРОВОЕ КУЛЬТУРНОЕ НАСЛЕДИЕ ЕВРОПЫ." Ученые записки (Алтайская государственная академия культуры и искусств) 2 (24) (2020). [link](https://cyberleninka.ru/article/n/evropeana-tsifrovoe-kulturnoe-nasledie-evropy/pdf)

Péter Király. “Adat a könyvtárban” (Data in the library -- paper in Hungarian about the changing status of data in LAM). In *Hagyomány és újítás a 21. századi könyvtárban (Erdélyi Évszázadok. A Kolozsvári Magyar Történeti Intézet Évkönyve. III.)* eds. Rüsz-Fogarasi Enikő, Monok István. Kolozsvár (Romania), 2018. ISBN 978-606-8886-1. pp. 49-74. [http://real.mtak.hu/92256/1/ErdEvsz_tordelt_nyomdaba.pdf](http://real.mtak.hu/92256/1/ErdEvsz_tordelt_nyomdaba.pdf)<br/>
cited by:<br/>
* Virágos Márta. "Open Science a könyvtárban: könyvtáros kompetenciák újraértelmezése." _Tudományos és Műszaki Tájékoztatás_ 67, no. 12 (2020): 739-756. [link](https://tmt.omikk.bme.hu/tmt/article/view/12803)

Péter Király. “Measuring metadata quality”. PhD dissertation. DOI [10.13140/RG.2.2.33177.77920](http://doi.org/10.13140/RG.2.2.33177.77920) (ResearchGate), [Göttingen eDiss repository](http://hdl.handle.net/21.11130/00-1735-0000-0003-C17C-8), [Academia.edu](https://www.academia.edu/40176196/Measuring_Metadata_Quality).<br/>
cited by:<br/>
* Tyler J. Skluzacek, Ryan Wong, Zhuozhao Li, Ryan Chard, Kyle Chard, and Ian Foster. "A Serverless Framework for Distributed Bulk Metadata Extraction." In _Proceedings of the 30th International Symposium on High-Performance Parallel and Distributed Computing_, pp. 7-18. 2020. [link](https://www.researchgate.net/profile/Tyler-J-Skluzacek/publication/352065654_A_Serverless_Framework_for_Distributed_Bulk_Metadata_Extraction/links/60b8276592851c209d5e4f6b/A-Serverless-Framework-for-Distributed-Bulk-Metadata-Extraction.pdf)

Péter Király. “Validating 126 million MARC records”. In *DATeCH2019 Proceedings of the 3rd International Conference on Digital Access to Textual Cultural Heritage* Brussels, Belgium — May 08-10, 2019. Published by ACM, 2019. ISBN: 978-1-4503-7194-0. pp. 161-168. DOI [10.1145/3322905.3322929](https://doi.org/10.1145/3322905.3322929)<br/>
cited by:<br/>
 * Ungváry, Rudolf. "MARC21 tartalmi adatmezők használata jelentősebb nagykönyvtárakban. Egy elemzés néhány tanulsága." Networkshop (2020): 33-53. [link](http://real.mtak.hu/119192/1/ungvary.pdf)
 * Ungváry, Rudolf. "Ismeretszervező-könyvtári rendszerek tartalmi feltárásának összehasonlító vizsgálata MARC21 környezetben." Tudományos és Műszaki Tájékoztatás, 2020. (67. évf.) 11. sz. pp. 655-680. [https://tmt.omikk.bme.hu/tmt/article/view/12776/14514](https://tmt.omikk.bme.hu/tmt/article/view/12776/14514)
 * Evan Bryer, Theppatorn Rhujittawiwat, John R. Rose, and Colin F. Wilder. "Spelling Based Ranked Clustering Algorithm To Clean And Normalize Early Modern European Book Titles." [link](https://www.ihci-conf.org/wp-content/uploads/2021/07/01_202107L013_Bryer.pdf)
 * Evan Bryer, Theppatorn Rhujittawiwat, Samyu Comandur, Vasco Madrid, Stephanie Riley, John Rose, and Colin Wilder. "Analysis of Clustering Algorithms to Clean and Normalize Early Modern European Book Titles." In 2021 The 4th International Conference on Software Engineering and Information Management, pp. 106-112. 2021. DOI [10.1145/3451471.3451489](https://doi.org/10.1145/3451471.3451489)
 * Gustavo Candela, Escobar, Pilar, Sáez, María Dolores and Marco-Such, Manuel. "A Shape Expression approach for assessing the quality of Linked Open Data in Libraries." _Semantic Web_ pp. 1--21. DOI [10.3233/SW-210441](https://doi.org/10.3233/SW-210441)
 * Jakob Voß. "Datenqualität als Grundlage qualitativer Inhaltserschließung." In _Qualität in der Inhaltserschließung._ Edited by: Michael Franke-Maier, Anna Kasprzik, Andreas Ledl and Hans Schürmann. Berlin, Boston: De Gruyter Saur. ISBN: 9783110691597, DOI 10.1515/9783110691597 (Bibliotheks- und Informationspraxis, Volume 70) pp. 167-176. DOI [10.1515/9783110691597-011](https://doi.org/10.1515/9783110691597-010)

Péter Király and Marco Büchler. “A teljesség minőségjelzőként való mérése az Europeanában”. (Hungarian translation of “Measuring completeness as metadata quality metric in Europeana”) In *Digitális Bölcsészet* 2, 2019. pp. 57-76. DOI [10.31400/dh-hun.2019.2.388](https://doi.org/10.31400/dh-hun.2019.2.388)

### 2020

Péter Király. "Empirical evaluation of library catalogues". In *EuropeanaTech Newsletter* 15, 2020. [https://pro.europeana.eu/page/issue-15-swib-2019#empirical-evaluation-of-library-catalogues](https://pro.europeana.eu/page/issue-15-swib-2019#empirical-evaluation-of-library-catalogues). In Spanish: “Evaluación empírica de los catálogos de las bibliotecas” (translator unkown - send me a message if you know the translator). Blog de la biblioteca de Traducción y Documentación de la Universidad de Salamanca, 2020. [https://universoabierto.org/2020/06/01/evaluacion-empirica-de-los-catalogos-de-las-bibliotecas/](https://universoabierto.org/2020/06/01/evaluacion-empirica-de-los-catalogos-de-las-bibliotecas/)

Péter Király. "A magyar népzenei adatok története és a (digitális) archiválás lehetőségei. Bolya Mátyás. Információelmélet és népzenekutatás: Rendszeralkotás, nyilvántartás, digitális archívum. Budapest: MTA BTK Zenetudományi Intézet–L’Harmattan Kiadó, 2019." Book review. In *Digitális Bölcsészet* 3, 2020. pp. 7-15. DOI [10.31400/dh-hun.2020.3.1405](https://doi.org/10.31400/dh-hun.2020.3.1405)

### 2021

Péter Király, and Jan Brase. "Qualitätsmanagement". In _Praxishandbuch Forschungsdatenmanagement_. Edited by: Markus Putnings, Heike Neuroth and Janna Neumann. Berlin, Boston: De Gruyter Saur. ISBN: 9783110653656, DOI 10.1515/9783110657807 (De Gruyter Praxishandbuch) pp. 357–380. DOI: [10.1515/9783110657807-020](https://doi.org/10.1515/9783110657807-020)

Rudolf Ungváry, and Péter Király. "Bemerkungen zu der Qualitätsbewertung von MARC-21-Datensätzen". In _Qualität in der Inhaltserschließung._ Edited by: Michael Franke-Maier, Anna Kasprzik, Andreas Ledl and Hans Schürmann. Berlin, Boston: De Gruyter Saur. ISBN: 9783110691597, DOI 10.1515/9783110691597 (Bibliotheks- und Informationspraxis, Volume 70) pp. 177-227. DOI [10.1515/9783110691597-011](https://doi.org/10.1515/9783110691597-011)

<!-- span id="badgeCont105"><script type="text/javascript" src="https://publons.com/mashlets?el=badgeCont105&rid=AAW-9289-2021"></script></span -->

## About me
My name is Péter Király, and I am a software developer, analyst. My main interests are publishing and searching large text corporas in the web, and the new ways of web presence of cultural heritage (mainly library and archival materials with special focus on semantic web technologies). You can reach me via the methods listed in the [contact page](/contact).

## Sponsors

Thanks to [GWDG](http://gwdg.de) for supporting my research in different ways, to [Europeana](https://europeana.eu) and [eTRAP](https://www.etrap.eu/) research group for using their computers, to JetBrains s.r.o. for [IntelliJ IDEA](https://www.jetbrains.com/idea/) community licence, to developers of Open Source software packages, and infrastructure services I used in the research, and to Open Data publishers for their data.
