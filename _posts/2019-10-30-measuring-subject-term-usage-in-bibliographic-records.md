---
title:      Measuring subject term usage in bibliographic records
layout:     post
date:       2019-10-30 00:00:00
author:     "pkiraly"
customjs:
 - http://code.jquery.com/jquery-1.4.2.min.js
 - http://pkiraly.github.io/js/table.js
---

The following text is current research plan. I submitted it to Koninklijke Bibliotheek's (the Dutch National Library) researcher-in-residence programme. Finally the jury selected somebody else for the grant, and now I publish its main text (I removed some administrative staff and contact details). I continue to work on this plan, and will present some preliminary results at <a href="http://swib.org/swib19/programme.html">SWIB 2019</a> (2019-11-27 11:05 - 11:30 if you will attend at the conference).

<!-- more -->

<h2>Bio (max 100 words)</h2>
<p><em>Please provide a short biography of each team member with a maximum of 100 words that provides evidence of your expertise in the field of your proposal.</em></p>
<p>I am a cultural heritage/digital humanities software developer and researcher since 1996. I worked in university libraries, archives, national library, digital libraries, and library vendors. Since 2014 I am a member of Göttingen eResearch Alliance focusing on research data management. I work in different fields: searching, metadata quality measurement, long term archiving, DH. I contribute to open source/data projects e.g. Europeana, Dataverse, Project Gutenberg, eXtensible Catalog, Göttingen Dialog in Digital Humanities, Göttingen Data Science Meetup, and Hungarian Electronic Library. I am an editor of the Code4Lib Journal. In 2019 I defended my doctoral thesis “Measuring Metadata Quality” (summa cum laude).</p>

<h2>Key Publications</h2>
<p><em>Please list your 3 most important publications that are relevant for your proposal. Please feel free to also include publications that are under review or in print.</em></p>
<ul>
	<li>Péter Király. “Measuring metadata quality”. Doctoral thesis. <a href="http://doi.org/10.13140/RG.2.2.33177.77920">http://doi.org/10.13140/RG.2.2.33177.77920</a></li>
	<li>Péter	Király. “Validating 126 million MARC records”. Accepted for DATeCH 2019 proceedings. A modified version is available in the thesis as Chapter 4. (Slides: <a href="http://bit.ly/qa-datech2019">http://bit.ly/qa-datech2019</a>)</li>
	<li>Péter Király and Marco Büchler. “Measuring completeness as metadata quality metric in Europeana.” in 2018 IEEE International Conference on Big Data, IEEE, pp. 2711–2720. <a href="https://doi.org/10.1109/BigData.2018.8622487">https://doi.org/10.1109/BigData.2018.8622487</a>. A modified version is available in the thesis as Chapter 2.</li>
</ul>

<p>List of my publications relevant to metadata quality measurement are available in Appendix C. of my thesis.</p>

<h3>2a. Title of the project</h3>
<p><em>Please provide a short but specific title. Acronyms are allowed but not necessary.</em></p>
<p>Measuring subject term usage in bibliographic records</p>

<h3>2b. Abstract (max 250 words)</h3>
<p><em>Please provide an abstract of your proposed research of maximum 250 words. Please note this abstract will be published on the KB Lab website and the KB website.</em></p>
<p>The purpose of this empirical research is to investigate and measure the application of Knowledge Organisation Systems (KOS) in metadata, and how they contribute to the quality of metadata records. To measure the quality of subject terms (classification), we should consider at least two facets:</p>
<p>1. The quality of the terms in the metadata records</p>
<p>2. The quality of the KOS</p>
<p>Previous research almost exclusively focused on the second facet, moreover most of them did not released open source tools to help institutions to measure their own data. This research will evaluate the existing metrics, propose new metrics and methods and will develop implementation for both facets. The research will intensively use KB’s open datasets (KB’s catalogues and the KOS-es maintained or available in KB), however both the proposed theoretical model and the software package will be applicable to other datasets in the cultural heritage domain.</p>
<p>The output of the research will be a scientific paper for a library and information science journal or conference, and two software packages: a standalone tool which measures the quality of bibliographical records and KOS-es, and a plugin which integrates this tool into my MARC quality assessment software. I will investigate the possibility of integration of the tool into KB’s existing IT infrastructure.</p>
<p>The project will follow the principles of repeatable research and of the maintainable research software development (data will be stored in citable research data repository, code will be properly tested, documented, and citable, communication will be transparent).</p>

<h2>Project	description (max 1.500 words for sections 3a-c)</h2>

<h3>3a. Background and research question</h3>
<p><em>Please give a short introduction on your project, building up to your research question.</em></p>
<p>The question has evolved from a finding in Europeana: there are 7+ million metadata records having “Document” subject term, which is very general concept and since it is applied to too many records it is not distinctive. How can we measure the specificity and distinctive power when a metadata record contains generic terms like that? Together they describe the document more specifically I suppose, but can we set up a measurable scale? Studying literature and discussing with experts <a class="sdfootnoteanc" name="sdfootnote1anc" href="#sdfootnote1sym">[1]</a>, I get to the conclusion that so far there were no studies neither open source tools available focusing both of the following two main facets:</p>
<p>1. the quality of the terms in the metadata records</p>
<ul>
	<li>Are the terms in the metadata record properly formatted?</li>
	<li>Do they represent a clear reference to a KOS?</li>
	<li>Are they specific or rather generic?</li>
	<li>How multiple generic terms do improve the specificity?</li>
</ul>
<p>2. the quality of the connected KOS</p>
<ul>
	<li>What are the expressive power and the functionalities of a KOS?</li>
	<li>What are the intrinsic qualities of KOS?</li>
</ul>
<p>What I would like to achieve is a computational model and its implementation within an existing software package which calculates one or more quality scores of the used KOS-es, of the individual KOS term instances in a bibliographical record, overall score(s) for the whole record, and overall score(s) for the whole catalogue (and for any reasonable subsets of it). Moreover, for all referenced KOS I would like to visualize the usage of them in the catalogue.</p>
<p>Some specific questions this research would like to answer:</p>
<ul>
	<li>Are	KOS terms/expressions valid in bibliographic records?</li>
	<li>Which	parts of the catalogues do use which KOS vocabularies?</li>
	<li>What is the average depth of the used terms in a hierarchical vocabulary?</li>
	<li>Are the term specific or rather generic to describe a resource?</li>
	<li>How many expressions are used per records?</li>
	<li>Are	there any “blank areas” where the records don't have any classification terms?</li>
	<li>What is the distribution of subject facets (thematic, geographic, temporal etc.)?</li>
</ul>
<p>In order to properly address these research questions we should be able to parse complex classification terms (think about Universal Decimal Classification's composition syntax); resolve the machine names such as “QA 10000” in the Regensburger Verbundklassifikation to human understandable labels; and (optionally) open up closed systems (UDC, Dewey etc. are behind the paywall).</p>
<p>In a previous research I’ve created a MARC quality analysis tool [Király, 2019, Király, 2017]. The current research proposal could benefit from this tool. The basics are already available: it extracts what kind of KOS-es are used in MARC records, what are the individual terms, and their frequencies.</p>
<p>We should link the individual terms to the KOS, resolve its label if the term is a symbolic value, and retrieve all the information about KOS vocabularies and their individual entries that need to calculate the above mentioned metrics (and those, which will be defined during the research). To answer these questions external services and different experts should be consulted. Two services are specifically relevant:</p>
<ul>
	<li>The Basel Register of Thesauri, Ontologies &amp; Classifications (BARTOC) <a class="sdfootnoteanc" name="sdfootnote2anc" href="#sdfootnote2sym">[2]</a></li>
	<li>coli-conc. Infrastructure to facilitate management and exchange of concordances between library knowledge organization systems <a class="sdfootnoteanc" name="sdfootnote3anc" href="#sdfootnote3sym">[3]</a></li>
</ul>
<p>Dutch National Bibliography and Brinkman thesaurus (alongside with German National Library’s database (DNB) and Dewey Decimal Classification (DDC)) could be good first use cases to start with. Other candidates are the Common Union Catalogue of two German library networks <a class="sdfootnoteanc" name="sdfootnote4anc" href="#sdfootnote4sym">[4]</a> and the catalogues which have been analysed in [Király, 2019]. The three most frequently used subject vocabularies in DNB are Dewey Decimal Classification, Systematik der Deutschen Nationalbibliographie, Subject Classes of the Schlagwortnormdatei. From these DDC is the one for which coli-conc recently provides APIs which let us to iterate over the full graph, and calculate the semantic specificity score as suggested in [Inácio et al., 2017].</p>
<p>Brinkman thesaurus has a Linked Data interface, which returns semantic formats. coli-conc works on a KOS assessment <a class="sdfootnoteanc" name="sdfootnote5anc" href="#sdfootnote5sym">[5]</a> tool based on [Stock, 2015], [Gangemi et al., 2005] and [Owens–Cochrane, 2004], so we could exchange our complementary results.</p>
<p>The preliminary analysis also shows that several KOS-es used frequently by libraries are not available as freely usable machine-readable resources. Maybe we could access some of those closed resources within this research, and also we could provide strong arguments for convincing the data owners to open their vocabularies for the greater good.</p>
<p>I will visualize the distribution of topics. I do not intend to create novel visualization form (such as recent improvements in LAM including [Kraker et al., 2016], [Oakes, 2017], and [Hibberd, 2018]), only to reuse the easily implementable parts of the available cutting edge technology.</p>

<h3>3b. Theoretical background</h3>
<p><em>Please provide a brief theoretical background on your project</em></p>
<p>Several papers can be found which investigated the quality of KOS themselves, but only 2-3 suggested metrics for KOS usages. The KOS metric I am most interested in is 'specificity' defined in [Inácio et al., 2017] and [Ferreira et al., 2017]. [Nogales et al., 2017] proposes different metrics such as vocabulary triples ratio, language usage, vocabulary’s class specialization, vocabulary’s property specialization, dominant vocabulary space, etc. [Suominen–Mader, 2014] categorized typical errors found in different SKOS vocabularies. They have also created an open source tool called qSKOS <a class="sdfootnoteanc" name="sdfootnote6anc" href="#sdfootnote6sym">[6]</a> to detect these errors. Their main categories are labelling and documentation (omitted or invalid language tags, incomplete language coverage, undocumented concepts, ...), structural criteria (orphan concepts, disconnected concept clusters, cyclic hierarchical relations, ...) and Linked Data (missing in-links and out-links, broken links). [Quarati et al., 2016] moves a step forward. They skipped some of [Suominen–Mader, 2014] metrics, and added the number of authoritative concepts available in the vocabulary. They introduced the concept of application context, which are usage scenarios in which the importance of the metrics are different. <a class="sdfootnoteanc" name="sdfootnote7anc" href="#sdfootnote7sym">[7]</a> They defined three scenarios: thesauri selection; thesaurus maintenance; thesaurus-based indexing. In the context of each scenarios they categorized metrics as relevant, less relevant, and irrelevant.</p>
<p>[Tarver et al., 2015] analysing Digital Public Library of America didn’t investigate the connection to KOS, they suggested metrics regarding to the existence and frequency of keywords on record level and on collection level.</p>
<p>Based on previous literature [da Graça Simões et al., 2018] identified two key principles that affect the retrieval of documents: exhaustivity and specificity. Exhaustivity relates to the number of subject that are translated to concrete representative terms for a document. Specificity is the level of detail which a particular concept is represented. They quoted the specificity definition of [Olson–Given, 2003] “the relative detail within the vocabular[y], the number of hierarchical levels defined, which increases with each level as hierarchy becomes deeper” which is close to the definition
of [Inácio et al., 2017].</p>
<p>[Lacasta et al., 2016] – as most of the cited literature – analysed thesauri, and not their usage. They set up the following measure categories: property completeness (completeness of preferred labels, uniqueness of preferred labels, ...), property content (detecting non-alphabetic characters, detecting adverbs, ...), property context (detecting duplicated labels, inconsistencies in the use of uppercase, ...), property complexity (syntactic complexity of the labels), and relation coherence (detecting non-informative relations, cycles in the model, ...). They used NLP technology, WordNet and DOLCE ontologies in the relation coherence measures. They provide algorithms, but do not release any software package alongside the paper.</p>
<p>[Wills, 2017] following [Kastrin et al., 2014] analysed the records of the MEDLINE citation database with network science methods. His main question was how it uses Medical Subject Headings (MeSH) classification scheme. The properties these papers investigated are the major topics and their co-occurrences; what are the connected components; degree distribution of the graph; how similar the citation graph is to other common real-world graph.</p>
<p>As far as I know there is no paper and tool about analysing the quality of large bibliographical dataset in terms of KOS usage, however in the revisited papers there are concepts which could be reused in the context of this research. I will investigate the computability and usefulness of these metrics, and probably new ones will be suggested if the existing ones will not proved to be enough to express the quality dimension of subject term usage.</p>

<h3>3c. Methods and techniques</h3>
<p><em>Please explain which methods or approach you will use to successfully complete your project</em></p>
<p>The research follows an iterative method. First the metrics should be selected, then they have to be implemented and calculate the scores on the selected datasets, finally we should evaluate the results together with KB Lab members and metadata expert (from and outside of KB). The project should provide feedback for the KOS service providers (including KB itself).</p>
<p>The development is a further development of a tool I’ve created during the doctoral research, which covers Extract-Transform-Load process, Exploratory Data Analysis, Machine Learning, Big Data analysis (written in Java, Scala, R, PHP, JavaScript). The data processing workflow contains four phases: data ingestion, feature extraction, data analysis and display of result via a ‘quality dashboard’. After the first round of discussions the tool may or may not be extended with additional input formats (above JSON and MARC).</p>

<h2>Outcomes</h2>
<p><em>Please describe what the outcomes of the project will be &amp; how you will use the KB data.</em></p>
<p>Outcomes:</p>
<ul>
	<li>a scientific paper about measuring subject term usage in bibliographical databases</li>
	<li>an open source software package which measures KOS quality metrics (on the level of the whole vocabulary and on the level of individual terms) which are not measured by other available packages (such as Skosify). This tool should be integrable to the above mentioned KOS services (BARTOC, coli-conc)</li>
	<li>an enhancement of the MARC quality assessment tool [Király, 2017], which integrates the measurements into a web based user interface alongside other, already implemented quality metrics</li>
	<li>testing the integration options into KB’s IT infrastructure and data workflow</li>
</ul>
<p>Based on preliminary research I plan to start with the Dutch National Bibliography <a class="sdfootnoteanc" name="sdfootnote8anc" href="#sdfootnote8sym">[8]</a> and Brinkman thesaurus <a class="sdfootnoteanc" name="sdfootnote9anc" href="#sdfootnote9sym">[9]</a>, however during the research if resources are available I might extend the set of analyzed data sources.</p>

<h2>Link to the KB Research agenda</h2>
<p><em>Please describe what the link is to the KB Research agenda. More information: <a href="https://www.kb.nl/organisatie/onderzoek-expertise/onderzoeksagenda-2018-2022">https://www.kb.nl/organisatie/onderzoek-expertise/onderzoeksagenda-2018-2022</a></em></p>
<p>The main goal of this project to help KB and the worldwide library community to improve the quality of their data. This has an impact in almost all items of the Research agenda.</p>
<p>To information society and customers: better data improves the services based on top of them by giving search and retrieval more precise and also more sensitive, which at the end makes KB a more reliable service from the customers’ point of view.</p>
<p>To publications: the proposed tool provides the same validation function for textual metadata as the JP2 Validator and Extractor tool does for JP2 images, so it will enhance KB’s current quality assurance process.</p>
<p>To access and sharing: the research’s contribution is the strongest in this theme, since it directly focuses the question “How do we improve the quality of our digital content?” By evaluating the effects of semi automatic processes described in [Kleppe et al., 2019], it provides feedback to them as well.</p>

<h2>Workplan and time table</h2>
<p><em>Please describe: 1) how you will work together with the KB team, 2) where or if you would need assistance, and 3) a short overview of the work per 2 months.</em></p>
<p>Metadata quality is a multi faceted and contextual dependent concept. In practice it means, that measuring requires input from the hosting institution about the functional requirements against data within the current KB services. During the research I plan to consult different expert groups of the library: metadata experts, IT staff, researchers to figure out their priorities regarding to the data. The research will be a row of iterative rounds: scanning of needs and expectations – research and implementation – discussing the results.</p>
<p>Above the consultation, I also need a virtual research infrastructure: a machine on which I could run the measurements. From this machine the necessary KB datasets should be accessible, it should have enough disk capacity store the data and the results, and it should be able to run an Apache based web site which is accessible from outside.</p>
<p>Planned time table:</p>

<table cellpadding="4" cellspacing="0">
	<col width="110">
	<tbody>
		<tr valign="top">
			<td>Months 1-2.</td>
			<td>Preliminary investigation regarding KB’s data (formats, access possibilities, rights and conditions). Setting up a virtual research environment (server, data access, tools). Discussions with KB’s (and external) metadata experts on their needs, opinions on quality and about the available data. Additional literature and implementation survey. Selecting relevant metrics.</td>
		</tr>
		<tr valign="top">
			<td>Months 3-4.</td>
			<td>Implementation phase. Set up the end user interface (quality dashboard) for metadata experts. Collecting feedback, improving the model and implementation iteratively. Rethink the metrics based on the results (some metrics probably will not be useful, other might be too complex to implement than previously expected).</td>
		</tr>
		<tr valign="top">
			<td>Months 5-6.</td>
			<td>Finalizing implementation. Publish a ‘stable enough’ release of the tool. Creating a pilot for integration into KB’s IT infrastructure and data workflow. Writing scientific paper. Display results and discuss the topic in the KB for an audience from KB and other organisations (Europeana, IFLA, CERL, DANS, Nationaal Archief, Archives Portal Europe etc.)</td>
		</tr>
	</tbody>
</table>

<h2>References</h2>
<p>da Graça Simões et al., 2018 – M. da Graça Simões, D. Martínez-Ávila, B. Rodríguez-Bravo, P. de Almeida, I. V. Evangelista, “Approaches to the concepts of exhaustivity and specificity in ISKO International meeting proceedings: 2000-2017” in: Challenges and Opportunities for Knowledge Organization in the Digital Age. Proceedings of the Fifteenth International ISKO Conference 9-11 July 2018 Porto, Portugal (Advances in Knowledge Organization, 16), pp. 58-65. (<a href="https://doi.org/10.5771/9783956504211-58">https://doi.org/10.5771/9783956504211-58</a>)</p>
<p>Ferreira et al., 2017 – J. Ferreira, B. Inácio, R. Salek, F. Couto, “Assessing Public Metabolomics Metadata, Towards Improving Quality” in Journal of Integrative Bioinformatics, pp. 14(4), 2017
(<a href="https://doi.org/10.1515/jib-2017-0054">https://doi.org/10.1515/jib-2017-0054</a>)</p>
<p>Gangemi et al., 2005 – A. Gangemi, C. Catenacci, M. Ciaramita, J. Lehmann, “A theoretical framework for ontology evaluation and validation.” 2005 (<a href="http://www.loa.istc.cnr.it/old/Papers/swap_final_v2.pdf">http://www.loa.istc.cnr.it/old/Papers/swap_final_v2.pdf</a>)</p>
<p>Hibberd, 2018 – G. Hibberd, “Speculative metaphors: a design-led approach to the visualisation of library collections.” PhD thesis. University of Technology Sydney, 2018. (<a href="https://opus.lib.uts.edu.au/handle/10453/135763">https://opus.lib.uts.edu.au/handle/10453/135763</a>)</p>
<p>Inácio et al., 2017 – B. Inácio, J. Ferreira, and F. Couto, “Metadata analyser: measuring metadata quality,” in Practical Applications of Computational Biology and Bioinformatics (PACBB), pp. 197--204, 2017 (<a href="https://doi.org/10.1007/978-3-319-60816-7_24">https://doi.org/10.1007/978-3-319-60816-7_24</a>)</p>
<p>Kastrin et al., 2014 – A. Kastrin, T. C. Rindflesch, D. Hristovski, “Large-Scale Structure of a Network of Co-Occurring MeSH Terms: Statistical Analysis of Macroscopic Properties”. PLoS ONE, 2014,
e102188 (<a href="https://doi.org/10.1371/journal.pone.0102188">https://doi.org/10.1371/journal.pone.0102188</a>)</p>
<p>Király, 2017 – P. Király, “Metadata assessment for MARC records“. Source code. 2017- (<a href="https://github.com/pkiraly/metadata-qa-marc">https://github.com/pkiraly/metadata-qa-marc</a>).
Some running instaces: <a href="http://134.76.163.21/dnb/">http://134.76.163.21/dnb/</a>, <a href="http://134.76.163.21/cerl/">http://134.76.163.21/cerl/</a>, <a href="http://134.76.163.21/gent/">http://134.76.163.21/gent/</a>.</p>
<p>Király, 2019 – P. Király, “Validating 126 million MARC records”. In P. Király, Measuring metadata quality. Ph.D. Thesis. 2019. (<a href="http://hdl.handle.net/21.11130/00-1735-0000-0003-C17C-8">http://hdl.handle.net/21.11130/00-1735-0000-0003-C17C-8</a>).</p>
<p>Király–Büchler, 2018 – P. Király, M. Büchler, “Measuring completeness as metadata quality metric in Europeana.” in 2018 IEEE International Conference on Big Data, IEEE, pp. 2711–2720.
(<a href="https://doi.org/10.1109/BigData.2018.8622487">https://doi.org/10.1109/BigData.2018.8622487</a>)</p>
<p>Kleppe et al., 2019 – M. Kleppe, S. Veldhoen, M. v. d. Waal-Gentenaar, B. d. Oudsten, D. Haagsma. “Exploration possibilities Automated Generation of Metadata”. Koninklijke Bibliotheek, 2019. (<a href="http://doi.org/10.5281/zenodo.3375192">http://doi.org/10.5281/zenodo.3375192</a>)</p>
<p>Kraker et al., 2016 – P. Kraker, Ch. Kittel, A. Enkhbayar, “Open Knowledge Maps: Creating a Visual Interface to the World’s Scientific Knowledge Based on Natural Language Processing”. 027.7 Journal for Library Culture, 2016. pp. 98-103 (<a href="https://0277.ch/ojs/index.php/cdrs_0277/article/view/157/338">https://0277.ch/ojs/index.php/cdrs_0277/article/view/157/338</a>)</p>
<p>Lacasta et al., 2016 – J. Lacasta, G. Falquet, F. J. Zarazaga-Soria, J. Nogueras-Iso, “An automatic method for reporting the quality of thesauri”. Data &amp; Knowledge Engineering, 2016, pp. 1-14 (<a href="https://doi.org/10.1016/j.datak.2016.05.002">https://doi.org/10.1016/j.datak.2016.05.002</a>)</p>
<p>Nogales et al., 2017 – A. Nogales, M. A. Sicilia-Urban, E. García-Barriocanal, “Measuring vocabulary use in the Linked Data Cloud”, Online Information Review, Vol. 41, 2017 Issue: 2, pp. 252-271 (<a href="https://doi.org/10.1108/OIR-06-2015-0183">https://doi.org/10.1108/OIR-06-2015-0183</a>)</p>
<p>Oakes, 2017 – G. Oakes, “Every Collection  is a Snowflake”. Presentation at SWIB, Hamburg, December 2017. Slides (<a href="https://swib.org/swib17/slides/oates_every-collection.pdf">https://swib.org/swib17/slides/oates_every-collection.pdf</a>)</p>
<p>Olson–Given, 2003 – H. A. Olson, L. M. Given, “Indexing and the ‘organized’ researcher”. The Indexer 2003. pp. 129-133. (<a href="https://www.researchgate.net/profile/Lisa_Given/publication/268052225_Indexing_and_the_'organized'_researcher/">https://www.researchgate.net/profile/Lisa_Given/publication/268052225_Indexing_and_the_'organized'_researcher/</a>)</p>
<p>Owens–Cochrane, 2004 – L. A. Owens, P. A. Cochrane, “Thesaurus Evaluation” in Cataloging &amp; Classification Quarterly 37:3-4 (2004) pp. 87-102 (<a href="http://doi.org/10.1300/J104v37n03_07">http://doi.org/10.1300/J104v37n03_07</a>)</p>
<p>Quarati et al., 2016 – A. Quarati, R. Albertoni, M. De Martino, “Overall quality assessment of SKOS thesauri: An AHP-based approach”. Journal of Information Science 2016. pp. 816-834. (<a href="http://doi.org/10.1177/0165551516671079">http://doi.org/10.1177/0165551516671079</a>)</p>
<p>Souza et al., 2012 – R. R. Souza, D. Tudhope, M. B. Almeida, “The KOS spectra: a tentative typology of Knowledge Organization Systems”. Knowledge Organization, 2012. pp. 179–192. (<a href="https://doi.org/10.5771/0943-7444-2012-3-179">https://doi.org/10.5771/0943-7444-2012-3-179</a>)</p>
<p>Stock, 2015 – W. G. Stock: “Informetric Analyses of Knowledge Organization Systems (KOSs).” (<a href="https://arxiv.org/abs/1505.03671">https://arxiv.org/abs/1505.03671</a>) Published in: C. R. Sugimoto (Ed.): Theories of Informetrics and Scholarly Communication. De Gruyter, 2015.</p>
<p>Stvillia et al., 2004 – B. Stvilia, L. Gasser, M. B. Twidale, S. L. Shreeves, T. W. Cole, “Metadata quality for federated collections”. In S. Chengulur-Smith, L. Raschid, J. Long, &amp; C. Seko (Eds.), Proceedings of the International Conference on Information Quality (ICIQ). 2004. pp. 111–125. Cambridge, MA: MIT. (<a href="http://hdl.handle.net/2142/145">http://hdl.handle.net/2142/145</a>)</p>
<p>Suominen et al., 2011 – O. Suominen, J. Voß, D. M. O. Heggø, S. Pessala, “Skosify. Validate, convert and improve SKOS vocabularies”. 2011- (<a href="https://github.com/NatLibFi/Skosify">https://github.com/NatLibFi/Skosify</a>)</p>
<p>Suominen–Mader, 2014 – O. Suominen, Ch. Mader, “Assessing and Improving the Quality of SKOS Vocabularies”. Journal of Data Semantics 2014. pp. 47–73 (<a href="http://doi.org/10.1007/s13740-013-0026-0">http://doi.org/10.1007/s13740-013-0026-0</a>)</p>
<p>Tarver et al., 2015 – H. Tarver, M. Phillips, O. Zavalina, P. Kizhakkethil, “An exploratory analysis of subject metadata in the digital public library of America”. In International Conference on Dublin Core and Metadata Applications. 2015. pp. 30--40. (<a href="https://dcpapers.dublincore.org/pubs/article/view/3761">https://dcpapers.dublincore.org/pubs/article/view/3761</a>).</p>
<p>Wills, 2017 – J. Wills, “Analyzing co-occurrence networks with GraphX”. In S. Ryza, U. Laserson, S. Owen, J. Wills: Advanced Analytics with Spark. 2017. pp. 141–171.</p>
<p>Zeng–Salaba, 2005 – M. L. Zeng, A. Salaba, “Toward an international sharing and use of subject authority data.” (PowerPoint presentation) In FRBR workshop, OCLC 2005. (<a href="http://www.oclc.org/research/events/frbr-workshop/presentations/zeng/Zeng_Salaba.ppt">http://www.oclc.org/research/events/frbr-workshop/presentations/zeng/Zeng_Salaba.ppt</a>)</p>

<h2>Notes</h2>
<p><a class="sdfootnotesym" name="sdfootnote1sym" href="#sdfootnote1anc">[1]</a> The experts I consulted: Rudolf Ungváry (retired, Hungarian National Library, HU), Gerard Coen (DANS and ISKO-NL, NL), Andreas Ledl (BARTOC and Uni Basel, CH), Anna Kasprzik (ZBW, DE), Jakob Voß (GBV, DE), Uma Balakrishnan (GBV, DE), Yann Y. Nicolas (ABES, FR), and Michael Franke-Maier (Freie Universität Berlin, DE), Gerhard Lauer (Uni Basel, CH).</p>
<p><a class="sdfootnotesym" name="sdfootnote2sym" href="#sdfootnote2anc">[2]</a> <a href="http://bartoc.org/">http://bartoc.org/</a></p>
<p><a class="sdfootnotesym" name="sdfootnote3sym" href="#sdfootnote3anc">[3]</a> <a href="http://coli-conc.gbv.de/">http://coli-conc.gbv.de/</a></p>
<p><a class="sdfootnotesym" name="sdfootnote4sym" href="#sdfootnote4anc">[4]</a> <a href="https://kxp.k10plus.de/">https://kxp.k10plus.de</a></p>
<p><a class="sdfootnotesym" name="sdfootnote5sym" href="#sdfootnote5anc">[5]</a> <a href="https://github.com/gbv/jskos-metrics">https://github.com/gbv/jskos-metrics</a></p>
<p><a class="sdfootnotesym" name="sdfootnote6sym" href="#sdfootnote6anc">[6]</a> <a href="https://github.com/cmader/qSKOS/">https://github.com/cmader/qSKOS/</a></p>
<p><a class="sdfootnotesym" name="sdfootnote7sym" href="#sdfootnote7anc">[7]</a> A similar concept are FRBR’s 12 fundamental functionalities, and the functional subdimensions defined within the Data Quality Committee of Europeana, see [Király–Büchler, 2018] and [Király, 2019].</p>
<p><a class="sdfootnotesym" name="sdfootnote8sym" href="#sdfootnote8anc">[8]</a> <a href="http://data.bibliotheken.nl/doc/dataset/nbt">http://data.bibliotheken.nl/doc/dataset/nbt</a></p>
<p><a class="sdfootnotesym" name="sdfootnote9sym" href="#sdfootnote9anc">[9]</a> <a href="http://data.bibliotheken.nl/doc/dataset/brinkman">http://data.bibliotheken.nl/doc/dataset/brinkman</a></p>
