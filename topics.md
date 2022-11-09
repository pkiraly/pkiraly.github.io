---
title: GWDG Cultural Analytics Team research topics
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

div#toc p {margin: 0; line-height:1.0;}
div#toc p.c14 {padding-top:4pt;  padding-bottom:0pt; }
div#toc p.c15 {padding-top:10pt; padding-bottom:0pt; }
div#toc p.c8  {margin-left:18pt; padding-top:3pt; padding-bottom:0pt;}
div#toc p.c22 {margin-left:18pt; padding-top:3pt; padding-bottom:4pt;}

</style>

<span class="blue">GWDG Cultural Analytics Team</span> research topics

Péter Király
last updated: 2022-11-04

<ul>
  <li><a href="#h.dbhfcpj8muh">I. Metadata Quality Assessment</a>
    <ul>
      <li><a href="#h.f7u6fsdxft67">I.1 SHACL4MARC&ndash;Validating MARC records against locally defined ruleset</a></li>
      <li><a href="#h.t5dz9y5v47ws">I.2 UNIMARC</a></li>
      <li><a href="#h.d18pz1c4a259">I.3 PICA and PICA+</a></li>
      <li><a href="#h.fbhlo0fq8hyu">I.4 Encoded Archival Description (EAD) and Encoded Archival Context (EAC)</a></li>
      <li><a href="#h.kbbv9oz8aewp">I.5 International Standard Bibliographic Description (ISBD)</a></li>
      <li><a href="#h.4nxautqtaory">I.6 Anglo-American Cataloguing Rules (AACR2)</a></li>
      <li><a href="#h.qokm407em93v">I.7 MAQUIS&ndash;The quality of the terms in the metadata records and of the Knowledge Organising Systems</a></li>
      <li><a href="#h.p8xbhn17yv0m">I.8 Citation data</a></li>
      <li><a href="#h.jqbwpwbff8w0">I.9 MARC authority records</a></li>
      <li><a href="#h.1u2r1ewy6o6s">I.10 Agile Qualit&auml;tssicherung von Metadaten zu kulturellen Objekten im Kontext von Datenintegrationsprozessen</a></li>
    </ul>
  </li>
  <li><a href="#h.onhgw5ps1do1">II. Cultural analytics / Bibliographic data science</a>
    <ul>
      <li><a href="#h.fjpp9yjyg95z">II.1 Kinder- und Jugendbücher international. Eine Metadatenanalyse</a></li>
      <li><a href="#h.55thhjh5aks2">II.2 Patterns of translations of national literatures</a></li>
      <li><a href="#h.qkgqr5bgpxh2">II.3 Patterns of publications</a></li>
    </ul>
  </li>
</ul>

Cultural Analytics Team is a research team inside the eScience Working Group (AG E) of Gesellschaft für wissenschaftliche Datenverarbeitung mbH Göttingen ([GWDG](https://www.gwdg.de/)), the computation centre and IT research institute of the [University of Göttingen](https://uni-goettingen.de/) and [Max Planck Society](https://www.mpg.de/en). The purpose of the team is to find ways to apply data analytics solutions in cultural heritage domains in collaboration with other players in Göttingen, Germany and abroad. The team is in a formation state.

This list declares the active and intended research topics of the team. There are two main branches: cultural heritage metadata quality assessment and cultural analytics with special focus on bibliographic data science. Each branch contains a number of individual, independent research, however altogether they form an interrelated network. Each research topic has two sides: an applied computer science one and a humanities one. The first are usually about software development questions and tasks, such as creating algorithms for interpreting data written in a metadata schema, or optimising the running of the software by time or memory consumption. The second side has content related questions, and requires humanistic research methods. Metadata quality assessment might be more appealing for students of Library and Information Science, of book studies (Buchwissenschaft, bibliology), of archival studies, while the cultural analytics topics might be interesting for a wider branch of Digital Humanities students. The research in both topics should be resulted in some written output (paper or thesis), the quality assessment topics optionally outputs software code as well.

We are constantly looking for student helpers, research assistants and collaborating partners in these researches so if the reader feels that a topic is interesting for her/him, do not hesitate to contact us via peter.kiraly@gwdg.de.

<h1 id="h.dbhfcpj8muh"><span class="blue">I.</span> Metadata Quality Assessment</h1>

<p>All of these topics are connected to <em>Metadata Quality Assessment Framework API</em> (MQAF API) <a href="#ftnt4" id="ftnt_ref4">[4]</a> and <em>QA catalogue</em> <a href="#ftnt5" id="ftnt_ref5">[5]</a> open source research software. The topics are extensions of previous research and these software packages. Our final purpose is to provide quality assessment solutions to the metadata records created with all the standard schemas used in cultural heritage institutions (libraries, archives and museums).</p>
<p>Metadata is a type of record, which describes the important features of an object stored in such organisation (such as a book, a letter of an 18th century scholar or a sculpture. Here the “data” is the original object, and since metadata literally means “data about data” includes the creator, title, identifier, location, material, size and other important features of the object. Metadata schema is a special document which describes the structure and rules of the records in a metadata collection, so it tells how to encode this information. Sometimes the schema has a machine readable version (serialised as an XML or JSON schema), sometimes it doesn’t have. Usually the schema does not contain all the information quality assessment requires, so we have to extend it with other information, for example which data elements or rules are more important than others in a particular context, what extra requirements are applicable in a particular organisation (e.g. an identifier might be a simple string or number, and in some context it is claimed to better if it forms a URL, and even better if the URL is persistent).</p>
<p>The MQAF API is a general metadata assessment tool, which requires a derivative of the metadata schema with specific properties for the quality assessment task. Based on this one can build a tool to analyse records in a particular schema simply by configuration. We already have some implementation for this kind of development for Deutsche Digitale Bibliothek, for Victoria and Albert Museum, and meemoo, the Flemish Institute for Archives.</p>
<p>QA catalogue (an extension of MQAF API) is specified for library catalogues and works with records in a metadata schema called MARC (MAchine Readable Cataloging), <a href="#ftnt6" id="ftnt_ref6">[6]</a> and already used by the British Library, KBR, the Royal Library of Belgium, and Gent University Library. Its future extensions should cover MARC variants and non-MARC bibliographic metadata schema such as PICA (and variants), and UNIMARC.</p>
<p>It is equally important for all metadata assessment tools, that they provide input for metadata experts, who decide which reported problems are really relevant for their institute and in which priority.</p>

<p>Abbreviations: </p>
<ul>
  <li>CS &ndash; Computer Science</li>
  <li>LIS &ndash; Library and Information Science</li>
  <li>DH &ndash; Digital Humanities</li>
  <li>BL &ndash; British Library</li>
  <li>KBR &ndash; Royal Library of Belgium</li>
</ul>


<h2 class="c18" id="h.f7u6fsdxft67"><span class="blue">I.1</span> SHACL4MARC&ndash;Validating MARC records against locally defined ruleset</h2>
<p><em>Introduction</em>. Shapes Constraint Language (SHACL) <a href="#ftnt7" id="ftnt_ref7">[7]</a> is a formal language for validating RDF <a href="#ftnt8" id="ftnt_ref8">[8]</a> graphs against a set of conditions (expressed also in RDF). Following this idea, and implementing a subset of the language, <em>MQAF API</em> provides a mechanism to define SHACL-like rules for data sources in non-RDF based formats, such as XML, CSV and JSON (SHACL validates only RDF graphs). The rules can be defined either with YAML or JSON configuration files or with Java code. <a href="#ftnt9" id="ftnt_ref9">[9]</a> <em>MQAF API</em> has already been validated in different organisations (Flemish Audio-Visual Archives, Victoria and Albert Museum, Deutsche Digitale Bibliothek). In this research we extend this ruleset to be applicable to MARC records. For making it available for MARC records there are two criteria:</p>

<ul>
  <li>supporting a particular &quot;addressing scheme&quot; which fits MARC records. This scheme is similar to XPATH or JSONPath which are mechanisms to precisely select a part of an XML and JSON document. For MARC there is a proposal, Carsten Klee&#39;s MARCspec - a common MARC record path language,</span> <a href="#ftnt10" id="ftnt_ref10">[10]</a> which is already supported by the QA catalogue.</li>
  <li>implementing a particular interface of MQAF API, which could return a unified value object when we specify it with an address of a data element.</li>
</ul>

<p>In this research we have two control data sets. BL provided a sample with examples where particular problems have been catched by an alternative tool, but not by QA catalogue. KBR developed an XSLT based solution to check local rulesets. We can use both to compare those results with ours.</p>
<p>During the research students will learn about the following technologies: MARC, SHACL, XPath, JSONPath, MARCspec.</p>

<p>Research questions and tasks (Computer Science):</p>
<ul>
  <li>Finish the implementation of MARCspec in QA catalogue</li>
  <li>Create a selector class which could find and retrieve the part of the record which is addressed by the MARCspec expression (other implementation of the interface are already available for Xpath, JSONPath and SQL column name expressions)</li>
  <li>Adapt MQAF API that it should accept this selector implementation as input parameter (right now the implementations are hard coded)</li>
  <li>Create a command line interface in QA catalogue which accepts a configuration file describing SHACL-like ruleset</li>
</ul>

<p>Research questions (Humanities):</p>
<ul>
  <li>Can the content specific cataloguing rules provided by BL and KBR be transformed to SHACL-like machine readable rules? Are there limitations, and if yes: describe their nature? What suggestions this research might have to the SHACL community and to the further development of QA catalogue?</li>
  <li>Comparing the results of KBR and QA catalogue approaches, what suggestions this research might have to both parties?</li>
</ul>

<p>Partners: </p>
<ul>
  <li>British Library</li>
  <li>KBR</li>
</ul>

<p>Data sources:</p>
<ul>
  <li>Catalogue of British Library</li>
  <li>Catalogue of KBR</li>
</ul>
<h2 class="c18" id="h.t5dz9y5v47ws"><span class="blue">I.2</span> UNIMARC</h2>
<p>The UNIMARC bibliographic format <a href="#ftnt11" id="ftnt_ref11">[11]</a> was first created and proposed by IFLA in 1977, with the title <em>UNIMARC: Universal MARC format</em>. The intention of the standard was to unify different MARC versions into a single schema (note: MARC21 had the same intention). It was updated several times, the current version is the 3rd edition. As for MARC21 there are bibliographic, authorities, classification and holdings sub-schemas. UNIMARC records are serialised in ISO 2709 (which is the basis of all MARC versions), and XML. It is in use in France, Italy, Portugal, Slovenia, Slovakia, Ukraina, Belarus, Russia. There is no machine readable version of the schema.</p>

<p>Research questions and tasks (Computer Science): </p>
<ul>
  <li>Write scripts which downloads UNIMARC records from the data sources via OAI-PMH and Z39.50 protocols. The scripts should handle the shortcomings of these protocols and the actual implementations.</li>
  <li>Create a machine readable UNIMARC schema, either as a set of Java classes according to the QA catalogue&#39;s MARC definition structure or to the JSON based Avram schema. <a href="#ftnt12" id="ftnt_ref12">[12]</a> It is also possible to implement it with other technology which can be exported into Avram schema.</li>
  <li>Modify QA catalogue backend to be able to use the above mentioned definition as an input configuration for the quality assessment processes.</li>
  <li>Adopt the user interface of QA catalogue to work with the output of the analysis</li>
</ul>

<p>Research questions and tasks (Humanities): </p>
<ul>
  <li>How has the UNIMARC schema changed historically, and how to match the proper schema with the records?</li>
  <li>Are there locally defined data elements in particular libraries? Are these documented? How could they be transformed as an input to QA catalogue, so it should understand them and apply the rules during the analyses?</li>
  <li>Literature scan: are there specific papers regarding UNIMARC quality assessment? Are the specific aspects of the structure or the content of the schema which are not available in MARC21 schema?</li>
  <li>Communicate with the data source and collect feedback. How could they use the report in daily work? Are there relevant needs which the result doesn’t fulfil? What are their data life cycles and relevant workflow, and how QA catalogue could be inserted into it?</li>
</ul>

<p>Possible partners:</p>
<ul>
  <li>Agence bibliographique de l&#39;emseignement supérieur (ABES), Montpellier, France, the maintainer of SUDOC, <a href="#ftnt13" id="ftnt_ref13">[13]</a> the French union catalogue of academic libraries</li>
  <li>Institut informacijskih znanosti (IZUM), Maribor, Slovenia, the maintainer of COBISS+, the Slovenian union catalogue</li>
  <li>Portugal National Library</li>
  <li>Italian National Library, Firenze</li>
</ul>

<p>Data sources:</p>
<ul>
  <li>SUDOC (from ABES)</li>
  <li>Portugal National Library</li>
  <li>COBISS+, the virtual library of Slovenia, one-stop access to information from 919 Slovenian libraries</li>
  <li>Italian National Library, Firenze <a href="#ftnt14" id="ftnt_ref14">[14]</a></li>
  <li>The catalogue of the Biblioth&egrave;que nationale de France (the French national library) <a href="#ftnt15" id="ftnt_ref15">[15]</a></li>
</ul>
<h2 class="c18" id="h.d18pz1c4a259"><span class="blue">I.3</span> PICA and PICA+</h2>
<p>PICA and PICA+ are metadata schemas for describing bibliographic resources, mainly used in Dutch and German libraries (instead of MARC). These schemas contain a fixed set of data elements, but libraries can define their own extra elements. Jakob Vo&szlig; maintains an Avram schema for PICA+. There is some initial code in the QA catalogue which reads Avram schema and uses it as an input for model building against which the analyses can be run.</p>

<p>Research questions and tasks (Computer Science): </p>
<ul>
  <li>Finalise Avram schema reader </li>
  <li>Finalise a record reader which takes an Avram schema, parse records which are in the schema describe by the Avram schema (in this case PICA), and creates Java objects for each record</li>
  <li>Modify QA catalogue that it could validate the objects created the above mentioned mechanism, and produce the same output as it creates for MARC records</li>
</ul>

<p>Research questions and tasks (Humanities): </p>
<ul>
  <li>How has the PICA/PICA+ schema changed historically, and how to match the proper schema with the records?</li>
  <li>Are there locally defined data elements in particular libraries? Are these documented? How could they be transformed as an input to QA catalogue, so it should understand them and apply the rules during the analyses?</li>
  <li>Literature scan: are there specific papers regarding PICA/PICA+ quality assessment? Are there specific aspects of the structure or the content of the schema which are not available in MARC21 schema?</li>
  <li>Communicate with the data source and collect feedback. How could they use the report in daily work? Are there relevant needs which the result doesn’t fulfil? What are their data life cycles and relevant workflow, and how QA catalogue could be inserted into it?</li>
</ul>

<p>Partner: GVD</p>
<ul>
  <li>Gemeinsamer Bibliotheksverbund (GBV), Göttingen</li>
</ul>

<p>Data sources:</p>
<ul>
  <li>K10Plus union catalogue, 60+ million records (maintained by GBV)</li>
</ul>
<h2 class="c18" id="h.fbhlo0fq8hyu"><span class="blue">I.4</span> Encoded Archival Description (EAD) and Encoded Archival Context (EAC)</h2>
<p>Encoded Archival Description is an XML schema to describe archival records, Encoded Archival Context is for describing the authorised form of named entities (persons, families, corporate bodies) that appeared in the archival records (similar to the authority records of a library catalogue). The challenging part of EAD is the hierarchical nature. Archival records form a large, multi-level hierarchy, where each level describes smaller parts of the collection up to single documents. However these levels do not always have the same nature. There are standard names for some distinct levels, but not all collections have the same number of levels and the same structure. It depends on lots of factors, such as the practice of the institution the collection comes from, the importance of the documents etc. On the other hand the number of data elements describing the properties of the levels is much less than that of the MARC schemas. The largest open access collection of these records are the Archives Portal Europe <a href="#ftnt16" id="ftnt_ref16">[16]</a> and National Archives and Records. <a href="#ftnt17" id="ftnt_ref17">[17]</a> Both provide APIs we can use in this research.</p>

<p>Research questions and tasks (Computer Science): </p>
<ul>
  <li>Create MQAF API compliant schemas from EAD/EAC XML schema. Take care of the hierarchical nature of the structure.</li>
  <li>Create a user interface which fits to the specific features of EAD/EAC records. Take care of the hierarchical nature of the structure.</li>
</ul>

<p>Research questions and tasks (Humanities): </p>
<ul>
  <li>Literature review on the analyses of EAD/EAC records, focusing on the data quality aspects</li>
  <li>Survey archivist and researchers who work with archival metadata about the metadata quality aspects. Based on the findings define a set of requirements against EAD/EAC records.</li>
  <li>Test the implementation, and create an evidence-based report on the quality related issues found in a concrete archival collection.</li>
  <li>Communicate the findings with the institution and get feedback about them. Did they know about the issues? How do they solve quality issues? Does the report “overlook” some issues they know?</li>
</ul>

<p>Partners: </p>
<ul>
  <li>Archives Portal Europe (The Hague)</li>
  <li>National Archives and Records (Washington DC)</li>
</ul>

<p>Data sources:</p>
<ul>
  <li>Archival Portal Europe</li>
  <li>National Archives and Records (Washington DC)</li>
</ul>
<h2 class="c18" id="h.kbbv9oz8aewp"><span class="blue">I.5</span> International Standard Bibliographic Description (ISBD)</h2>
<p>International Standard Bibliographic Description (ISBD) <a href="#ftnt18" id="ftnt_ref18">[18]</a> contains a set of rules about the content of data elements in library catalogue records to offer consistency when sharing bibliographic information. It is mostly used in European libraries (Anglo-Saxon libraries are using a similar set of rules, Anglo-American Cataloguing Rules). It mainly focuses on descriptive metadata. National cataloguing rules are usually derived from the ISBDs, but with a number of significant differences in distinct libraries. ISBD also provides a human readable, language independent representation of the records (by setting the (in)famous “punctuation rules” where dots, colons, slashes have context-dependent semantic meaning). </p>

<p>ISBD could be used within MARC records. The record should contain information about if ISBD has been applied or not. The MARC21 standard itself does not document ISBD rules, so in order to validate MARC, an extra ISBD validation layer is necessary. IFLA&#39;s ISBD web page says that &quot;The ISBD review group also maintains an ISBD RDF/XML schema, to enable libraries to publish their metadata as linked data&quot; - however at time of writing this document I haven’t found it. This schema may or may not provide a starting point to this research.</p>

<p>Research questions and tasks (Computer Science): </p>
<ul>
  <li>Find and investigate the above mentioned RDF/XML schema</li>
  <li>Investigate the ISBD documentation</li>
  <li>Create a machine readable, MQAD API compliant ruleset from the ISBD rules (either as Java code or a YAML/JSON configuration file)</li>
  <li>Run analyses in QA catalogue</li>
</ul>

<p>Research questions and tasks (Humanities): </p>
<ul>
  <li>Literature review on ISBD, focusing on the data quality aspects</li>
  <li>Survey library metadata experts and researchers who work with ISBD based records about the metadata quality aspects. Based on the findings, define a set of requirements against ISBD data elements as a textual document or with SHACL expressions. </li>
  <li>Test the implementation, and create an evidence-based report on the quality related issues found in particular catalogues.</li>
</ul>

<p>Partners:</p>
<ul>
  <li>British Library</li>
  <li>any other library who applies ISBD in their catalogue</li>
</ul>

<p>Data sources:</p>
<ul>
  <li>British Library catalogue</li>
</ul>
<h2 class="c18" id="h.4nxautqtaory"><span class="blue">I.6</span> Anglo-American Cataloguing Rules (AACR2)</h2>
<p>AACR2 contains a set of rules about the content of data elements in the catalogue records used in English and US libraries. </p>

<p>AACR2 could be used within MARC records. The record should contain information about if AACR2 has been applied or not. The MARC21 standard itself does not document AACR2 rules, so in order to validate MARC, an extra AACR2 validation layer is necessary. It is not clear if there is a machine readable representation of the AACR2 ruleset.</p>

<p>Research questions and tasks (Computer Science): </p>
<ul>
  <li>Investigate if there is a machine readable (RDF/XML schema) representation of the AACR2</li>
  <li>Investigate the AACR2 documentation</li>
  <li>Create a machine readable, MQAD API compliant ruleset from the AACR2 rules (either as Java code or a YAML/JSON configuration file)</li>
  <li>Run analyses in QA catalogue</li>
</ul>

<p>Research questions and tasks (Humanities): </p>
<ul>
  <li>Literature review on AACR2, focusing on the data quality aspects</li>
  <li>Survey library metadata experts and researchers who work with AACR2 based records about the metadata quality aspects. Based on the findings, define a set of requirements against AACR2 data elements as a textual document or with SHACL expressions.</li>
  <li>Test the implementation, and create an evidence-based report on the quality related issues found in particular catalogues.</li>
</ul>

<p>Data sources:</p>
<ul>
  <li>Library of Congress catalogue</li>
</ul>

<h2 class="c18" id="h.qokm407em93v"><span class="blue">I.7</span> MAQUIS&ndash;The quality of the terms in the metadata records and of the Knowledge Organising Systems</h2>
<p>Previous research almost exclusively focused on the quality of Knowledge Organising Systems, and most of them did not release open source tools to help institutions to measure their own data. This research aims to evaluate existing metrics, to propose new metrics and methods and to develop implementation for both aspects. The research will intensively use large library catalogues (such as EconBiz, SUDOC and Gemeinsamer Verbundkatalog, B3Kat and others) and the KOSes linked to them, however both the proposed theoretical model and the software package should be applicable to other bibliographical catalogues.</p>

<p>Additionally, the metadata records and the KOS together form three networks:</p>
<ul>
  <li>a record-subject network (records have subjects)</li>
  <li>a subject co-occurrence network,</li>
  <li>and the network of records which are connected by subjects and other kinds of authority entries (e.g. persons, organisations, events etc.).</li>
</ul>

<p>We will measure the standard properties of these networks (density, components, clusters, connectedness, degree distribution, PageRank, Small-World).</p>

<p>Two types of output are expected:</p>
<ul>
  <li>scientific publication(s): thesis, scientific paper, conference presentation</li>
  <li>two open source software packages: a standalone tool which measures the quality of bibliographical records and KOS, and a plugin which integrates this tool into the QA catalogue quality assessment software. </li>
</ul>

<p>If the results of the research will be promising, and evaluated as usable by the partner institutions, and if there will be an interest in implementation or deployment of the same, we will also investigate the possibility of integration into the existing IT infrastructure of the organisation.</p>

<p>The project follows the principles of repeatable research and of maintainable research software development (part of the research data is open data, code will be properly tested, documented, and citable, communication will be transparent).</p>

<p>Research questions and tasks (Computer Science): </p>
<ul>
  <li>Analyse the bipartite (record-subject) network. Does the basic properties of the network reveal anything about the quality of subject indexing?</li>
  <li>How subject indexing supports retrieval?</li>
  <li>How the intrinsic quality features of the KOS affects the usage of the records?</li>
  <li>Is there a correlation between the quality of subject indexing and other known quality dimensions?</li>
</ul>

<p>Research questions and tasks (Humanities): </p>
<ul>
  <li>Literature review on data quality aspects of subject indexing</li>
  <li>Survey library metadata experts and researchers who work in the subject indexing field about the metadata quality aspects. Based on the findings, define a set of requirements against AACR2 data elements as a textual document or with SHACL expressions.</li>
  <li>Test the implementation, and create an evidence-based report on the quality related issues found in particular catalogues. </li>
</ul>

<p>Partners:</p>
<ul>
  <li>Agence bibliographique de l&#39;emseignement supérieur (ABES), Montpellier</li>
  <li>Gemeinsamer Bibliotheksverbund (GBV), Göttingen</li>
  <li>ZWB &ndash; Leibniz-Informationszentrum Wirtschaft</li>
</ul>

<p>Data sources:</p>
<ul>
  <li>EconBiz catalogue of ZWB</li>
  <li>Syst&egrave;me Universitaire de Documentation (SUDOC) of ABES</li>
  <li>Gemeinsamer Verbundkatalog (GVK) of GBV and SWB</li>
</ul>
<h2 class="c18" id="h.p8xbhn17yv0m"><span class="blue">I.8</span> Citation data</h2>
<p>Citation data, or bibliographic data of scholarly articles is a neuralgic point for the libraries. In the “Western World” and for large languages, the publishers are those players which traditionally built databases for the scholarly articles (such as Web of Knowledge, Scopus) instead of libraries. By and large there have been exceptions even in Western European countries. In case of smaller languages and for poorer countries the large publishers do not see the market value to publish scientific journals in vernacular languages therefore those journals are not covered in their databases. In the last two decades several different projects have been launched to make these metadata out of “paywalls”. The largest of these projects is the DOI database, but the larger part of DOI metadata is also not freely available, however the Initiative for Open Citations 16 works on making the citation data open. Recently WikiCite <a href="#ftnt19" id="ftnt_ref19">[19]</a> is the largest freely available citation database based on the bibliographic data imported into Wikidata. <a href="#ftnt20" id="ftnt_ref20">[20]</a> It provides a query interface and [database dumps](http://wikicite.org/access.html). Together with Jakob Vo&szlig;, a volunteer of WikiCite and Wikidata we started a research project 20 to analyse the data. This research is in a preliminary stage. Now I highlight only one feature of the citation data namely page numbers, which seems to be simple, but reveals some complex problems. One can expect that page numbers are arabic or roman numbers separated by dashes and commas (sometimes with some text before or after the numbers). I found several hundred patterns, which do not fit this expectation. Here I show three issues with “strange” page numbers. Wikidata uses a language neutral notation for describing its semantic structure, the entities are denoted by &lsquo;Q’ and a number, while properties are denoted by &lsquo;P’ and a number. For example: P304 <a href="#ftnt21" id="ftnt_ref21">[21]</a> is the property of the page numbers. Its human readable label in English is “page(s)”.</p>

<p>Some known problems with the page number properties:</p>

<p>1. Using article identifier as page number</p>

<p>Q40154916 <a href="#ftnt22" id="ftnt_ref22">[22]</a>: “e0179574” -- This article was published in PLoS ONE. The publisher provides citation text, and metadata in RIS and BibTeX format. The citation contains &lsquo;e0179574’, however it does not explain what exactly it means (as it neither explains any other elements). e0179574 is an article identifier.</p>

<p>Q21820630 <a href="#ftnt23" id="ftnt_ref23">[23]</a>: “c181” -- This paper was published in the British Medical Journal. It does not have a PDF version, the only available online version is HTML which does not have page numbers at all. c181 is an article identifier.</p>

<p>In both examples even the publisher exports bad data claiming article numbers as page number metadata.</p>

<p>2. Wikidata contains extra info, which is not available elsewhere</p>

<p>Q39877401 <a href="#ftnt24" id="ftnt_ref24">[24]</a>: ”108-17; quiz 118-9” -- &quot;quiz 118-9&quot; does not appear anywhere in the publisher or DOI metadata. Wikidata does not have a note about the source of this piece.</p>

<p>3. Wikidata uses page number field to add comment</p>

<p>Q28710224 <a href="#ftnt25" id="ftnt_ref25">[25]</a>: ”E3523; author reply E3524&ndash;5” -- E3524&ndash;5 is not part of the article. It is a related article, which is also available in Wikidata (as Q28710226 <a href="#ftnt26" id="ftnt_ref26">[26]</a>). These two articles are not interlinked with distinct properties. One could suppose that the occurrence &lsquo;author reply’ in other Wikidata records’ page number could reveal similar hidden links.</p>

<p>Some analyses are available in this repository: <a href="https://github.com/pkiraly/metadata-qa-wikidata/">https://github.com/pkiraly/metadata-qa-wikidata/</a>.</p>

<p>Research questions and tasks (Computer Science): </p>
<ul>
  <li>What are the basic quality dimensions applicable to citation data?</li>
  <li>How does quality of citation data affect scientometrics?</li>
  <li>If there is a correlation, is there a known method from scientometrics’ side to minimize it?</li>
</ul>

<p>Research questions and tasks (Humanities): </p>
<ul>
  <li>Literature review on data quality aspects of citation data</li>
  <li>Survey library metadata experts and researchers who work with citation records about the metadata quality aspects. Based on the findings, define a set of requirements against citation data elements as a textual document or with SHACL expressions.</li>
  <li>Test the implementation, and create an evidence-based report on the quality related issues found in particular catalogues.</li>
  <li>How can we fix derivative data (e.g. a citation found in Wikidata or other open access repository) in a way that the fix would be applicable to the source data (the publisher!s side)? Would it be a different approach for commercial and not-for-profit publishers?</li>
</ul>

<p>Data sources:</p>
<ul>
  <li>WikiCite <a href="#ftnt27" id="ftnt_ref27">[27]</a></li>
  <li>Crossref data dumps <a href="#ftnt28" id="ftnt_ref28">[28]</a></li>
  <li>Open Citations corpus <a href="#ftnt29" id="ftnt_ref29">[29]</a></li>
</ul>
<h2 class="c18" id="h.jqbwpwbff8w0"><span class="blue">I.9</span> MARC authority records</h2>
<p>The QA catalogue analyses MARC21 <em>bibliographic</em> records. MARC21 and UNIMARC also have a distinct schema for authority records. They describe contextual information: subject or name vocabularies which contain standardised form of names for people, corporate bodies, meetings, titles, and subjects referred in the bibliographical records. On the authority record the standardised form is the key element for which the record was made, so it is also called the heading. These records provide authority control, i.e. establishing a recognized form for an entity name and using that form whenever the name is needed as an access point in a bibliographic record. The record has three main components: headings, cross references, and notes. The authority schema is similar in structure to that of the bibliographic schema, but it contains much less data elements.</p>
<p>Short introduction: <a href="https://www.loc.gov/marc/uma/pt1-7.html">https://www.loc.gov/marc/uma/pt1-7.html</a>.</p>

<p>Research questions and tasks (Computer Science): </p>
<ul>
  <li>How to transform MARC21 authority schema into Java classes the same way as bibliographic record schema elements are implemented in QA catalogue?</li>
  <li>How to create a mechanism where the user can tell QA catalogue to analyse authority records instead of bibliographic records?</li>
  <li>How to report the results? What would be the ideal user interface? </li>
</ul>

<p>Research questions and tasks (Humanities): </p>
<ul>
  <li>Literature review on data quality aspects of authority data</li>
  <li>Survey library metadata experts and researchers who work with authority records about the metadata quality aspects. Based on the findings, define a set of requirements against authority data elements as a textual document or with SHACL expressions.</li>
  <li>Test the implementation, and create an evidence-based report on the quality related issues found in particular catalogues.</li>
</ul>

<p>Partners:</p>
<ul>
  <li>KBR</li>
</ul>

<p>Data sources:</p>
<ul>
  <li>authority records of KBR catalogue</li>
  <li>authority records Library of Congress catalogue</li>
</ul>
<h2 class="c18" id="h.1u2r1ewy6o6s"><span class="blue">I.10</span> Agile Qualit&auml;tssicherung von Metadaten zu kulturellen Objekten im Kontext von Datenintegrationsprozessen</h2>

<p>The aim of this project is to invent semi-automatic mechanisms which translate quality criteria against metadata expressed in natural language into a machine actionable form which could be used as an input in a quality assessment process.</p>

<p>Administrative status: submitted proposal</p>

<p>Research questions and tasks (Computer Science): </p>
<ul>
  <li>Given a complex, hierarchical metadata schema in XML format. How to implement the following user scenario: the user - with limited technical knowledge (typically a metadata creator or integrator) - enters a human readable input, such as “title” or “genre” in a graphical interface, and the application returns XPath expression(s) which can be generated based on the metadata schema’s structure and the input? The user should be able to test the expression instantly on test records. The user should be able to modify the input, or the XPath expression.</li>
  <li>How to extend this application to work with other serialization formats and query languages?</li>
  <li>How to embed the resulted expression into conditional statements, such as “find records where title is missing” or “find records where birth date is larger than death date”?</li>
  <li>How to transform these statements into SHACL-like expressions?</li>
</ul>

<p>Research questions and tasks (Humanities): </p>
<ul>
  <li>What are the common metadata quality problems in Lightweight Information Describing Objects (LIDO) <a href="#ftnt30" id="ftnt_ref30">[30]</a> records?</li>
  <li>What are the common metadata quality problems in TEI <a href="#ftnt31" id="ftnt_ref31">[31]</a> records?</li>
</ul>

<p>Partners:</p>
<ul>
  <li>SUB</li>
  <li>Fachbereich Mathematik und Informatik, Philipps-Universit&auml;t Marburg</li>
  <li>Deutsche Digitale Bibliothek</li>
</ul>

<h1 id="h.onhgw5ps1do1"><span class="blue">II.</span> Cultural analytics / Bibliographic data science</h1>

<p>These topics utilise catalogue as source data or evidence which could be used to answer Humanities research questions. The bibliographic data contains some generally available factual dimensions, such as personal names of authors and contributors (occasionally with additional properties), the place and date of publication, the name of publisher/printer/scriptor, genre, the subject description of the content (keywords, classification terms), the physical properties of the document, occasionally provenance (current and previous holding institutions, owners). After (more or less) data cleaning all these draw some historical patterns, such as how the roles of different languages changed, how the literary canon evolved, who were the important authors and books in a particular periods, which were enduring and ephemeral successes, how the media changed, and how all these correlated with each other?</p>

<p>Some important publications, which could be used as examples of such researches:</p>

<ul>
  <li>Andrew Prescott. (2013). “Bibliographic Records as Humanities Big Data.” In 2013 IEEE International Conference on Big Data, 55&ndash;58, 2013. <a href="https://doi.org/10.1109/BigData.2013.6691670">https://doi.org/10.1109/BigData.2013.6691670</a>.</li>
</ul>
<ul>
  <li>Michael F. Suarez. (2009). “Towards a bibliometric analysis of the surviving record, 1701&ndash;1800.” in The Cambridge History of the Book in Britain, Volume 5: 1695&ndash;1830, Cambridge University Press, 2009. pp. 37-65. <a href="https://doi.org/10.1017/CHOL9780521810173.003">https://doi.org/10.1017/CHOL9780521810173.003</a></li>
  <li>Sandra Tuppen, Stephen Rose, and Loukia Drosopoulou (2016). “Library Catalogue Records as a Research Resource: Introducing &lsquo;A Big Data History of Music.’” Fontes Artis Musicae 63, no. 2:67&ndash;88. <a href="https://doi.org/10.1353/fam.2016.0011">https://doi.org/10.1353/fam.2016.0011</a></li>
  <li>Tolonen, M., M&auml;kel&auml;, E., Marjanen, J., Kanner, A., Lahti, L., Ginter, F., Salmi, H., Vesanto, A., Nivala, A., Rantala, H., &amp; Sippola, R. (2018). Metadata analysis and text reuse detection: Reassessing public discourse in Finland through newspapers and journals 1771&ndash;1917. Paper presented at digital humanities in the Nordic countries DHN2018, Helsinki, Finland. <a href="https://researchportal.helsinki.fi/en/publications/metadata-analysis-and-text-reuse-detection-reassessing-public-dis">https://researchportal.helsinki.fi/en/publications/metadata-analysis-and-text-reuse-detection-reassessing-public-dis</a></li>
  <li>Lahti, L., Marjanen, J., Roivainen, H., &amp; Tolonen, M. (2019). Bibliographic data science and the history of the book (c. 1500&ndash;1800). Cataloging &amp; Classification Quarterly, 57(1), 5&ndash;23. <a href="https://doi.org/10.1080/01639374.2018.1543747">https://doi.org/10.1080/01639374.2018.1543747</a></li>
  <li>Marjanen, J., Kurunm&auml;ki, J. A., Pivovarova, L., &amp; Zosa, E. (2020). The expansion of isms, 1820&ndash;1917: Data-driven analysis of political language in digitized newspaper collections. Journal of Data Mining and Digital Humanities, HistoInformatics, 1&ndash;28. <a href="https://jdmdh.episciences.org/6728">https://jdmdh.episciences.org/6728</a></li>
  <li>Mikko Tolonen, Mark J. Hill, Ali Ijaz, Ville Vaara, Leo Lahti. (2021). Examining the Early Modern Canon : The English Short Title Catalogue and Large-Scale Patterns of Cultural Production. In Ileana Baird (eds.) Data Visualization in Enlightenment Literature and Culture. Cham : Palgrave Macmillan, 2021. pp. 63-119 <a href="https://doi.org/10.1007/978-3-030-54913-8_3">https://doi.org/10.1007/978-3-030-54913-8_3</a></li>
  <li>Simon Burrows. (2021). In Search of Enlightenment: From Mapping Books to Cultural History. In: Baird, I. (eds) Data Visualization in Enlightenment Literature and Culture . Palgrave Macmillan, Cham. <a href="https://doi.org/10.1007/978-3-030-54913-8_2">https://doi.org/10.1007/978-3-030-54913-8_2</a></li>
</ul>
<h2 class="c18" id="h.fjpp9yjyg95z"><span class="blue">II.1</span> Kinder- und Jugendbücher international. Eine Metadatenanalyse</h2>
<p>Kinder- und Jugendliteratur (KJL) galt schon Paul Hazard (1952) als die erste Weltliteratur und seine Einsch&auml;tzung trifft heute mehr denn je zu. Denn Kinder- und Jugendliteratur ist wesentlich vom internationalen Lizenzgesch&auml;ft bestimmt, übersetzungen und Adaptionen von Illustrationen spielen eine prominente Rolle. Spitzentitel wie &bdquo;Harry Potter“ bestimmen den Buchmarkt und das Lesen wie keine andere Sachgruppe. Am drittgrö&szlig;ten, dem deutschsprachigen Publikumsbuchmarkt hat die KJL einen Marktanteil von etwa einem Drittel, auf dem chinesischen Publikumsbuchmarkt soll die KJL sogar die grö&szlig;te Sachgruppe bilden. Kaum eine andere Gruppe gew&auml;hrt daher einen so genauen Einblick in die Internationalisierung und Globalisierung der Kultur wie eben die KJL. </p>

<p>Eine Arbeitsgruppe der Mainzer Buchwissenschaft erarbeitet aus verschiedenen Daten einen Weltatlas der Literatur. Vorbild ist das Projekt der Oxforder Arbeitsgruppe um Max Roser &bdquo;Our World in Data“. W&auml;hrend &bdquo;Our World in Data“ vor allem aktuelle Daten zur globalen sozialen Welt sammelt, soll unser Projekt Daten zur Kultur sammeln (&bdquo;Our Culture in Data“), zun&auml;chst einmal Daten zur Literatur. Doch Daten zur Kultur zu erheben ist schwierig, da mit den Sozialwissenschaften vergleichbare Datenerhebungen nur vereinzelt durchgeführt werden, etwa zu Museumsbesuchen, der Zahl der Klassikfestivals oder dann auch zu der Zahl der verkauften Bücher. Diese Zahlen werden fast ausschlie&szlig;lich national erhoben nach nicht vergleichbaren Parametern. Die Daten über das Leseverhalten in Europa beispielsweise werden so unterschiedlich erhoben, dass eine Aggregation derzeit nicht sinnvoll möglich ist.</p>

<p>W&auml;hrend diese potenziellen Daten zur Kultur noch viel Aufbereitung bedürfen, gibt es eine Quelle für eine datenbasierte Analyse der weltweiten Kultur, die bislang wenig genutzt wurde. Das sind Bibliothekskataloge. Sie wurden oft über Jahrhunderte gepflegt, haben Standards der Datenerfassung entwickelt und ein gemeinsames Verst&auml;ndnis des Verzeichniswerten erarbeitetet. Sie werden vor allem zum Auffinden genutzt, aber nur in wenigen buchwissenschaftlichen Studien auch als Quelle zum Verst&auml;ndnis von Kultur (Zedelmaier, 2016; Duncan 2021). In dieser schmalen Linie kulturwissenschaftlicher Forschung verstehen wir Bibliothekskataloge als institutionell verdichtetes und verstetigtes Wissen über Kultur. Unser Startpunkt ist die Kinder- und Jugendliteratur, die seit dem 19. Jahrhundert als eine eigene Rubrik auch in der DNB bzw. ihren Vorl&auml;ufern verzeichnet wurde. Umfangreiche Sammlungen und Sonderbest&auml;nde in verschiedenen Bibliotheken erlauben eine sowohl historische wie systematische Ann&auml;herung an das, was als Kinder- und Jugendbuch (vor-)gelesen wurde und wird.</p>

<p>Ziel des Vorhabens ist also am Beispiel der Kinder- und Jugendliteratur zu analysieren, welche Kinder- und Jugendliteratur wo gesammelt wurde und wird, welche Publikationsformen, Gattungen und Genres, für welche Altersgruppen verzeichnet wurden. Unser Interesse gilt also den Metadaten. Wir erhoffen uns eine quantitativ valide Antwort auf die Frage, was für KJL liest die Welt.</p>

<p>Research questions and tasks (Computer Science): </p>
<ul>
  <li>Find how to extract information about if a particular record belongs to the category of children and youth literature, along with other information of the book (title, authors, publication date, publisher)</li>
  <li>Visualise the extracted information with timeline and map</li>
</ul>

<p>Research questions and tasks (Humanities): </p>
<ul>
  <li>How information about if a particular record belongs to the category of children and youth literature is encoded in metadata records</li>
  <li>How has this category changed over the times?</li>
  <li>Are there regional differences in the application of the category?</li>
</ul>

<p>Partners:</p>
<ul>
  <li>Prof. Dr. Gerhard Lauer, Dr. Wei Ding &ndash; Buchwissenschaft, Johannes Gutenberg-Universit&auml;t Mainz</li>
  <li>Deutsche Nationalbibliothek</li>
</ul>
<h2 class="c18" id="h.55thhjh5aks2"><span class="blue">II.2</span> Patterns of translations of national literatures</h2>
<p>Some kinds of bibliographical records make it possible to reveal patterns of translations from a particular national literature. Lots of interesting features can be extracted from the data, such as the changing of the target languages (which other literature were interested in the source literature?), of publication places and translators (were the translations been created at home or abroad?), of the volume, of publishers (what was the prestige of the author?). Were there any key languages which helped the literature to enter world literature (for example for a long time German translations of Hungarian works preceded other translations, and sometimes those other translations are created from German, not from Hungarian). </p>

<p>UNESCO maintains a dedicated database (Index Translationum) into which national libraries send records about translated works. This database typically contains information about books, but not in an analytical manner (e.g. without the analyses of the parts of the book, which would be important if it is an anthology with multiple translations) and does not cover publications in periodicals. On the other hand there are some dedicated databases and bibliographies concentrating on particular aspects (like translations from a given language, or of works in a genre, or an author), but with greater details than that of the Index Translationum.</p>

<p>There is a distinct scientific branch called translation studies, which also includes empirical research, however most of them utilise Index Translationum as a single source. The niche of this current research is to try to overcome the above mentioned limitation of this central data source, and shading light to phenomena which could be revealed only from others sources.</p>

<p>Research questions and tasks (Computer Science): </p>
<ul>
  <li>How to extract relevant information from semi structured data sources?</li>
  <li>How can different types of data be normalised?</li>
  <li>How can this data be enriched with external data sources (e.g. library catalogues)?</li>
  <li>Once the data are normalised, what exploratory data analysis methods can be created to help answering the humanities research questions below?</li>
  <li>Are there any feedback or suggestions for the data providers? Is there an improved dataset which can be given back to the data providers?</li>
</ul>

<p>Research questions and tasks (Humanities): </p>
<ul>
  <li>How translations are changing through time, what are the temporal patterns?</li>
  <li>How translations are changing through space, what are the spatial patterns?</li>
  <li>What are the missing information types in a particular data source?</li>
  <li>What are the relevant external data sources for an enrichment process?</li>
  <li>How has the medium (the format of publishing) changed over time?</li>
  <li>What languages have been important over time?</li>
  <li>Are there correlations between the above mentioned factors (time, space, format, language, authors)?</li>
  <li>What would be the optimal communication format based on the findings?</li>
</ul>

<p>Data sources:</p>
<ul>
  <li>UNESCO&#39;s Index Translationum <a href="#ftnt32" id="ftnt_ref32">[32]</a></li>
  <li>national bibliographies</li>
  <li>Bibliographica Hungarica <a href="#ftnt33" id="ftnt_ref33">[33]</a></li>
</ul>

<p>Partners:</p>
<ul>
  <li>Prof. András Kiséry, City College of New York</li>
</ul>

<h2 class="c18" id="h.qkgqr5bgpxh2"><span class="blue">II.3</span> Patterns of publications</h2>

<p>National bibliographies aim to describe all the books published in a given country (however none of them are complete). This huge set of information is not well exploited from the perspective of cultural history, because they are usually accessible only via a search interface with limited feature set, which doesn’t enable researchers to extract information, and run statistical analyses on them. The side effect of the QA catalogue project is that the tools created there are generic tools, and can be utilised for data extraction. The library catalogue records may or may not contain information in standardised form (see section on MARC Authority records), which may or may not involve data cleaning in the process. At the end we could extract information from the catalogue such as authors and other collaborators, place names including publication place and places which the book is talking about, subjects (in human readable or in encoded form), dates, language of publication, physical dimensions of the publications and several other data elements. In some MARC records some of these entities found in descriptive data elements have authorised formats attached to the same record. These authorised formats however usually do not inform the reader about which data element they belong to. The two forms are different, and maybe differently segmented as well.</p>

<p>Research questions and tasks (Computer Science): </p>
<ul>
  <li>How could the entities found in the descriptive data elements be paired with the authorised form? Which relevant data elements do not have authorised forms?</li>
  <li>Could this knowledge (non authorised form - authorised form) be reused for a suggesting application in case of records where the normalised part is missing? How other data elements can be used in such an application which provides larger context (related to information on what? who? where? when?).</li>
  <li>How external information sources could be reused (e.g. Geonames, <a href="#ftnt34" id="ftnt_ref34">[34]</a> VIAF, <a href="#ftnt35" id="ftnt_ref35">[35]</a> CERL Thesaurus, <a href="#ftnt36" id="ftnt_ref36">[36]</a> Share-VDE <a href="#ftnt37" id="ftnt_ref37">[37]</a> etc.) to normalise entities?</li>
</ul>

<p>Research questions and tasks (Humanities): </p>
<ul>
  <li>How has the importance of cities as publication places changed?</li>
  <li>What was the ratio of vernacular and foreign languages (Latin, German, Russian, English) in different periods?</li>
  <li>How did the connection between the format and the genre change over time?</li>
  <li>What other countries had the most impact (measured by the number of their publications held in the library under scrutiny) in different times?</li>
</ul>

<p>Partners: </p>
<ul>
  <li>DARIAH Bibliographical Data Working Group <a href="#ftnt38" id="ftnt_ref38">[38]</a></li>
  <li>libraries</li>
</ul>

<p>Data source:</p>
<ul>
  <li>library catalogues</li>
</ul>

<hr class="c20">

<div id="notes">
<p><a href="#ftnt_ref1" id="ftnt1">[1]</a> <a href="https://www.gwdg.de/">https://www.gwdg.de/</a></p>
<p><a href="#ftnt_ref2" id="ftnt2">[2]</a> <a href="https://uni-goettingen.de/">https://uni-goettingen.de/</a></p>
<p><a href="#ftnt_ref3" id="ftnt3">[3]</a> <a href="https://www.mpg.de/en">https://www.mpg.de/</a></p>
<p><a href="#ftnt_ref4" id="ftnt4">[4]</a> <a href="https://github.com/pkiraly/metadata-qa-api">https://github.com/pkiraly/metadata-qa-api</a></p>
<p><a href="#ftnt_ref5" id="ftnt5">[5]</a> <a href="https://github.com/pkiraly/metadata-qa-marc">https://github.com/pkiraly/metadata-qa-marc</a></p>
<p><a href="#ftnt_ref6" id="ftnt6">[6]</a> <a href="https://www.loc.gov/marc/">https://www.loc.gov/marc/</a></p>
<p><a href="#ftnt_ref7" id="ftnt7">[7]</a> <a href="https://www.w3.org/TR/shacl/">https://www.w3.org/TR/shacl/</a></p>
<p><a href="#ftnt_ref8" id="ftnt8">[8]</a> Resource Description Framework, <a href="https://www.w3.org/RDF/">https://www.w3.org/RDF/</a></p>
<p><a href="#ftnt_ref9" id="ftnt9">[9]</a> &bdquo;Validating JSON, XML and CSV data with SHACL-like constraint” slides of presentation held at DINI-KIM 2022, <a href="https://bit.ly/qa-dini-kim-2022">https://bit.ly/qa-dini-kim-2022</a></p>
<p><a href="#ftnt_ref10" id="ftnt10">[10]</a> <a href="http://marcspec.github.io/MARCspec/marc-spec.html">http://marcspec.github.io/MARCspec/marc-spec.html</a></p>
<p><a href="#ftnt_ref11" id="ftnt11">[11]</a> <a href="https://www.ifla.org/publications/unimarc-formats-and-related-documentation/">https://www.ifla.org/publications/unimarc-formats-and-related-documentation/</a></p>
<p><a href="#ftnt_ref12" id="ftnt12">[12]</a> <a href="https://format.gbv.de/schema/avram/specification">https://format.gbv.de/schema/avram/specification</a></p>
<p><a href="#ftnt_ref13" id="ftnt13">[13]</a> <a href="http://www.sudoc.abes.fr/cbs/">http://www.sudoc.abes.fr/cbs/</a></p>
<p><a href="#ftnt_ref14" id="ftnt14">[14]</a> Z39.50 provides a limited download options. We should contact them directly.</p>
<p><a href="#ftnt_ref15" id="ftnt15">[15]</a> The datasets are downloadable from the pef.bnf.fr FTP server in UNIMARC and INTERMARC format (which is the internal metadata schema of Biblioth&egrave;que nationale de France.</p>
<p><a href="#ftnt_ref16" id="ftnt16">[16]</a> <a href="https://www.archivesportaleurope.net/">https://www.archivesportaleurope.net/</a></p>
<p><a href="#ftnt_ref17" id="ftnt17">[17]</a> <a href="https://www.archives.gov/">https://www.archives.gov/</a></p>
<p><a href="#ftnt_ref18" id="ftnt18">[18]</a> <a href="https://www.ifla.org/references/best-practice-for-national-bibliographic-agencies-in-a-digital-age/resource-description-and-standards/bibliographic-control/international-standard-bibliographic-description-isbd/">https://www.ifla.org/references/best-practice-for-national-bibliographic-agencies-in-a-digital-age/resource-description-and-standards/bibliographic-control/international-standard-bibliographic-description-isbd/</a></p>
<p><a href="#ftnt_ref19" id="ftnt19">[19]</a> <a href="http://wikicite.org/">http://wikicite.org/</a></p>
<p><a href="#ftnt_ref20" id="ftnt20">[20]</a> <a href="https://www.wikidata.org/wiki/Wikidata:Main_Page">https://www.wikidata.org/wiki/Wikidata:Main_Page</a></p>
<p><a href="#ftnt_ref21" id="ftnt21">[21]</a> <a href="https://www.wikidata.org/wiki/Property:P304">https://www.wikidata.org/wiki/Property:P304</a></p>
<p><a href="#ftnt_ref22" id="ftnt22">[22]</a> <a href="https://www.wikidata.org/wiki/Q40154916">https://www.wikidata.org/wiki/Q40154916</a></p>
<p><a href="#ftnt_ref23" id="ftnt23">[23]</a> <a href="https://www.wikidata.org/wiki/Q21820630">https://www.wikidata.org/wiki/Q21820630</a></p>
<p><a href="#ftnt_ref24" id="ftnt24">[24]</a> <a href="https://www.wikidata.org/wiki/Q39877401">https://www.wikidata.org/wiki/Q39877401</a></p>
<p><a href="#ftnt_ref25" id="ftnt25">[25]</a> <a href="https://www.wikidata.org/wiki/Q28710224">https://www.wikidata.org/wiki/Q28710224</a></p>
<p><a href="#ftnt_ref26" id="ftnt26">[26]</a> <a href="https://www.wikidata.org/wiki/Q28710226">https://www.wikidata.org/wiki/Q28710226</a></p>
<p><a href="#ftnt_ref27" id="ftnt27">[27]</a> <a href="http://wikicite.org/">http://wikicite.org/</a></p>
<p><a href="#ftnt_ref28" id="ftnt28">[28]</a> <a href="https://academictorrents.com/browse.php?search%3DCrossref">https://academictorrents.com/browse.php?search=Crossref</a></p>
<p><a href="#ftnt_ref29" id="ftnt29">[29]</a> <a href="https://opencitations.net/corpus">https://opencitations.net/corpus</a></p>
<p><a href="#ftnt_ref30" id="ftnt30">[30]</a> <a href="http://www.lido-schema.org/">http://www.lido-schema.org/</a></p>
<p><a href="#ftnt_ref31" id="ftnt31">[31]</a> <a href="https://tei-c.org/">https://tei-c.org/</a></p>
<p><a href="#ftnt_ref32" id="ftnt32">[32]</a> <a href="http://portal.unesco.org/culture/en/ev.php-URL_ID%3D7810%26URL_DO%3DDO_TOPIC%26URL_SECTION%3D201.html">http://portal.unesco.org/culture/en/ev.php-URL_ID=7810&amp;URL_DO=DO_TOPIC&amp;URL_SECTION=201.html</a></p>
<p><a href="#ftnt_ref33" id="ftnt33">[33]</a> <a href="http://demeter.oszk.hu">http://demeter.oszk.hu</a></p>
<p><a href="#ftnt_ref34" id="ftnt34">[34]</a> <a href="https://www.geonames.org/">https://www.geonames.org/</a></p>
<p><a href="#ftnt_ref35" id="ftnt35">[35]</a> <a href="https://viaf.org/">https://viaf.org/</a></p>
<p><a href="#ftnt_ref36" id="ftnt36">[36]</a> <a href="https://thesaurus.cerl.org/">https://thesaurus.cerl.org/</a></p>
<p><a href="#ftnt_ref37" id="ftnt37">[37]</a> <a href="https://www.share-vde.org/">https://www.share-vde.org/</a></p>
<p><a href="#ftnt_ref38" id="ftnt38">[38]</a> <a href="https://www.dariah.eu/activities/working-groups/bibliographical-data-bibliodata/">https://www.dariah.eu/activities/working-groups/bibliographical-data-bibliodata/</a></p>
</div>
