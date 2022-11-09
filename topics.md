---
title: GWDG Cultural Analytics Team research topics
layout: post
---

<style>
ol, ul {
  margin: 0 0 0 25px;
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

.blue{color:#4a86e8}

.post-content ul { list-style-type:none }
.post-content ul > li:before {content:"\002605  "; color: #4a86e8}
.post-content li:before {margin-left:-25pt; white-space:nowrap; display:inline-block; min-width:25pt}

</style>

# <span class="blue">GWDG Cultural Analytics Team</span><br/>research topics

last updated: 2022-11-04

<ul>
  <li><a href="#h.dbhfcpj8muh">I. Metadata Quality Assessment</a>
    <ul>
      <li><a href="#I.1">I.1 SHACL4MARC&ndash;Validating MARC records against locally defined ruleset</a></li>
      <li><a href="#I.2">I.2 UNIMARC</a></li>
      <li><a href="#I.3">I.3 PICA and PICA+</a></li>
      <li><a href="#I.4">I.4 Encoded Archival Description (EAD) and Encoded Archival Context (EAC)</a></li>
      <li><a href="#I.5">I.5 International Standard Bibliographic Description (ISBD)</a></li>
      <li><a href="#I.6">I.6 Anglo-American Cataloguing Rules (AACR2)</a></li>
      <li><a href="#I.7">I.7 MAQUIS&ndash;The quality of the terms in the metadata records and of the Knowledge Organising Systems</a></li>
      <li><a href="#I.8">I.8 Citation data</a></li>
      <li><a href="#I.9">I.9 MARC authority records</a></li>
      <li><a href="#I.10">I.10 Agile Qualitätssicherung von Metadaten zu kulturellen Objekten im Kontext von Datenintegrationsprozessen</a></li>
    </ul>
  </li>
  <li><a href="#II">II. Cultural analytics / Bibliographic data science</a>
    <ul>
      <li><a href="#II.1">II.1 Kinder- und Jugendbücher international. Eine Metadatenanalyse</a></li>
      <li><a href="#II.2">II.2 Patterns of translations of national literatures</a></li>
      <li><a href="#II.3">II.3 Patterns of publications</a></li>
    </ul>
  </li>
</ul>

Cultural Analytics Team is a research team inside the eScience Working Group (AG E) of the Gesellschaft für wissenschaftliche Datenverarbeitung mbH Göttingen ([GWDG](https://www.gwdg.de/)), the computation centre and IT research institute of the [University of Göttingen](https://uni-goettingen.de/) and [Max Planck Society](https://www.mpg.de/en). The purpose of the team is to find ways to apply data analytics solutions in cultural heritage domains in collaboration with other players in Göttingen, Germany and abroad. The team is in a formation state.

This list declares the active and intended research topics of the team. There are two main branches: cultural heritage metadata quality assessment and cultural analytics with special focus on bibliographic data science. Each branch contains a number of individual, independent research, however altogether they form an interrelated network. Each research topic has two sides: an applied computer science one and a humanities one. The first are usually about software development questions and tasks, such as creating algorithms for interpreting data written in a metadata schema, or optimising the running of the software by time or memory consumption. The second side has content related questions, and requires humanistic research methods. Metadata quality assessment might be more appealing for students of Library and Information Science, of book studies (Buchwissenschaft, bibliology), of archival studies, while the cultural analytics topics might be interesting for a wider branch of Digital Humanities students. The research in both topics should be resulted in some written output (paper or thesis), the quality assessment topics optionally outputs software code as well.

We are constantly looking for student helpers, research assistants and collaborating partners in these researches so if the reader feels that a topic is interesting for her/him, do not hesitate to contact us via peter.kiraly@gwdg.de.

## <a id="I"/><span class="blue">I.</span> Metadata Quality Assessment

All of these topics are connected to <em>Metadata Quality Assessment Framework API</em> ([MQAF API](https://github.com/pkiraly/metadata-qa-api)) and [QA catalogue](https://github.com/pkiraly/metadata-qa-marc) open source research software. The topics are extensions of previous research and these software packages. Our final purpose is to provide quality assessment solutions to the metadata records created with all the standard schemas used in cultural heritage institutions (libraries, archives and museums).

Metadata is a type of record, which describes the important features of an object stored in such organisation (such as a book, a letter of an 18th century scholar or a sculpture. Here the “data” is the original object, and since metadata literally means “data about data” includes the creator, title, identifier, location, material, size and other important features of the object. Metadata schema is a special document which describes the structure and rules of the records in a metadata collection, so it tells how to encode this information. Sometimes the schema has a machine readable version (serialised as an XML or JSON schema), sometimes it doesn’t have. Usually the schema does not contain all the information quality assessment requires, so we have to extend it with other information, for example which data elements or rules are more important than others in a particular context, what extra requirements are applicable in a particular organisation (e.g. an identifier might be a simple string or number, and in some context it is claimed to better if it forms a URL, and even better if the URL is persistent).

The MQAF API is a general metadata assessment tool, which requires a derivative of the metadata schema with specific properties for the quality assessment task. Based on this one can build a tool to analyse records in a particular schema simply by configuration. We already have some implementation for this kind of development for Deutsche Digitale Bibliothek, for Victoria and Albert Museum, and meemoo, the Flemish Institute for Archives.

QA catalogue (an extension of MQAF API) is specified for library catalogues and works with records in a metadata schema called [MARC](https://www.loc.gov/marc/) (MAchine Readable Cataloging), and already used by the British Library, KBR, the Royal Library of Belgium, and Gent University Library. Its future extensions should cover MARC variants and non-MARC bibliographic metadata schema such as PICA (and variants), and UNIMARC.

It is equally important for all metadata assessment tools, that they provide input for metadata experts, who decide which reported problems are really relevant for their institute and in which priority.

Abbreviations:

* CS &ndash; Computer Science
* LIS &ndash; Library and Information Science
* DH &ndash; Digital Humanities
* BL &ndash; British Library
* KBR &ndash; Royal Library of Belgium

### <a id="I.1"><span class="blue">I.1</span> SHACL4MARC&ndash;Validating MARC records against locally defined ruleset

<em>Introduction</em>. Shapes Constraint Language ([SHACL](https://www.w3.org/TR/shacl/)) is a formal language for validating Resource Description Framework ([RDF](https://www.w3.org/RDF/)) graphs against a set of conditions (expressed also in RDF). Following this idea, and implementing a subset of the language, <em>MQAF API</em> provides a mechanism to define SHACL-like rules for data sources in non-RDF based formats, such as XML, CSV and JSON (SHACL validates only RDF graphs). The rules can be defined either with YAML or JSON configuration files or with Java code.<sup>a</sup> <em>MQAF API</em> has already been validated in different organisations (Flemish Audio-Visual Archives, Victoria and Albert Museum, Deutsche Digitale Bibliothek). In this research we extend this ruleset to be applicable to MARC records. For making it available for MARC records there are two criteria:

* supporting a particular &quot;addressing scheme&quot; which fits MARC records. This scheme is similar to XPATH or JSONPath which are mechanisms to precisely select a part of an XML and JSON document. For MARC there is a proposal, Carsten Klee&#39;s [MARCspec](http://marcspec.github.io/MARCspec/marc-spec.html) - a common MARC record path language, which is already supported by the QA catalogue.
* implementing a particular interface of MQAF API, which could return a unified value object when we specify it with an address of a data element.

In this research we have two control data sets. BL provided a sample with examples where particular problems have been catched by an alternative tool, but not by QA catalogue. KBR developed an XSLT based solution to check local rulesets. We can use both to compare those results with ours.

During the research students will learn about the following technologies: MARC, SHACL, XPath, JSONPath, MARCspec.

Research questions and tasks (Computer Science):

* Finish the implementation of MARCspec in QA catalogue
* Create a selector class which could find and retrieve the part of the record which is addressed by the MARCspec expression (other implementation of the interface are already available for Xpath, JSONPath and SQL column name expressions)
* Adapt MQAF API that it should accept this selector implementation as input parameter (right now the implementations are hard coded)
* Create a command line interface in QA catalogue which accepts a configuration file describing SHACL-like ruleset

Research questions (Humanities):

* Can the content specific cataloguing rules provided by BL and KBR be transformed to SHACL-like machine readable rules? Are there limitations, and if yes: describe their nature? What suggestions this research might have to the SHACL community and to the further development of QA catalogue?
* Comparing the results of KBR and QA catalogue approaches, what suggestions this research might have to both parties?

Partners:

* British Library
* KBR

Data sources:

* Catalogue of British Library
* Catalogue of KBR

<sup>a</sup> &bdquo;Validating JSON, XML and CSV data with SHACL-like constraint” slides of presentation held at DINI-KIM 2022, [qa-dini-kim-2022](https://bit.ly/qa-dini-kim-2022)

### <a id="I.2"/><span class="blue">I.2</span> UNIMARC

The [UNIMARC](https://www.ifla.org/publications/unimarc-formats-and-related-documentation/) bibliographic format was first created and proposed by IFLA in 1977, with the title <em>UNIMARC: Universal MARC format</em>. The intention of the standard was to unify different MARC versions into a single schema (note: MARC21 had the same intention). It was updated several times, the current version is the 3rd edition. As for MARC21 there are bibliographic, authorities, classification and holdings sub-schemas. UNIMARC records are serialised in ISO 2709 (which is the basis of all MARC versions), and XML. It is in use in France, Italy, Portugal, Slovenia, Slovakia, Ukraina, Belarus, Russia. There is no machine readable version of the schema.

Research questions and tasks (Computer Science):

* Write scripts which downloads UNIMARC records from the data sources via OAI-PMH and Z39.50 protocols. The scripts should handle the shortcomings of these protocols and the actual implementations.
* Create a machine readable UNIMARC schema, either as a set of Java classes according to the QA catalogue&#39;s MARC definition structure or to the JSON based [Avram schema](https://format.gbv.de/schema/avram/specification). It is also possible to implement it with other technology which can be exported into Avram schema.
* Modify QA catalogue backend to be able to use the above mentioned definition as an input configuration for the quality assessment processes.
* Adopt the user interface of QA catalogue to work with the output of the analysis

Research questions and tasks (Humanities):

* How has the UNIMARC schema changed historically, and how to match the proper schema with the records?
* Are there locally defined data elements in particular libraries? Are these documented? How could they be transformed as an input to QA catalogue, so it should understand them and apply the rules during the analyses?
* Literature scan: are there specific papers regarding UNIMARC quality assessment? Are the specific aspects of the structure or the content of the schema which are not available in MARC21 schema?
* Communicate with the data source and collect feedback. How could they use the report in daily work? Are there relevant needs which the result doesn’t fulfil? What are their data life cycles and relevant workflow, and how QA catalogue could be inserted into it?

Potential partners:

* Agence bibliographique de l&#39;emseignement supérieur ([ABES](http://abes.fr)), Montpellier, France, the maintainer of [SUDOC](http://www.sudoc.abes.fr/cbs/), the French union catalogue of academic libraries
* Institut informacijskih znanosti (IZUM), Maribor, Slovenia, the maintainer of COBISS+, the Slovenian union catalogue
* Portugal National Library
* Italian National Library, Firenze

Data sources:

* SUDOC (from ABES)
* Portugal National Library
* COBISS+, the virtual library of Slovenia, one-stop access to information from 919 Slovenian libraries
* Italian National Library, Firenze<sup>a</sup>
* The catalogue of the Bibliothèque nationale de France<sup>b</sup>

<sup>a</sup> The data is available via Z39.50, but with limited download options

<sup>b</sup> The datasets are downloadable from the pef.bnf.fr FTP server in UNIMARC and INTERMARC format, which is the internal metadata schema of Bibliothèque nationale de France.

### <a id="I.3"/><span class="blue">I.3</span> PICA and PICA+

PICA and PICA+ are metadata schemas for describing bibliographic resources, mainly used in Dutch and German libraries (instead of MARC). These schemas contain a fixed set of data elements, but libraries can define their own extra elements. Jakob Voß maintains an Avram schema for PICA+. There is some initial code in the QA catalogue which reads Avram schema and uses it as an input for model building against which the analyses can be run.

Research questions and tasks (Computer Science):

* Finalise Avram schema reader 
* Finalise a record reader which takes an Avram schema, parse records which are in the schema describe by the Avram schema (in this case PICA), and creates Java objects for each record
* Modify QA catalogue that it could validate the objects created the above mentioned mechanism, and produce the same output as it creates for MARC records

Research questions and tasks (Humanities):

* How has the PICA/PICA+ schema changed historically, and how to match the proper schema with the records?
* Are there locally defined data elements in particular libraries? Are these documented? How could they be transformed as an input to QA catalogue, so it should understand them and apply the rules during the analyses?
* Literature scan: are there specific papers regarding PICA/PICA+ quality assessment? Are there specific aspects of the structure or the content of the schema which are not available in MARC21 schema?
* Communicate with the data source and collect feedback. How could they use the report in daily work? Are there relevant needs which the result doesn’t fulfil? What are their data life cycles and relevant workflow, and how QA catalogue could be inserted into it?

Partner:

* Gemeinsamer Bibliotheksverbund (GBV), Göttingen

Data sources:

* K10Plus union catalogue, 60+ million records (maintained by GBV)

### <a id="I.4"><span class="blue">I.4</span> Encoded Archival Description (EAD) and Encoded Archival Context (EAC)

Encoded Archival Description is an XML schema to describe archival records, Encoded Archival Context is for describing the authorised form of named entities (persons, families, corporate bodies) that appeared in the archival records (similar to the authority records of a library catalogue). The challenging part of EAD is the hierarchical nature. Archival records form a large, multi-level hierarchy, where each level describes smaller parts of the collection up to single documents. However these levels do not always have the same nature. There are standard names for some distinct levels, but not all collections have the same number of levels and the same structure. It depends on lots of factors, such as the practice of the institution the collection comes from, the importance of the documents etc. On the other hand the number of data elements describing the properties of the levels is much less than that of the MARC schemas. The largest open access collection of these records are the [Archives Portal Europe](https://www.archivesportaleurope.net) and [National Archives and Records](https://www.archives.gov/). Both provide APIs we can use in this research.

Research questions and tasks (Computer Science):

* Create MQAF API compliant schemas from EAD/EAC XML schema. Take care of the hierarchical nature of the structure.
* Create a user interface which fits to the specific features of EAD/EAC records. Take care of the hierarchical nature of the structure.

Research questions and tasks (Humanities):

* Literature review on the analyses of EAD/EAC records, focusing on the data quality aspects
* Survey archivist and researchers who work with archival metadata about the metadata quality aspects. Based on the findings define a set of requirements against EAD/EAC records.
* Test the implementation, and create an evidence-based report on the quality related issues found in a concrete archival collection.
* Communicate the findings with the institution and get feedback about them. Did they know about the issues? How do they solve quality issues? Does the report “overlook” some issues they know?

Partners:

* Archives Portal Europe (The Hague)
* National Archives and Records (Washington DC)

Data sources:

* Archival Portal Europe
* National Archives and Records (Washington DC)

### <a id="I.5"/><span class="blue">I.5</span> International Standard Bibliographic Description (ISBD)

International Standard Bibliographic Description ([ISBD](https://www.ifla.org/references/best-practice-for-national-bibliographic-agencies-in-a-digital-age/resource-description-and-standards/bibliographic-control/international-standard-bibliographic-description-isbd/)) contains a set of rules about the content of data elements in library catalogue records to offer consistency when sharing bibliographic information. It is mostly used in European libraries (Anglo-Saxon libraries are using a similar set of rules, Anglo-American Cataloguing Rules). It mainly focuses on descriptive metadata. National cataloguing rules are usually derived from the ISBDs, but with a number of significant differences in distinct libraries. ISBD also provides a human readable, language independent representation of the records (by setting the (in)famous “punctuation rules” where dots, colons, slashes have context-dependent semantic meaning).

ISBD could be used within MARC records. The record should contain information about if ISBD has been applied or not. The MARC21 standard itself does not document ISBD rules, so in order to validate MARC, an extra ISBD validation layer is necessary. IFLA&#39;s ISBD web page says that &quot;The ISBD review group also maintains an ISBD RDF/XML schema, to enable libraries to publish their metadata as linked data&quot; - however at time of writing this document I haven’t found it. This schema may or may not provide a starting point to this research.

Research questions and tasks (Computer Science):

* Find and investigate the above mentioned RDF/XML schema
* Investigate the ISBD documentation
* Create a machine readable, MQAD API compliant ruleset from the ISBD rules (either as Java code or a YAML/JSON configuration file)
* Run analyses in QA catalogue

Research questions and tasks (Humanities):

* Literature review on ISBD, focusing on the data quality aspects
* Survey library metadata experts and researchers who work with ISBD based records about the metadata quality aspects. Based on the findings, define a set of requirements against ISBD data elements as a textual document or with SHACL expressions. 
* Test the implementation, and create an evidence-based report on the quality related issues found in particular catalogues.

Partners:

* British Library
* any other library who applies ISBD in their catalogue

Data sources:

* British Library catalogue

### <a id="I.6"/><span class="blue">I.6</span> Anglo-American Cataloguing Rules (AACR2)

AACR2 contains a set of rules about the content of data elements in the catalogue records used in English and US libraries.

AACR2 could be used within MARC records. The record should contain information about if AACR2 has been applied or not. The MARC21 standard itself does not document AACR2 rules, so in order to validate MARC, an extra AACR2 validation layer is necessary. It is not clear if there is a machine readable representation of the AACR2 ruleset.

Research questions and tasks (Computer Science):

* Investigate if there is a machine readable (RDF/XML schema) representation of the AACR2
* Investigate the AACR2 documentation
* Create a machine readable, MQAD API compliant ruleset from the AACR2 rules (either as Java code or a YAML/JSON configuration file)
* Run analyses in QA catalogue

Research questions and tasks (Humanities):

* Literature review on AACR2, focusing on the data quality aspects
* Survey library metadata experts and researchers who work with AACR2 based records about the metadata quality aspects. Based on the findings, define a set of requirements against AACR2 data elements as a textual document or with SHACL expressions.
* Test the implementation, and create an evidence-based report on the quality related issues found in particular catalogues.

Data sources:

* Library of Congress catalogue

### <a id="I.7"/><span class="blue">I.7</span> MAQUIS&ndash;The quality of the terms in the metadata records and of the Knowledge Organising Systems

Previous research almost exclusively focused on the quality of Knowledge Organising Systems, and most of them did not release open source tools to help institutions to measure their own data. This research aims to evaluate existing metrics, to propose new metrics and methods and to develop implementation for both aspects. The research will intensively use large library catalogues (such as EconBiz, SUDOC and Gemeinsamer Verbundkatalog, B3Kat and others) and the KOSes linked to them, however both the proposed theoretical model and the software package should be applicable to other bibliographical catalogues.

Additionally, the metadata records and the KOS together form three networks:

* a record-subject network (records have subjects)
* a subject co-occurrence network,
* and the network of records which are connected by subjects and other kinds of authority entries (e.g. persons, organisations, events etc.).

We will measure the standard properties of these networks (density, components, clusters, connectedness, degree distribution, PageRank, Small-World).

Two types of output are expected:

* scientific publication(s): thesis, scientific paper, conference presentation
* two open source software packages: a standalone tool which measures the quality of bibliographical records and KOS, and a plugin which integrates this tool into the QA catalogue quality assessment software. 

If the results of the research will be promising, and evaluated as usable by the partner institutions, and if there will be an interest in implementation or deployment of the same, we will also investigate the possibility of integration into the existing IT infrastructure of the organisation.

The project follows the principles of repeatable research and of maintainable research software development (part of the research data is open data, code will be properly tested, documented, and citable, communication will be transparent).

Research questions and tasks (Computer Science):

* Analyse the bipartite (record-subject) network. Does the basic properties of the network reveal anything about the quality of subject indexing?
* How subject indexing supports retrieval?
* How the intrinsic quality features of the KOS affects the usage of the records?
* Is there a correlation between the quality of subject indexing and other known quality dimensions?

Research questions and tasks (Humanities):

* Literature review on data quality aspects of subject indexing
* Survey library metadata experts and researchers who work in the subject indexing field about the metadata quality aspects. Based on the findings, define a set of requirements against AACR2 data elements as a textual document or with SHACL expressions.
* Test the implementation, and create an evidence-based report on the quality related issues found in particular catalogues. 

Partners:

* Agence bibliographique de l&#39;emseignement supérieur (ABES), Montpellier
* Gemeinsamer Bibliotheksverbund (GBV), Göttingen
* ZWB &ndash; Leibniz-Informationszentrum Wirtschaft

Data sources:

* EconBiz catalogue of ZWB
* Système Universitaire de Documentation (SUDOC) of ABES
* Gemeinsamer Verbundkatalog (GVK) of GBV and SWB

### <a id="I.8"/><span class="blue">I.8</span> Citation data

Citation data, or bibliographic data of scholarly articles is a neuralgic point for the libraries. In the “Western World” and for large languages, the publishers are those players which traditionally built databases for the scholarly articles (such as Web of Knowledge, Scopus) instead of libraries. By and large there have been exceptions even in Western European countries. In case of smaller languages and for poorer countries the large publishers do not see the market value to publish scientific journals in vernacular languages therefore those journals are not covered in their databases. In the last two decades several different projects have been launched to make these metadata out of “paywalls”. The largest of these projects is the DOI database, but the larger part of DOI metadata is also not freely available, however the Initiative for Open Citations 16 works on making the citation data open. Recently [WikiCite](http://wikicite.org/) is the largest freely available citation database based on the bibliographic data imported into [Wikidata](https://www.wikidata.org/wiki/Wikidata:Main_Page). It provides a query interface and [database dumps](http://wikicite.org/access.html). Together with Jakob Voß, a volunteer of WikiCite and Wikidata we started a research project 20 to analyse the data. This research is in a preliminary stage. Now I highlight only one feature of the citation data namely page numbers, which seems to be simple, but reveals some complex problems. One can expect that page numbers are arabic or roman numbers separated by dashes and commas (sometimes with some text before or after the numbers). I found several hundred patterns, which do not fit this expectation. Here I show three issues with “strange” page numbers. Wikidata uses a language neutral notation for describing its semantic structure, the entities are denoted by &lsquo;Q’ and a number, while properties are denoted by &lsquo;P’ and a number. For example: [P304](https://www.wikidata.org/wiki/Property:P304) is the property of the page numbers. Its human readable label in English is “page(s)”.

Some known problems with the page number properties:

#### 1. Using article identifier as page number

[Q40154916](https://www.wikidata.org/wiki/Q40154916): “e0179574” -- This article was published in PLoS ONE. The publisher provides citation text, and metadata in RIS and BibTeX format. The citation contains &lsquo;e0179574’, however it does not explain what exactly it means (as it neither explains any other elements). e0179574 is an article identifier.

[Q21820630](https://www.wikidata.org/wiki/Q21820630): “c181” -- This paper was published in the British Medical Journal. It does not have a PDF version, the only available online version is HTML which does not have page numbers at all. c181 is an article identifier.

In both examples even the publisher exports bad data claiming article numbers as page number metadata.

#### 2. Wikidata contains extra info, which is not available elsewhere

[Q39877401](https://www.wikidata.org/wiki/Q39877401): ”108-17; quiz 118-9” -- &quot;quiz 118-9&quot; does not appear anywhere in the publisher or DOI metadata. Wikidata does not have a note about the source of this piece.

#### 3. Wikidata uses page number field to add comment

[Q28710224](https://www.wikidata.org/wiki/Q28710224): ”E3523; author reply E3524&ndash;5” -- E3524&ndash;5 is not part of the article. It is a related article, which is also available in Wikidata (as [Q28710226](https://www.wikidata.org/wiki/Q28710226)). These two articles are not interlinked with distinct properties. One could suppose that the occurrence &lsquo;author reply’ in other Wikidata records’ page number could reveal similar hidden links.

Some analyses are available in this repository: [metadata-qa-wikidata](https://github.com/pkiraly/metadata-qa-wikidata/).

Research questions and tasks (Computer Science):

* What are the basic quality dimensions applicable to citation data?
* How does quality of citation data affect scientometrics?
* If there is a correlation, is there a known method from scientometrics’ side to minimize it?

Research questions and tasks (Humanities):

* Literature review on data quality aspects of citation data
* Survey library metadata experts and researchers who work with citation records about the metadata quality aspects. Based on the findings, define a set of requirements against citation data elements as a textual document or with SHACL expressions.
* Test the implementation, and create an evidence-based report on the quality related issues found in particular catalogues.
* How can we fix derivative data (e.g. a citation found in Wikidata or other open access repository) in a way that the fix would be applicable to the source data (the publisher!s side)? Would it be a different approach for commercial and not-for-profit publishers?

Data sources:

* [WikiCite](http://wikicite.org/)
* Crossref [data dumps](https://academictorrents.com/browse.php?search%3DCrossref)
* Open Citations [corpus](https://opencitations.net/corpus)

### <a id="I.9"/><span class="blue">I.9</span> MARC authority records

The QA catalogue analyses MARC21 <em>bibliographic</em> records. MARC21 and UNIMARC also have a distinct schema for authority records. They describe contextual information: subject or name vocabularies which contain standardised form of names for people, corporate bodies, meetings, titles, and subjects referred in the bibliographical records. On the authority record the standardised form is the key element for which the record was made, so it is also called the heading. These records provide authority control, i.e. establishing a recognized form for an entity name and using that form whenever the name is needed as an access point in a bibliographic record. The record has three main components: headings, cross references, and notes. The authority schema is similar in structure to that of the bibliographic schema, but it contains much less data elements.

A short introduction: [loc.gov](https://www.loc.gov/marc/uma/pt1-7.html).

Research questions and tasks (Computer Science):

* How to transform MARC21 authority schema into Java classes the same way as bibliographic record schema elements are implemented in QA catalogue?
* How to create a mechanism where the user can tell QA catalogue to analyse authority records instead of bibliographic records?
* How to report the results? What would be the ideal user interface? 

Research questions and tasks (Humanities):

* Literature review on data quality aspects of authority data
* Survey library metadata experts and researchers who work with authority records about the metadata quality aspects. Based on the findings, define a set of requirements against authority data elements as a textual document or with SHACL expressions.
* Test the implementation, and create an evidence-based report on the quality related issues found in particular catalogues.

Partners:

* KBR

Data sources:

* authority records of KBR catalogue
* authority records Library of Congress catalogue

### <a id="I.10"/><span class="blue">I.10</span> Agile Qualitätssicherung von Metadaten zu kulturellen Objekten im Kontext von Datenintegrationsprozessen

The aim of this project is to invent semi-automatic mechanisms which translate quality criteria against metadata expressed in natural language into a machine actionable form which could be used as an input in a quality assessment process.

Administrative status: submitted proposal.

Research questions and tasks (Computer Science):

* Given a complex, hierarchical metadata schema in XML format. How to implement the following user scenario: the user - with limited technical knowledge (typically a metadata creator or integrator) - enters a human readable input, such as “title” or “genre” in a graphical interface, and the application returns XPath expression(s) which can be generated based on the metadata schema’s structure and the input? The user should be able to test the expression instantly on test records. The user should be able to modify the input, or the XPath expression.
* How to extend this application to work with other serialization formats and query languages?
* How to embed the resulted expression into conditional statements, such as “find records where title is missing” or “find records where birth date is larger than death date”?
* How to transform these statements into SHACL-like expressions?

Research questions and tasks (Humanities):

* What are the common metadata quality problems in Lightweight Information Describing Objects ([LIDO](http://www.lido-schema.org/)) records?
* What are the common metadata quality problems in [TEI](https://tei-c.org/) records?

Partners:

* SUB
* Fachbereich Mathematik und Informatik, Philipps-Universität Marburg
* Deutsche Digitale Bibliothek

## <a id="II"/><span class="blue">II.</span> Cultural analytics / Bibliographic data science

These topics utilise catalogue as source data or evidence which could be used to answer Humanities research questions. The bibliographic data contains some generally available factual dimensions, such as personal names of authors and contributors (occasionally with additional properties), the place and date of publication, the name of publisher/printer/scriptor, genre, the subject description of the content (keywords, classification terms), the physical properties of the document, occasionally provenance (current and previous holding institutions, owners). After (more or less) data cleaning all these draw some historical patterns, such as how the roles of different languages changed, how the literary canon evolved, who were the important authors and books in a particular periods, which were enduring and ephemeral successes, how the media changed, and how all these correlated with each other?

Some important publications, which could be used as examples of such researches:

* Andrew Prescott. (2013). “Bibliographic Records as Humanities Big Data.” In 2013 IEEE International Conference on Big Data, 55&ndash;58, 2013. [10.1109/BigData.2013.6691670](https://doi.org/10.1109/BigData.2013.6691670)
* Michael F. Suarez. (2009). “Towards a bibliometric analysis of the surviving record, 1701&ndash;1800.” in The Cambridge History of the Book in Britain, Volume 5: 1695&ndash;1830, Cambridge University Press, 2009. pp. 37-65. [10.1017/CHOL9780521810173.003](https://doi.org/10.1017/CHOL9780521810173.003)
* Sandra Tuppen, Stephen Rose, and Loukia Drosopoulou (2016). “Library Catalogue Records as a Research Resource: Introducing &lsquo;A Big Data History of Music.’” Fontes Artis Musicae 63, no. 2:67&ndash;88. [10.1353/fam.2016.0011](https://doi.org/10.1353/fam.2016.0011)
* Tolonen, M., Mäkelä, E., Marjanen, J., Kanner, A., Lahti, L., Ginter, F., Salmi, H., Vesanto, A., Nivala, A., Rantala, H., &amp; Sippola, R. (2018). Metadata analysis and text reuse detection: Reassessing public discourse in Finland through newspapers and journals 1771&ndash;1917. Paper presented at digital humanities in the Nordic countries DHN2018, Helsinki, Finland. [researchportal.helsinki.fi](https://researchportal.helsinki.fi/en/publications/metadata-analysis-and-text-reuse-detection-reassessing-public-dis)
* Lahti, L., Marjanen, J., Roivainen, H., &amp; Tolonen, M. (2019). Bibliographic data science and the history of the book (c. 1500&ndash;1800). Cataloging &amp; Classification Quarterly, 57(1), 5&ndash;23. [10.1080/01639374.2018.1543747](https://doi.org/10.1080/01639374.2018.1543747)
* Marjanen, J., Kurunmäki, J. A., Pivovarova, L., &amp; Zosa, E. (2020). The expansion of isms, 1820&ndash;1917: Data-driven analysis of political language in digitized newspaper collections. Journal of Data Mining and Digital Humanities, HistoInformatics, 1&ndash;28. [https://jdmdh.episciences.org/6728](https://jdmdh.episciences.org/6728)
* Mikko Tolonen, Mark J. Hill, Ali Ijaz, Ville Vaara, Leo Lahti. (2021). Examining the Early Modern Canon : The English Short Title Catalogue and Large-Scale Patterns of Cultural Production. In Ileana Baird (eds.) Data Visualization in Enlightenment Literature and Culture. Cham : Palgrave Macmillan, 2021. pp. 63-119 [10.1007/978-3-030-54913-8_3](https://doi.org/10.1007/978-3-030-54913-8_3)
* Simon Burrows. (2021). In Search of Enlightenment: From Mapping Books to Cultural History. In: Baird, I. (eds) Data Visualization in Enlightenment Literature and Culture . Palgrave Macmillan, Cham. [10.1007/978-3-030-54913-8_2](https://doi.org/10.1007/978-3-030-54913-8_2)

### <a id="II.1"/><span class="blue">II.1</span> Kinder- und Jugendbücher international. Eine Metadatenanalyse

Kinder- und Jugendliteratur (KJL) galt schon Paul Hazard (1952) als die erste Weltliteratur und seine Einschätzung trifft heute mehr denn je zu. Denn Kinder- und Jugendliteratur ist wesentlich vom internationalen Lizenzgeschäft bestimmt, übersetzungen und Adaptionen von Illustrationen spielen eine prominente Rolle. Spitzentitel wie &bdquo;Harry Potter“ bestimmen den Buchmarkt und das Lesen wie keine andere Sachgruppe. Am drittgrößten, dem deutschsprachigen Publikumsbuchmarkt hat die KJL einen Marktanteil von etwa einem Drittel, auf dem chinesischen Publikumsbuchmarkt soll die KJL sogar die größte Sachgruppe bilden. Kaum eine andere Gruppe gewährt daher einen so genauen Einblick in die Internationalisierung und Globalisierung der Kultur wie eben die KJL.

Eine Arbeitsgruppe der Mainzer Buchwissenschaft erarbeitet aus verschiedenen Daten einen Weltatlas der Literatur. Vorbild ist das Projekt der Oxforder Arbeitsgruppe um Max Roser &bdquo;Our World in Data“. Während &bdquo;Our World in Data“ vor allem aktuelle Daten zur globalen sozialen Welt sammelt, soll unser Projekt Daten zur Kultur sammeln (&bdquo;Our Culture in Data“), zunächst einmal Daten zur Literatur. Doch Daten zur Kultur zu erheben ist schwierig, da mit den Sozialwissenschaften vergleichbare Datenerhebungen nur vereinzelt durchgeführt werden, etwa zu Museumsbesuchen, der Zahl der Klassikfestivals oder dann auch zu der Zahl der verkauften Bücher. Diese Zahlen werden fast ausschließlich national erhoben nach nicht vergleichbaren Parametern. Die Daten über das Leseverhalten in Europa beispielsweise werden so unterschiedlich erhoben, dass eine Aggregation derzeit nicht sinnvoll möglich ist.

Während diese potenziellen Daten zur Kultur noch viel Aufbereitung bedürfen, gibt es eine Quelle für eine datenbasierte Analyse der weltweiten Kultur, die bislang wenig genutzt wurde. Das sind Bibliothekskataloge. Sie wurden oft über Jahrhunderte gepflegt, haben Standards der Datenerfassung entwickelt und ein gemeinsames Verständnis des Verzeichniswerten erarbeitetet. Sie werden vor allem zum Auffinden genutzt, aber nur in wenigen buchwissenschaftlichen Studien auch als Quelle zum Verständnis von Kultur (Zedelmaier, 2016; Duncan 2021). In dieser schmalen Linie kulturwissenschaftlicher Forschung verstehen wir Bibliothekskataloge als institutionell verdichtetes und verstetigtes Wissen über Kultur. Unser Startpunkt ist die Kinder- und Jugendliteratur, die seit dem 19. Jahrhundert als eine eigene Rubrik auch in der DNB bzw. ihren Vorläufern verzeichnet wurde. Umfangreiche Sammlungen und Sonderbestände in verschiedenen Bibliotheken erlauben eine sowohl historische wie systematische Annäherung an das, was als Kinder- und Jugendbuch (vor-)gelesen wurde und wird.

Ziel des Vorhabens ist also am Beispiel der Kinder- und Jugendliteratur zu analysieren, welche Kinder- und Jugendliteratur wo gesammelt wurde und wird, welche Publikationsformen, Gattungen und Genres, für welche Altersgruppen verzeichnet wurden. Unser Interesse gilt also den Metadaten. Wir erhoffen uns eine quantitativ valide Antwort auf die Frage, was für KJL liest die Welt.

Research questions and tasks (Computer Science):

* Find how to extract information about if a particular record belongs to the category of children and youth literature, along with other information of the book (title, authors, publication date, publisher)
* Visualise the extracted information with timeline and map

Research questions and tasks (Humanities):

* How information about if a particular record belongs to the category of children and youth literature is encoded in metadata records
* How has this category changed over the times?
* Are there regional differences in the application of the category?

Partners:

* Prof. Dr. Gerhard Lauer, Dr. Wei Ding &ndash; Buchwissenschaft, Johannes Gutenberg-Universität Mainz
* Deutsche Nationalbibliothek

### <a id="II.2"/><span class="blue">II.2</span> Patterns of translations of national literatures

Some kinds of bibliographical records make it possible to reveal patterns of translations from a particular national literature. Lots of interesting features can be extracted from the data, such as the changing of the target languages (which other literature were interested in the source literature?), of publication places and translators (were the translations been created at home or abroad?), of the volume, of publishers (what was the prestige of the author?). Were there any key languages which helped the literature to enter world literature (for example for a long time German translations of Hungarian works preceded other translations, and sometimes those other translations are created from German, not from Hungarian).

UNESCO maintains a dedicated database (Index Translationum) into which national libraries send records about translated works. This database typically contains information about books, but not in an analytical manner (e.g. without the analyses of the parts of the book, which would be important if it is an anthology with multiple translations) and does not cover publications in periodicals. On the other hand there are some dedicated databases and bibliographies concentrating on particular aspects (like translations from a given language, or of works in a genre, or an author), but with greater details than that of the Index Translationum.

There is a distinct scientific branch called translation studies, which also includes empirical research, however most of them utilise Index Translationum as a single source. The niche of this current research is to try to overcome the above mentioned limitation of this central data source, and shading light to phenomena which could be revealed only from others sources.

Research questions and tasks (Computer Science):
* How to extract relevant information from semi structured data sources?
* How can different types of data be normalised?
* How can this data be enriched with external data sources (e.g. library catalogues)?
* Once the data are normalised, what exploratory data analysis methods can be created to help answering the humanities research questions below?
* Are there any feedback or suggestions for the data providers? Is there an improved dataset which can be given back to the data providers?

Research questions and tasks (Humanities):

* How translations are changing through time, what are the temporal patterns?
* How translations are changing through space, what are the spatial patterns?
* What are the missing information types in a particular data source?
* What are the relevant external data sources for an enrichment process?
* How has the medium (the format of publishing) changed over time?
* What languages have been important over time?
* Are there correlations between the above mentioned factors (time, space, format, language, authors)?
* What would be the optimal communication format based on the findings?

Data sources:

* UNESCO&#39;s [Index Translationum](http://portal.unesco.org/culture/en/ev.php-URL_ID%3D7810%26URL_DO%3DDO_TOPIC%26URL_SECTION%3D201.html)
* national bibliographies
* [Bibliographica Hungarica](http://demeter.oszk.hu)

Partners:

* Prof. András Kiséry, City College of New York

### <a id="II.3"/><span class="blue">II.3</span> Patterns of publications

National bibliographies aim to describe all the books published in a given country (however none of them are complete). This huge set of information is not well exploited from the perspective of cultural history, because they are usually accessible only via a search interface with limited feature set, which doesn’t enable researchers to extract information, and run statistical analyses on them. The side effect of the QA catalogue project is that the tools created there are generic tools, and can be utilised for data extraction. The library catalogue records may or may not contain information in standardised form (see section on MARC Authority records), which may or may not involve data cleaning in the process. At the end we could extract information from the catalogue such as authors and other collaborators, place names including publication place and places which the book is talking about, subjects (in human readable or in encoded form), dates, language of publication, physical dimensions of the publications and several other data elements. In some MARC records some of these entities found in descriptive data elements have authorised formats attached to the same record. These authorised formats however usually do not inform the reader about which data element they belong to. The two forms are different, and maybe differently segmented as well.

Research questions and tasks (Computer Science):

* How could the entities found in the descriptive data elements be paired with the authorised form? Which relevant data elements do not have authorised forms?
* Could this knowledge (non authorised form - authorised form) be reused for a suggesting application in case of records where the normalised part is missing? How other data elements can be used in such an application which provides larger context (related to information on what? who? where? when?).
* How external information sources could be reused (e.g. [Geonames](https://www.geonames.org/), [VIAF](https://viaf.org/), [CERL Thesaurus](https://thesaurus.cerl.org/), [Share-VDE](https://www.share-vde.org/) etc.) to normalise entities?

Research questions and tasks (Humanities):

* How has the importance of cities as publication places changed?
* What was the ratio of vernacular and foreign languages (Latin, German, Russian, English) in different periods?
* How did the connection between the format and the genre change over time?
* What other countries had the most impact (measured by the number of their publications held in the library under scrutiny) in different times?

Partners:

* [DARIAH Bibliographical Data Working Group](https://www.dariah.eu/activities/working-groups/bibliographical-data-bibliodata/)
* libraries


Data source:

* library catalogues
