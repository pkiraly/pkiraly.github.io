---
title: About
layout: post
---

<style>
ol {
  margin-top: 0 0 0 20px;
}
ol li {
  font-size: 85%;
}
p {
  margin-top: 20px;
  margin-bottom: 0px;
  text-indent: 25px;
}
</style>

## The project

The Metadata Quality Assessment Framework is a research project on figuring out how one can decide in an algorithmic way whether a metadata record in a cultural heritage database is "good" or "bad". During the project a general framework is developed, which enables metadata repositories and digital libraries (such as [Europeana](http://europeana.eu), [TextGrid](http://textgrid.de) or [Digital Public Library of America](http://dp.la)) to run a range of measurements on the collection, and get suggestion where they should improve the quality of their metadata. Multiple extensions are being developed along with the core framework to work with specific metadata schemas, or data source.

These pages are about the process of the research -- my findings, results, codes, talks.

## The author
Péter Király, is a software developer and researcher at at GWDG, the data, compute and research centre for Max-Planck-Society and University of Göttingen. He received PhD (summa cum laude) from University of Göttingen, in 2019 as the output of this research. His main research interests are quality assessment of cultural heritage metadata and cultural analytics, the data analysis of these metadata as historical source. He is also interested in publishing and searching large text corpora in the web, and the new ways of web presence of cultural heritage (archival, library and museum materials with special focus on semantic web technologies). He is an editor of Code4Lib Journal, co-chair of LIBER Data Science in Libraries working group, member of different library and digital humanities related groups, maker and supporter of open source and open data projects. He collaborates with British Library, Belgian National Library, Gemeinsamer Bibliotheksverbund, a German library consortium, Europeana, Deutsche Digitale Bibliothek, meemoo (the Flemish Institute for Archives), Gent University Library, Victoria and Albert museum and other cultural heritage organisations.


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

### 2015

Péter Király. "Metadata quality assurrance framework". Unpublished doctoral research plan (2015) [pkiraly.github.io](http://pkiraly.github.io/metadata-quality-project-plan.pdf)<br/>
cited by:<br/>

1. Vivien Petras, and Juliane Stiller. "A decade of evaluating europeana-constructs, contexts, methods & criteria." In _International Conference on Theory and Practice of Digital Libraries_, pp. 233-245. Springer, Cham, 2017. DOI: [10.1007/978-3-319-67008-9_19](https://doi.org/10.1007/978-3-319-67008-9_19)
2. Marcin Roszkowski. "Diagnostyka metadanych w kolekcjach cyfrowych." _Diagnostyka w zarządzaniu informacją: perspektywa informatologiczna_ (2017): pp. 365-390. [researchgate.net](https://www.researchgate.net/profile/Marcin-Roszkowski/publication/322505864_Diagnostyka_metadanych_w_kolekcjach_cyfrowych/links/5a5cbf810f7e9b4f78395fd9/Diagnostyka-metadanych-w-kolekcjach-cyfrowych.pdf)
3. Oksana L. Zavalina, Shadi Shakeri, Priya Kizhakkethil, and Mark E. Phillips. "Uncovering Hidden Insights for Information Management: Examination and Modeling of Change in Digital Collection Metadata." In _International Conference on Information_, pp. 645-651. Springer, Cham, 2018. DOI: [10.1007/978-3-319-78105-1_74](https://doi.org/10.1007/978-3-319-78105-1_74)
4. Branka Badovinac. "Merjenje kakovosti podatkov v bibliografskih in normativnih zapisih: študija primera izbranih podatkovnih elementov za fasetno omejevanje in izpis seznama zadetkov v COBISS+." _Organizacija Znanja_ 24, no. 1/2 (2019): pp. 1-20. [cobiss.si](https://www.cobiss.si/OZ/PDF/OZ_2019_1_2_final/1924005_Badovinac.pdf)
5. Mark Edward Phillips, Oksana L. Zavalina, and Hannah Tarver. "Exploring the utility of metadata record graphs and network analysis for metadata quality evaluation and augmentation." _International Journal of Metadata, Semantics and Ontologies_ 14, no. 2 (2020): 112-123. DOI: [10.1504/IJMSO.2020.108326](https://doi.org/10.1504/IJMSO.2020.108326)
6. Rachel Jaffe. "Rethinking Metadata’s Value and How It Is Evaluated." _Technical Services Quarterly_ 37, no. 4 (2020): 432-443. DOI: [10.1080/07317131.2020.1810443](https://doi.org/10.1080/07317131.2020.1810443)
7. August Wierling, Valeria Jana Schwanitz, Sebnem Altinci, Maria Bałazinska, Michael J. Barber, Mehmet Efe Biresselioglu, Christopher Burger-Scheidlin, Massimo Celino, Muhittin Hakan Demir, Richard Dennis, Nicolas Dintzner, Adel el Gammal, Carlos M. Fernández-Peruchena, Winston Gilcrease, Paweł Gładysz, Carsten Hoyer-Klick, Kevin Joshi, Mariusz Kruczek, David Lacroix, Małgorzata Markowska, Rafael Mayo-García, Robbie Morrison, Manfred Paier, Giuseppe Peronato, Mahendranath Ramakrishnan, Janeita Reid, Alessandro Sciullo, Berfu Solak, Demet Suna, Wolfgang Süß, Astrid Unger, Maria Luisa Fernandez Vanoni and Nikola Vasiljevic. "FAIR Metadata Standards for Low Carbon Energy Research—A Review of Practices and How to Advance." _Energies_ (2021) 14, no. 20, 6692. DOI: [10.3390/en14206692](https://doi.org/10.3390/en14206692)
8. Matteo Lorenzini, Marco Rospocher, Sara Tonelli. "On assessing metadata completeness in digital cultural heritage repositories." _Digital Scholarship in the Humanities_ 36, Supplement_2, (2021) pp. ii182–ii188. DOI: [10.1093/llc/fqab036](https://doi.org/10.1093/llc/fqab036)
9. Jhon Francined Herrera Cubides. "Metamodelo para vinculación de recursos educativos abiertos mediante especificaciones LOD y basado en principios de confianza." Thesis doctoral. Universidad Distrital “Francisco José de Caldas" Facultad de Ingeniería. Bogotá - Colombia, 2021 [link](https://repository.udistrital.edu.co/handle/11349/28263)
10. Jhon Francined Herrera-Cubides, Paulo Alonso Gaona-García, Carlos Enrique Montenegro-Marin, Salvador Sánchez-Alonso. "The Relevance of Open Data Principles for the Web of Data." _Journal of Electrical and Computer Engineering_ 2023. Article ID 4854965, pp. 1-17. DOI: [10.1155/2023/4854965](https://doi.org/10.1155/2023/4854965)

<!--
The following paper was rejected, and is not available
8. Jhon Francined Herrera-Cubides, Paulo A. Gaona-García and Salvador Sánchez-Alonso. “The Web of Data radiography: Is current Open Data good enough for Linked Data?” (2020). [semantic-web-journal.net](http://www.semantic-web-journal.net/system/files/swj2530.pdf)
-->

### 2017

Juliane Stiller, and Péter Király. “Multilinguality of Metadata Measuring the Multilingual Degree of Europeana’s Metadata.” In M. Gäde, V. Trkulja, V. Petras (Eds.): *Everything Changes, Everything Stays the Same? Understanding Information Spaces.* Proceedings of the 15th International Symposium of Information Science (ISI 2017), Berlin, 13th—15th March 2017. Glückstadt: Verlag Werner Hülsbusch, pp. 164—176. URL (whole book): [http://isi2017.ib.hu-berlin.de/ISI_17_ONLINE_FINAL.pdf](http://isi2017.ib.hu-berlin.de/ISI_17_ONLINE_FINAL.pdf) (this paper): [researchgate.net](https://www.researchgate.net/publication/314879735_Multilinguality_of_Metadata_Measuring_the_Multilingual_Degree_of_Europeana%27s_Metadata)<br/>
cited by:<br/>

1. Sarah Fallert. "Multilinguale Herausforderungen in der Sacherschließung." Master's thesis, Humboldt-Universität zu Berlin, 2020. [edoc.hu-berlin.de](https://edoc.hu-berlin.de/handle/18452/22048)
2. August Wierling, Valeria Jana Schwanitz, Sebnem Altinci, Maria Bałazinska, Michael J. Barber, Mehmet Efe Biresselioglu, Christopher Burger-Scheidlin, Massimo Celino, Muhittin Hakan Demir, Richard Dennis, Nicolas Dintzner, Adel el Gammal, Carlos M. Fernández-Peruchena, Winston Gilcrease, Paweł Gładysz, Carsten Hoyer-Klick, Kevin Joshi, Mariusz Kruczek, David Lacroix, Małgorzata Markowska, Rafael Mayo-García, Robbie Morrison, Manfred Paier, Giuseppe Peronato, Mahendranath Ramakrishnan, Janeita Reid, Alessandro Sciullo, Berfu Solak, Demet Suna, Wolfgang Süß, Astrid Unger, Maria Luisa Fernandez Vanoni  and Nikola Vasiljevic. "FAIR Metadata Standards for Low Carbon Energy Research—A Review of Practices and How to Advance." _Energies_ 2021, 14, 6692. DOI: [10.3390/en14206692](https://doi.org/10.3390/en14206692)


Péter Király. “Towards an extensible measurement of metadata quality.” In *Second International Conference on Digital Access to Textual Cultural Heritage.* Conference Proceedings. Göttingen, June 1-2, 2017. Published by ACM 2017. ISBN 978-1-4503-5265-9. pp. 111-115. DOI: [10.1145/3078081.3078109](https://doi.org/10.1145/3078081.3078109)
URL: [http://dl.acm.org/citation.cfm?doid=3078081.3078109](http://dl.acm.org/citation.cfm?doid=3078081.3078109)<br/>
cited by:<br/>
1. Gustavo Candela, Pilar Escobar, María Dolores Sáez and Manuel Marco-Such. "A Shape Expression approach for assessing the quality of Linked Open Data in Libraries." _Semantic Web_ pp. 1--21. DOI: [10.3233/SW-210441](https://doi.org/10.3233/SW-210441)
2. Widad Elouataoui, Imane El Alaoui, and Youssef Gahi. "Metadata Quality in the Era of Big Data and Unstructured Content." In The International Conference on Information, Communication & Cybersecurity, pp. 110-121. Springer, Cham, 2021. DOI: [10.1007/978-3-030-91738-8_11](https://doi.org/10.1007/978-3-030-91738-8_11)
3. Hannah Tarver, Mark Edward Phillips, and Ana Krahmer. "EPIC: an iterative model for metadata improvement." International Journal of Metadata, Semantics and Ontologies 15, no. 4 (2021): 244-253. DOI: [10.1504/IJMSO.2021.125885](https://doi.org/10.1504/IJMSO.2021.125885)
4. Volodymyr A. Shekhovtsov, Johann Eder, "Metadata Quality for Biobanks". _Applied Sciences_ 2022, 12, 9578. pp. 1--37. DOI: [10.3390/app12199578](https://doi.org/10.3390/app12199578)
5. Gustavo Candela. "Towards a semantic approach in GLAM Labs: the case of the Data Foundry at the National Library of Scotland." arXiv preprint (2023) [arXiv:2301.11182](https://arxiv.org/abs/2301.11182).
6. Bruno Zolotareff dos Santos, Sandra Santos Vales, and Jorge Rady Almeira Junior. "A Metrics-Based Approach to Metadata Classification Applied in a Recommendation System." Preprint. (2023). DOI: [10.21203/rs.3.rs-3132032](https://doi.org/10.21203/rs.3.rs-3132032/v1)


Péter Király. “Measuring completeness as metadata quality metric in Europeana.” In *Digital Humanities 2017. Conference Abstracts.* McGill University & Université de Montréal, Montréal, Canada, August 8–11, 2017. Prepared by Rhian Lewis and the DH2017 Local Organizers: Cecily Raynor, Dominic Forest, Michael Sinatra and Stéfan Sinclair. pp. 291-293. URL (whole book): [https://dh2017.adho.org/abstracts/DH2017-abstracts.pdf](https://dh2017.adho.org/abstracts/DH2017-abstracts.pdf), URL (the abstract): [https://dh2017.adho.org/abstracts/458/458.pdf](https://dh2017.adho.org/abstracts/458/458.pdf).


### 2018

Valentine Charles, Juliane Stiller, Péter Király, Werner Bailer, and Nuno Freire. "Data Quality Assessment in Europeana: Metrics for Multilinguality." In *Joint Proceedings of the 1st Workshop on Temporal Dynamics in Digital Libraries (TDDL 2017), the (Meta)-Data Quality Workshop (MDQual 2017) and the Workshop on Modeling Societal Future (Futurity 2017) (TDDL MDQual Futurity 2017) co-located with 21st International Conference on Theory and Practice of Digital Libraries (TPLD 2017)* (Grand Hotel Palace, Thessaloniki, Greece, 21 September 2017), edited by A. Caputo, N. Kanhabua, P. Basile, S. Lawless, D. Gavrilis, Ch. Papatheodorou, D. Trandabat. (CEUR Workshop Proceedings Volume 2038. ISSN 1613-0073.), Published by CEUR, 2018. [http://ceur-ws.org/Vol-2038/paper6.pdf](http://ceur-ws.org/Vol-2038/paper6.pdf).<br/>
cited by:<br/>
1. Matteo Lorenzini, Rospocher Marco, and Sara Tonelli. "Proposta per una valutazione automatica della completeness dei metadati nel contesto delle biblioteche digitali." _DigItalia_ 2. (2020). pp. 159-167. DOI: [10.36181/digitalia-00023](https://doi.org/10.36181/digitalia-00023)
2. Subhi Issa, Onaopepo Adekunle, Fayçal Hamdi, Samira Si-Said Cherfi, Michel Dumontier, and Amrapali Zaveri. "Knowledge Graph Completeness: A Systematic Literature Review." _IEEE Access_ 9. (2021). pp. 31322-31339. DOI: [10.1109/ACCESS.2021.3056622](https://doi.org/10.1109/ACCESS.2021.3056622)

### 2019

Péter Király and Marco Büchler. “Measuring completeness as metadata quality metric in Europeana.” In *2018 IEEE International Conference on Big Data (Big Data).* Published by IEEE, 2019. pp. 2711–2720. DOI: [10.1109/BigData.2018.8622487](https://doi.org/10.1109/BigData.2018.8622487)<br/>
cited by:<br/>
1. Nadim Akhtar Khan, S. M. Shafi, and Humma Ahangar. "Digitization of cultural heritage: Global initiatives, opportunities and challenges." _Journal of Cases on Information Technology (JCIT)_ 20, no. 4 (2018): 1-16. [igi-global.com](https://www.igi-global.com/article/digitization-of-cultural-heritage/212621)
2. Jongwook Lee. "Analysis and Suggestions of Digital Heritage Policy." _Journal of The Korea Society of Computer and Information_ 24, no. 10 (2019): 71-78. [koreascience.or.kr](https://www.koreascience.or.kr/article/JAKO201931765018680.page)
3. Klara Martha Wanderley Freire. "A curadoria digital nas instituições culturais: possibilidades de reuso de dados de Arte." (2019). [repositorio.ibict.br](https://repositorio.ibict.br/handle/123456789/1050)
4. Jussi Pajari. "Tutkimusaineistojen metatiedot: Metatietojen laatu data-ja metatietoarkistoissa." Master's thesis, 2019. [trepo.tuni.fi](https://trepo.tuni.fi/handle/10024/120079)
5. Mohammadreza Tavakoli, Mirette Elias, Gábor Kismihók, and Sören Auer. "Quality prediction of open educational resources a metadata-based approach." In _2020 IEEE 20th International Conference on Advanced Learning Technologies (ICALT)_, pp. 29-31. IEEE, 2020. DOI: [10.1109/ICALT49669.2020.00007](https://doi.org/10.1109/ICALT49669.2020.00007)
6. Kristen Schuster, and Stuart Dunn, eds. _Routledge International Handbook of Research Methods in Digital Humanities_. Routledge, 2020. [books.google.com](https://books.google.com/books?hl=en&lr=&id=VmLyDwAAQBAJ&oi=fnd&pg=PT7&ots=3VJbMtiXVc&sig=KwdribufDLXFuw33mYcCOXbkK-Y)
7. Mohammadreza Tavakoli, Ali Faraji, Stefan T. Mol, and Gábor Kismihók. "OER Recommendations to Support Career Development." In _2020 IEEE Frontiers in Education Conference (FIE)_, pp. 1-5. IEEE, 2020. DOI: [10.1109/FIE44824.2020.9274175](https://doi.org/10.1109/FIE44824.2020.9274175)
8. A. J. Million "Information Communication Technologies, Infrastructure, and Research Methods in the Digital Humanities." In _Routledge International Handbook of Research Methods in Digital Humanities_, pp. 190-202. Routledge, 2020. DOI: [10.4324/9780429777028-15](https://doi.org/10.4324/9780429777028-15)
9. Mark Edward Phillips, Oksana L. Zavalina, and Hannah Tarver. "Exploring the utility of metadata record graphs and network analysis for metadata quality evaluation and augmentation." _International Journal of Metadata, Semantics and Ontologies_ 14, no. 2 (2020): 112-123. DOI: [10.1504/IJMSO.2020.108326](https://doi.org/10.1504/IJMSO.2020.108326)
10. Yalemisew Abgaz, Amelie Dorn, José Luis Preza Díaz, and Gerda Koch. "Towards a Comprehensive Assessment of the Quality and Richness of the Europeana Metadata of food-related Images." In _Proceedings of the 1st International Workshop on Artificial Intelligence for Historical Image Enrichment and Access_, pp. 29-33. 2020. [aclweb.org](https://www.aclweb.org/anthology/2020.ai4hi-1.5/)
11. Johann Eder and Vladimir A. Shekhovtsov. "Data Quality for Medical Data Lakelands." In _International Conference on Future Data and Security Engineering_, pp. 28-43. Springer, Cham, 2020. DOI: [10.1007/978-3-030-63924-2_2](https://doi.org/10.1007/978-3-030-63924-2_2)
12. Matteo Lorenzini, Marco Rospocher, and Sara Tonelli. "Proposta per una valutazione automatica della completeness dei metadati nel contesto delle biblioteche digitali." _DigItalia_ 2. (2020). pp. 159-167. DOI: [10.36181/digitalia-00023](https://doi.org/10.36181/digitalia-00023)
13. Johann Eder and Vladimir A. Shekhovtsov. "Data quality for federated medical data lakes." _International Journal of Web Information Systems_ (2021). DOI: [10.1108/IJWIS-03-2021-0026](https://doi.org/10.1108/IJWIS-03-2021-0026)
14. Mark Edward Phillips and Hannah Tarver. "Investigating the use of metadata record graphs to analyze subject headings in the digital public library of America." _The Electronic Library_ (2021). DOI: [10.1108/EL-11-2020-0317](https://doi.org/10.1108/EL-11-2020-0317)
15. Susan A. Barrett "Participatory Description and Metadata Quality in Rapid Response Archives." _Collections_ (2021): 1550190620981038. DOI: [10.1177/1550190620981038](https://doi.org/10.1177/1550190620981038)
16. Matteo Lorenzini, Marco Rospocher, and Sara Tonelli. "Automatically evaluating the quality of textual descriptions in cultural heritage records." _International Journal on Digital Libraries_ 22, no. 2 (2021): 217-231. DOI: [10.1007/s00799-021-00302-1](https://doi.org/10.1007/s00799-021-00302-1)
17. Lisa Wenige, Claus Stadler, Michael Martin, Richard Figura, Robert Sauter, and Christopher W. Frank. "Open Data and the Status Quo--A Fine-Grained Evaluation Framework for Open Data Quality and an Analysis of Open Data portals in Germany." _arXiv preprint_ arXiv:2106.09590 (2021). [arxiv.org](https://arxiv.org/abs/2106.09590)
18. Mohammadreza Tavakoli, Mirette Elias, Gábor Kismihók, and Sören Auer. "Metadata Analysis of Open Educational Resources." In _LAK21: 11th International Learning Analytics and Knowledge Conference_, pp. 626-631. 2021. DOI: [10.1145/3448139.3448208](https://doi.org/10.1145/3448139.3448208)
19. Lisandra Díaz de la Paz, Francisco N. Riestra Collado, Juan L. García Mendoza, Luisa M. González González, Amed A. Leiva Mederos, and Alberto Taboada Crispi. "Weights Estimation in the Completeness Measurement of Bibliographic Metadata." Computación y Sistemas 25, no. 1. 2021. pp. 47–65. DOI: [10.13053/CyS-25-1-3355](https://doi.org/10.13053/CyS-25-1-3355)
20. Петр Сергеевич Ершов, and Юрий Евгеньевич Хохлов. "Цифровая инфраструктура для работы с большими данными." _Информационное общество_ 4-5 (2021): 110-131. [infosoc.iis.ru](http://infosoc.iis.ru/article/view/657)
21. Vladimir A. Shekhovtsov and Johann Eder. "Data Item Quality for Biobanks." In _Transactions on Large-Scale Data-and Knowledge-Centered Systems_ L, Springer, Berlin, Heidelberg, 2021. pp. 77-115. DOI: [10.1007/978-3-662-64553-6_5](https://doi.org/10.1007/978-3-662-64553-6_5)
22. Widad Elouataoui, Imane El Alaoui, and Youssef Gahi. "Metadata Quality in the Era of Big Data and Unstructured Content." In The International Conference on Information, Communication & Cybersecurity, pp. 110-121. Springer, Cham, 2021. DOI: [10.1007/978-3-030-91738-8_11](https://doi.org/10.1007/978-3-030-91738-8_11)
23. Mohammadreza Tavakoli, Abdolali Faraji, Jarno Vrolijk, Mohammadreza Molavi, Stefan T. Mol, Gábor Kismihók. "An AI-based open recommender system for personalized labor market driven education." Advanced Engineering Informatics, Volume 52, 2022, 101508. DOI: [10.1016/j.aei.2021.101508](https://doi.org/10.1016/j.aei.2021.101508)    
24. Kaylin Blount. "Knowing What We Have: Proposing a Sustainable Workflow for the Assessment of Digitized Archival Collections at Wilson Library." Master thesis in Information Science. University of North Caroline, School of Information and Library Science, 2022. [unc.edu](https://cdr.lib.unc.edu/concern/masters_papers/x059cj11d)
25. Barbara Šlibar, and Enrique Mu. "OGD metadata country portal publishing guidelines compliance: A multi-case study search for completeness and consistency". *Government Information Quarterly* 2022, August. 101756. DOI: [10.1016/j.giq.2022.101756](https://doi.org/10.1016/j.giq.2022.101756)
26. Volodymyr A. Shekhovtsov, Johann Eder. "Metadata Quality for Biobanks". _Applied Sciences_ 2022, 12, 9578. pp. 1--37. DOI: [10.3390/app12199578](https://doi.org/10.3390/app12199578)
27. Hannah Tarver, Meredith Hale, Rachel White, Steven Gentry, Madison Chartier, Rachel Wittmann. "Metadata Quality in Digital Libraries: An Analysis of Survey Response Data". In Proceedings of the 18th International Conference on Digital Preservation 2022. Glasgow, Scotland. [10.7207/ipres2022-proceedings](https://doi.org/10.7207/ipres2022-proceedings). pp. 162-172.
28. Juan Ribeiro Reis, Flavia Bernadini, Jose Viterbo. "A New Approach for Assessing Metadata Completeness in Open Data Portals". _International Journal of Electronic Government Research_ (IJEGR) 18, 2022, no.1: 1-20. [10.4018/IJEGR.313636](http://doi.org/10.4018/IJEGR.313636)
29. Johann Eder, Volodymyr A. Shekhovtsov. "Managing the Quality of Data and Metadata for Biobanks". In T. K. Dang et al. (Eds.) _Future Data and Security Engineering. Big Data, Security and Privacy, Smart City and Industry 4.0 Applications 2022_ (FDSE 2022), CCIS 1688. pp. 52–69. DOI: [10.1007/978-981-19-8069-5_4](https://doi.org/10.1007/978-981-19-8069-5_4)
30. Mirette Magdy Michel Elias. "Adapting OpenCourseWare Based on the Needs and Preferences of Disabled Learners". PhD Dissertation, University of Bonn. 2022. [uni-bonn.de](https://bonndoc.ulb.uni-bonn.de/xmlui/handle/20.500.11811/10539)

Péter Király, Juliane Stiller, Valentine Charles, Werner Bailer, and Nuno Freire. “Evaluating Data Quality in Europeana: Metrics for Multilinguality.” In *Metadata and Semantic Research 2019. 12th International Conference, MTSR 2018, Limassol, Cyprus, October 23-26, 2018, Revised Selected Papers* (Communications in Computer and Information Science, volume 846) Published by Springer, 2019. pp. 199–211. DOI: [10.1007/978-3-030-14401-2_19](https://doi.org/10.1007/978-3-030-14401-2_19)<br/>
cited by:<br/>
1. Nuno Freire and Antoine Isaac. "Technical usability of Wikidata’s linked data." In International Conference on Business Information Systems, pp. 556-567. Springer, Cham, 2019. DOI: [10.1007/978-3-030-36691-9_47](https://doi.org/10.1007/978-3-030-36691-9_47)
2. Mark E. Phillips, Oksana L. Zavalina, and Hannah Tarver. "Using metadata record graphs to understand digital library metadata." In International Conference on Dublin Core and Metadata Applications, pp. 49-58. 2020. [dcpapers.dublincore.org](https://dcpapers.dublincore.org/pubs/article/view/4237)
3. Nuno Freire, and Antoine Isaac. "Wikidata's linked data for cultural heritage digital resources: an evaluation based on the Europeana data model." In International Conference on Dublin Core and Metadata Applications, pp. 59-68. 2020. [dcpapers.dublincore.org](https://dcpapers.dublincore.org/pubs/article/view/4239)
4. Sarantos Kapidakis. "Consistency and Interoperability on Dublin Core Element Values in Collections Harvested using the Open Archive Initiative Protocol for Metadata Harvesting." In _Proceedings of the 12th International Joint Conference on Knowledge Discovery, Knowledge Engineering and Knowledge Management (IC3K 2020)_ Volume 2: KEOD, pp. 181-188. 2020. DOI: [10.5220/0010112001810188](https://doi.org/10.5220/0010112001810188)
5. Yalemisew Abgaz, Amelie Dorn, José Luis Preza Díaz, and Gerda Koch. "Towards a Comprehensive Assessment of the Quality and Richness of the Europeana Metadata of food-related Images." In Proceedings of the 1st International Workshop on Artificial Intelligence for Historical Image Enrichment and Access, pp. 29-33. 2020. [aclanthology.org](https://aclanthology.org/2020.ai4hi-1.5/)
6. Н. С. Редькина "ЕВРОПЕАНА: ЦИФРОВОЕ КУЛЬТУРНОЕ НАСЛЕДИЕ ЕВРОПЫ." Ученые записки (Алтайская государственная академия культуры и искусств) 2 (24) (2020). [cyberleninka.ru](https://cyberleninka.ru/article/n/evropeana-tsifrovoe-kulturnoe-nasledie-evropy/pdf)
7. Inkyung Choi, Wan-Chen Lee, Ying-Hsang Liu, Hsinliang Chen, Douglas W. Oard, and Chi Young Oh. "Cross-cultural information access." 85th Annual Meeting of the Association for Information Science & Technology, 2022. Proceedings of the Association for Information Science and Technology, 2022 59:1 pp. 551-554. [10.1002/pra2.624](https://doi.org/10.1002/pra2.624). Preprint: [umd.edu](https://terpconnect.umd.edu/~oard/pdf/asist22panel.pdf).
8. Julia Neumann. "Semantic interoperability in metrology through controlled vocabulary." In IMEKO TC6 International Conference on Metrology and Digital Transformation. September 19 − September 21, 2022, Berlin, Germany. 2022 [m4dconf2022.ptb.de](https://www.m4dconf2022.ptb.de/fileadmin/documents/m4dconf2022/Material/Paper/IMEKOTC6-M4Dconf-2022-P46-NEUMANN.pdf)
9. Manuel Alejandro Flores Chávez. "MetaMetrics: prototipo de visualización de la calidad de los metadatos en revistas científicas latinoamericanas publicadas en Open Journal System." _Biblioteca Universitaria_ 26, no. 1 (2023). DOI: [10.22201/dgbsdi.0187750xp.2023.1.1466](https://doi.org/10.22201/dgbsdi.0187750xp.2023.1.1466)

Péter Király. “Adat a könyvtárban” (Data in the library -- paper in Hungarian about the changing status of data in LAM). In *Hagyomány és újítás a 21. századi könyvtárban (Erdélyi Évszázadok. A Kolozsvári Magyar Történeti Intézet Évkönyve. III.)* eds. Rüsz-Fogarasi Enikő, Monok István. Kolozsvár (Romania), 2018. ISBN 978-606-8886-1. pp. 49-74. [http://real.mtak.hu/92256/1/ErdEvsz_tordelt_nyomdaba.pdf](http://real.mtak.hu/92256/1/ErdEvsz_tordelt_nyomdaba.pdf)<br/>
cited by:<br/>
1. Virágos Márta. "Open Science a könyvtárban: könyvtáros kompetenciák újraértelmezése." _Tudományos és Műszaki Tájékoztatás_ 67, no. 12 (2020): 739-756. [tmt.omikk.bme.hu](https://tmt.omikk.bme.hu/tmt/article/view/12803)

Péter Király. “Measuring metadata quality”. PhD dissertation, University of Göttingen. DOI: [10.13140/RG.2.2.33177.77920](http://doi.org/10.13140/RG.2.2.33177.77920) (ResearchGate), [Göttingen eDiss repository](http://hdl.handle.net/21.11130/00-1735-0000-0003-C17C-8), [Academia.edu](https://www.academia.edu/40176196/Measuring_Metadata_Quality).<br/>
cited by:<br/>
1. Tyler J. Skluzacek, Ryan Wong, Zhuozhao Li, Ryan Chard, Kyle Chard, and Ian Foster. "A Serverless Framework for Distributed Bulk Metadata Extraction." In _Proceedings of the 30th International Symposium on High-Performance Parallel and Distributed Computing_, pp. 7-18. 2020. DOI: [10.1145/3431379.3460636](https://doi.org/10.1145/3431379.3460636)
2. Widad Elouataoui, Imane El Alaoui, and Youssef Gahi. "Metadata Quality in the Era of Big Data and Unstructured Content." In The International Conference on Information, Communication & Cybersecurity, pp. 110-121. Springer, Cham, 2021. DOI: [10.1007/978-3-030-91738-8_11](https://doi.org/10.1007/978-3-030-91738-8_11)
3. Salman Haider. "Library Cataloging, Classification, and Metadata Research: A Bibliography of Doctoral Dissertations—A Supplement, 2021". _Cataloging & Classification Quarterly_, 2022. no. 1. pp. 1-6. DOI: [10.1080/01639374.2021.2025183](https://doi.org/10.1080/01639374.2021.2025183)
4. Tyler J. Skluzacek, Matthew Chen, Erica Hsu, Kyle Chard, and Ian Foster. "Models and Metrics for Mining Meaningful Metadata." _International Conference on Computational Science_ (ICCS), 2022. [ResearchGate.net](https://www.researchgate.net/publication/359971955_Models_and_Metrics_for_Mining_Meaningful_Metadata).
5. Nhu, Nam Dan. "Nachschlagedienst für qualitative hochwertige Metadaten von Veröffentlichungen." Bachelor's thesis, Hannover: Gottfried Wilhelm Leibniz Universität Hannover, Institut für Verteilte Systeme, 2022. [handle:123456789/12472](https://www.repo.uni-hannover.de/handle/123456789/12472)
6. Tyler J. Skluzacek. "Automated Metadata Extraction Can Make Data Swamps More Navigable." Ph.D. dissertation. The University of Chicago, Computer Science (2022). DOI: [10.6082/uchicago.4760](https://doi.org/10.6082/uchicago.4760)
7. Volodymyr A. Shekhovtsov, and Johann Eder. "Metadata Quality for Biobanks". _Applied Sciences_ 2022, 12, 9578. pp. 1--37. DOI: [10.3390/app12199578](https://doi.org/10.3390/app12199578)
8. Agnieszka Karlińska, Cezary Rosiński, Jan Wieczorek, Patryk Hubar, Jan Kocoń, Marek Kubis, Stanisław Woźniak, Arkadiusz Margraf, and Wiktor Walentynowicz. "Towards a contextualised spatial-diachronic history of literature: mapping emotional representations of the city and the country in Polish fiction from 1864 to 1939." In Proceedings of the 6th Joint SIGHUM Workshop on Computational Linguistics for Cultural Heritage, Social Sciences, Humanities and Literature, Gyeongju, Republic of Korea. International Conference on Computational Linguistics. 2022. pp. 115–125 [aclanthology.org](https://aclanthology.org/2022.latechclfl-1.14)
9. Murari Tapaswi. "Some issues in the Shodhganga–A theses repository from India." _Annals of Library and Information Studies_ 70, no. 2 (2023): 74-84. DOI [10.56042/alis.v70i2.1834](https://doi.org/10.56042/alis.v70i2.1834)

Péter Király. “Validating 126 million MARC records”. In *DATeCH2019 Proceedings of the 3rd International Conference on Digital Access to Textual Cultural Heritage* Brussels, Belgium — May 08-10, 2019. Published by ACM, 2019. ISBN: 978-1-4503-7194-0. pp. 161-168. DOI: [10.1145/3322905.3322929](https://doi.org/10.1145/3322905.3322929)<br/>
cited by:<br/>
1. Ungváry, Rudolf. "MARC21 tartalmi adatmezők használata jelentősebb nagykönyvtárakban. Egy elemzés néhány tanulsága." Networkshop (2020): 33-53. [real.mtak.hu](http://real.mtak.hu/119192/1/ungvary.pdf)
2. Ungváry, Rudolf. "Ismeretszervező-könyvtári rendszerek tartalmi feltárásának összehasonlító vizsgálata MARC21 környezetben." Tudományos és Műszaki Tájékoztatás, 2020. (67. évf.) 11. sz. pp. 655-680. [tmt.omikk.bme.hu](https://tmt.omikk.bme.hu/tmt/article/view/12776/14514)
3. Evan Bryer, Theppatorn Rhujittawiwat, John R. Rose, and Colin F. Wilder. "Spelling Based Ranked Clustering Algorithm To Clean And Normalize Early Modern European Book Titles." [ihci-conf.org](https://www.ihci-conf.org/wp-content/uploads/2021/07/01_202107L013_Bryer.pdf)
4. Evan Bryer, Theppatorn Rhujittawiwat, Samyu Comandur, Vasco Madrid, Stephanie Riley, John Rose, and Colin Wilder. "Analysis of Clustering Algorithms to Clean and Normalize Early Modern European Book Titles." In 2021 The 4th International Conference on Software Engineering and Information Management, pp. 106-112. 2021. DOI: [10.1145/3451471.3451489](https://doi.org/10.1145/3451471.3451489)
5. Gustavo Candela, Pilar Escobar, María Dolores Sáez and Manuel Marco-Such. "A Shape Expression approach for assessing the quality of Linked Open Data in Libraries." _Semantic Web_ pp. 1--21. DOI: [10.3233/SW-210441](https://doi.org/10.3233/SW-210441)
6. Jakob Voß. "Datenqualität als Grundlage qualitativer Inhaltserschließung." In _Qualität in der Inhaltserschließung._ Edited by: Michael Franke-Maier, Anna Kasprzik, Andreas Ledl and Hans Schürmann. Berlin, Boston: De Gruyter Saur. ISBN: 9783110691597, DOI: 10.1515/9783110691597 (Bibliotheks- und Informationspraxis, Volume 70) pp. 167-176. DOI: [10.1515/9783110691597-011](https://doi.org/10.1515/9783110691597-010)
7. Vyacheslav Zavalin, Oksana L. Zavalina and Rachel Safa. "Patterns of Subject Metadata Change in MARC 21 Bibliographic Records for Video Recordings." _Proceedings of the Association for Information Science and Technology_ 58, no. 1 (2021): 543-547. DOI: [10.1002/pra2.494](https://doi.org/10.1002/pra2.494)
8. Evan Bryer, Theppatorn Rhujittawiwat, John R. Rose, and Colin F. Wilder. "Improvement of Clustering Algorithms by Implementation of Spelling Based Ranking." _IADIS International Journal on Computer Science and Information Systems_ 2021. Vol. 16, No. 2, pp. 45-60. ISSN: 1646-3692. [iadisportal.org](http://www.iadisportal.org/ijcsis/papers/2021160204.pdf)
9. Tomasz Umerle and Vojtěch Malínek. "Literarybibliography.eu — modelový příklad pro tvorbu mezinárodní oborové bibliografie." _Ceska Literatura_  70(2022):5. pp. 579--595. DOI: [10.51305/cl.2022.05.03](https://doi.org/10.51305/cl.2022.05.03)
10. Gustavo Candela, Nele Gabriëls, Sally Chambers, Thuy-An Pham, Sarah Ames, Neil Fitzgerald, Katrine Hofmann, Victor Harbo, Abigail Potter, Meghan Ferriter, Eileen Manchester, Alba Irollo, Ellen Van Keer, Mahendra Mahey, Olga Holownia, Milena Dobreva. "A Checklist to Publish Collections as Data in GLAM Institutions." arXiv preprint (2023) arXiv: [2304.02603](https://arxiv.org/abs/2304.02603)

Péter Király and Marco Büchler. “A teljesség minőségjelzőként való mérése az Europeanában”. (Hungarian translation of “Measuring completeness as metadata quality metric in Europeana”) In *Digitális Bölcsészet* 2, 2019. pp. 57-76. DOI: [10.31400/dh-hun.2019.2.388](https://doi.org/10.31400/dh-hun.2019.2.388)

### 2020

Péter Király. "Empirical evaluation of library catalogues". In *EuropeanaTech Newsletter* 15, 2020. [https://pro.europeana.eu/page/issue-15-swib-2019#empirical-evaluation-of-library-catalogues](https://pro.europeana.eu/page/issue-15-swib-2019#empirical-evaluation-of-library-catalogues). In Spanish: “Evaluación empírica de los catálogos de las bibliotecas” (translator unkown - send me a message if you know the translator). Blog de la biblioteca de Traducción y Documentación de la Universidad de Salamanca, 2020. [https://universoabierto.org/2020/06/01/evaluacion-empirica-de-los-catalogos-de-las-bibliotecas/](https://universoabierto.org/2020/06/01/evaluacion-empirica-de-los-catalogos-de-las-bibliotecas/)

Péter Király. "A magyar népzenei adatok története és a (digitális) archiválás lehetőségei. Bolya Mátyás. Információelmélet és népzenekutatás: Rendszeralkotás, nyilvántartás, digitális archívum. Budapest: MTA BTK Zenetudományi Intézet–L’Harmattan Kiadó, 2019." Book review. In _Digitális Bölcsészet_ 3, 2020. pp. 7-15. DOI: [10.31400/dh-hun.2020.3.1405](https://doi.org/10.31400/dh-hun.2020.3.1405)

### 2021

Péter Király, and Jan Brase. "Qualitätsmanagement". In _Praxishandbuch Forschungsdatenmanagement_. Edited by: Markus Putnings, Heike Neuroth and Janna Neumann. Berlin, Boston: De Gruyter Saur. ISBN: 9783110653656, DOI: 10.1515/9783110657807 (De Gruyter Praxishandbuch) pp. 357–380. DOI: [10.1515/9783110657807-020](https://doi.org/10.1515/9783110657807-020)<br/>
cited by:<br/>
1. Dietmar Kammerer and Kai Matuszkiewicz. "Forschungsdaten in der Medienwissenschaft: Infrastrukturen, Plattformen und Forschungsdatenmanagement und ihre Bedeutung für die digitale Transformation der Medienwissenschaft". In: Stollfuß, S., Niebling, L., Raczkowski, F. (eds) Handbuch Digitale Medien und Methoden. Springer VS, Wiesbaden, 2023. pp. 1-19. DOI: [10.1007/978-3-658-36629-2_6-1](https://doi.org/10.1007/978-3-658-36629-2_6-1)
2. Maxi Kindling. "Qualitätssicherung von Datenpublikationen bei Data Journals und Forschungsdatenrepositorien". Doctoral Thesis. Philosophischen Fakultät der Humboldt-Universität zu Berlin. 2022. DOI: [10.18452/26023](https://doi.org/10.18452/26023)
3. Dr. Yves Vincent Grossmann (ed.) "Data Quality". In: Max Planck Digital Library. _Research Data Management. Information Platform for Max Planck Researchers_ [mpdl.mpg.de](https://rdm.mpdl.mpg.de/before-research/data-quality/)


Rudolf Ungváry, and Péter Király. "Bemerkungen zu der Qualitätsbewertung von MARC-21-Datensätzen". In _Qualität in der Inhaltserschließung._ Edited by: Michael Franke-Maier, Anna Kasprzik, Andreas Ledl and Hans Schürmann. Berlin, Boston: De Gruyter Saur. ISBN: 9783110691597, DOI: 10.1515/9783110691597 (Bibliotheks- und Informationspraxis, Volume 70) pp. 177-227. DOI: [10.1515/9783110691597-011](https://doi.org/10.1515/9783110691597-011)

Király Péter. "Kulturális adatelemzés – bevezetés és önéletrajz. Lev Manovich. Cultural analytics. Cambridge, Massachussetts–London, England: The MIT Press, 2020." Book Review. In _Digitális Bölcsészet_ 4, 2021. pp. 11-22. DOI: [10.31400/dh-hun.2021.4.3510](https://doi.org/10.31400/dh-hun.2021.4.3510)

### 2022

Tomasz Umerle, Giovanni Colavizza, Elżbieta Herden, Rindert Jagersma, Péter Király, Beata Koper, Leo Lahti, David Lindemann, Jakub Maciej Łubocki, Vojtěch Malínek, Alexandra Milanova, Róbert Péter, Nanette Rißler-Pipka, Matteo Romanello, Marcin Roszkowski, Dorota Siwecka, Mikko Tolonen, Ondřej Vimr. "An Analysis of The Current Bibliographical Data Landscape in the Humanities. A Case for the Joint Bibliodata Agendas of Public Stakeholders". 46 p. DARIAH. DOI: [10.5281/zenodo.6559857](https://doi.org/10.5281/zenodo.6559857)

Péter Király, and Hannes Lowagie. "Implementation of a daily MARC assessment with open source tools at KBR, the royal library of Belgium.". *IFLA Metadata Newsletter* Volume 8, Number 1, June 2022. pp. 12-15 [ifla.org](https://repository.ifla.org/bitstream/123456789/1976/1/IFLA_Metadata_Newsletter_June_2022.pdf)<br/>
cited by:<br/>
1. Ann Van Camp and Sven Lieber. "ISNI, a top tool for quality enhancement, smooth data flows and efficient internal processes". In: 87th IFLA World Library and Information Congress (WLIC) / 2022. pp. 1-10. [ifla.org](http://repository.ifla.org/handle/123456789/2008)

Rudolf Ungváry, and Péter Király. "A MARC21 tételfejének és kódolt tartalmi jellemzőinek feldolgozási minősége néhány nemzeti könyvtárban". *Tudományos és Műszaki Tájékoztatás* 2022. pp. 155-175. DOI: [10.3311/tmt.13174](http://doi.org/10.3311/tmt.13174)

Triet Ho Anh Doan, Péter Király, Sven Bingert. "MINE – Workspace as a Service for Text Analysis." In: Gianmaria Silvello, Oscar Corcho, Paolo Manghi, Giorgio Maria Di Nunzio, Koraljka Golub, Nicola Ferro, Antonella Poggi (Eds.) Linking Theory and Practice of Digital Libraries. 26th International Conference on Theory and Practice
of Digital Libraries, TPDL 2022 Padua, Italy, September 20–23, 2022, Proceedings. Lecture Notes in Computer Science, vol 13541. Springer, Cham. pp 328–334. DOI: [10.1007/978-3-031-16802-4_29](https://doi.org/10.1007/978-3-031-16802-4_29)

### 2023

Ungváry Rudolf, Király Péter. "Nemzeti könyvtárak és az OSZK MARC21 állományainak összehasonlító elemzése néhány adatmező alapján: Tanulságok." *Tudományos és Műszaki Tájékoztatás*, 2023. pp. 1-28. DOI: [10.3311/tmt.13250](https://doi.org/10.3311/tmt.13250)

Király Péter. "Adatelemzés Pythonnal bölcsészeknek. Recenzió Folgert Karsdorp, Mike Kestemont, and Allen Riddel. Humanities Data Analysis: Case studies with Python című könyvéről" _Digitális Bölcsészet_, 2022. 6. K:3-K:9. DOI: [10.31400/dh-hun.2022.6.5580](https://doi.org/10.31400/dh-hun.2022.6.5580).

Erzsébet Tóth-Czifra, Marta Błaszczyńska, Francesco Gelati, Femmy Admiraal, Mirjam Blümm, Erik Buelinckx, Vera Chiquet, Rita Gautschy, Peter Gietz, Péter Király, Maria Vivas-Romero, Walter Scholger, Bartłomiej Szleszyński, & Ulrike Wuttke. "Research Data Management for Arts and Humanities: Integrating Voices of the Community."" Zenodo, 2023. 97 p. DOI: [10.5281/zenodo.8059626](https://doi.org/10.5281/zenodo.8059626)

<!-- span id="badgeCont105"><script type="text/javascript" src="https://publons.com/mashlets?el=badgeCont105&rid=AAW-9289-2021"></script></span -->


## Sponsors

Thanks to 
* [GWDG](http://gwdg.de) for supporting my research in different ways, 
* to [Europeana](https://europeana.eu) and [eTRAP](https://www.etrap.eu/) research group for using their computers, 
* to JetBrains s.r.o. for [IntelliJ IDEA](https://www.jetbrains.com/idea/) community licence, 
* to [British Library](https://www.bl.uk/), [KBR, the Belgian National Library](https://kbr.be) and [Gemeinsamer Bibliotheksverbund](https://www.gbv.de/) for supporting the developments of [QA catalogue](https://github.com/pkiraly/metadata-qa-marc) and for [Deutsche Digitale Bibliothek](https://www.deutsche-digitale-bibliothek.de/) for supporting the developments of [Metadata Quality Assessment Framework](https://github.com/pkiraly/metadata-qa-api), 
* to developers of Open Source software packages, and infrastructure services I used in the research, and
* to Open Data publishers for their data.

You can reach me via the methods listed in the [contact page](/contact).
