---
title:      Report Number Four (Making General)
layout:     post
date:       2016-07-02 00:00:00
author:     "pkiraly"
customjs:
 - http://code.jquery.com/jquery-1.4.2.min.js
 - http://pkiraly.github.io/js/table.js
---

In the last weeks I was working on making the framework really general and reusable
in other project.  The initiative came from Europeana.  They would like to build in
the measurement into their ingestion service.  It was a good occasion to separate
different concerns of the source code.

<!-- more --> 

## Reorganization of the software

Now we have a top level (software) project: [Metadata Quality Assurance Framework API](http://github.com/pkiraly/metadata-qa-api). It contains the actual measurements,
and definition of the workflow. It also contains examples of metadata schema
abstractions. It is called API, because it is a Java API, and other projects use
this API in different context (for example in Apache Spark, command line interface,
or a REST API).

The second project is the [Europeana Quality Assurance API](http://github.com/pkiraly/europeana-qa-api).
It contains Europeana-related extension to the Metadata QA API.  Similar projects
will be writen to handle other cultural heritage metadata schemas, such as MARC,
DPLA schema, EAD and others.  I have started working with records come from an
OAI-PMH service, and now I have to work with records stored in MongoDB. Thes have
the same big structure, but have different naming conventions: OAI-PMH uses
qualified XML names, such as dc:title, while the MongoDB records follow the
camel-case naming convention, such as dcTitle.

The third layer contains the software which use Europeana QA API project. Now
we have two of them: [Europeana QA Spark](http://github.com/pkiraly/europeana-qa-spark), 
which is the Apache Spark interface, used for batch processing of record-level
measurements, and [Europeana QA Clients](http://github.com/pkiraly/europeana-qa-client)
which provides a REST interface to measuring.

In order to make the APIs useful in other projects they were published in the Maven Central.
For non Java savvy reader: this is a central repository of Java libraries. There are
tools, which helps you to use these libraries without the burden of downloading
and compiling the source codes. The libraries are available in
[The Central Repository](http://search.maven.org/#search%7Cga%7C1%7Cmetadataqa) or in [mvnrepository.com](http://mvnrepository.com/artifact/de.gwdg.metadataqa). All
the developer need is add the following lines to the `pom.xml` file:

```xml
<dependency>
    <groupId>de.gwdg.metadataqa</groupId>
    <artifactId>metadata-qa-api</artifactId>
    <version>0.2</version>
</dependency>
```
or if s/he wants to build on Europeana:

```xml
<dependency>
    <groupId>de.gwdg.metadataqa</groupId>
    <artifactId>europeana-qa-api</artifactId>
    <version>0.2</version>
</dependency>
```
Now we have two versions, 0.1, and 0.2, and 0.3 will be published soon. The API 
documentation is available [here](http://pkiraly.github.io/metadata-qa-api/).

## The Java API Usage

The central class (and usually this is the only one you have to use) is the EdmCalculatorFacade (in the de.gwdg.europeanaqa.api.calculator namespace). You have to do two things:

1. configure the object - i.e. deciding which metrics you want to run on the records
2. run the meausements
3. retrieve the results

### 1. Configuration

The result will contain a bunch of information depending on the configuration. The information blocks are:

1. Extracted fields from the JSON record: identifier, dataset and data provider
2. Completeness
    1. Existence of fields (if a field exists it gets 1, otherwise 0)
    2. Cardinality of fields (how many times a field exists in a record)
4. Uniqueness values of (at the time of writing) three fields: dc:title, dcterms:alterative, dc:description. Each values appear in two flavors: an aggregated one and an average
5. Problem catalog. You can check existence of known metadata problems in a record. The score gives you the number of times they appear in the record. Right now there are 3 problems defined: „long subject”, „ientical title and description”, and „empty strings”.
6. Encountering languages. It gives you a different return value - the codes used in the language attribute of a string value. Since it requires a different post-processing method it might worth to run in a separate batch process.
 
The parameters you can set:

1. `runFieldExistence(boolean)` configure to run the existence measurement (see #2.i in the above list)
2. `runFieldCardinality(boolean)` configure to run the cardinality measurement (see #2.ii in the above list)
3. `runCompleteness(boolean)` configure to run the completeness measurement (see #2 in the above list)
4. `runTfIdf(boolean)` configure to run the uniqueness measurement (see #4 in the above list)
5. `runProblemCatalog(boolean)` configure to run the problem catalog measurement (see #5 in the above list)
6. `runLanguage(boolean)` configure to run the language measurement (see #6 in the above list)

Other options:

* `verbose(boolean)` The completeness calculation will collect empty, existent and missing fields
* `abbreviate(boolean)` The field extractor will use a predefined dictionary to translate dataset and data provider names to numbers (which makes the output CSV smaller)
* `collectTfIdfTerms(boolean)` If it is set, the measurement will collect each individual terms with their Term Ferquency and Invers Document Frequency scores.

When you set the values, you have to issue

     calculator.configure();

to make everything prepared.

### 2. Run measurement

To run the measurement you have to call `measure(String)` method with the JSON string as the parameter. It parses JSON and if it finds invalid throws `com.jayway.jsonpath.InvalidJsonException` error. The method return the result as CSV (Comma Separated Values) string.

```java
try {
    String csv = calculator.measure(jsonRecord);
} catch (InvalidJsonException e) {
    // handle exception
}
```

### 3. Retrieve the results

The `measure()` method already returns a CSV string, but you might want more.

* `Map<String, Double> getResults()` returns the raw scores in a Map
* `List<String> getExistingFields()` returns the list of existing fields
* `List<String> getEmptyFields()` returns the list of empty fields
* `List<String> getMissingFields()` returns the list of missing fields
* `Map<String, List<TfIdf>> getTermsCollection()` returns the TF-IDF term list

## Examples

Note: these examples are for illustrating the API usage, when you write real code, organize it according to the general design and code organization principles.

### Most general usage: measuring scores

The first step the class provides a number of configuration options.

```java
import de.gwdg.europeanaqa.api.calculator.EdmCalculatorFacade;
import com.jayway.jsonpath.InvalidJsonException;

...
// create an instance and configure the object
EdmCalculatorFacade calculator = new EdmCalculatorFacade();
calculator.doAbbreviate(true);
calculator.runCompleteness(true);
calculator.runFieldCardinality(true);
calculator.runFieldExistence(true);
calculator.runTfIdf(false);
calculator.runProblemCatalog(true);
calculator.configure();

List<String> jsonRecords = ... // read JSON records from file/database
List<String> metrics = new ArrayList<>();
for (String jsonRecord : jsonRecords) {
   try {
      metrics.add(calculator.measure(jsonRecord));
   } catch (InvalidJsonException e) {
      // handle exception
   }
}
```

### Returning a JSON object (if you want to create a REST API)

First, create a Result object which is a simple placeholder for all the data:

```java
public class Result {
   private List<String> existingFields;
   private List<String> missingFields;
   private List<String> emptyFields;
   private Map<String, Double> results;
   private Map<String, List<TfIdf>> termsCollection;

   public Result() {} // a parameterless constructor is need for JSON converter

   ... // getters and setters come here
}
```

The main class:

```java
EdmCalculatorFacade calculator = new EdmCalculatorFacade();
calculator.abbreviate(true);
calculator.runCompleteness(true);
calculator.runFieldCardinality(true);
calculator.runFieldExistence(true);
calculator.runTfIdf(true);
calculator.runProblemCatalog(true);
calculator.collectTfIdfTerms(true);
calculator.verbose(true);
calculator.configure();

Result result = null;
try {
    calculator.measure(jsonRecord);

    result = new Result();
    result.setResults(calculator.getResults());
    result.setExistingFields(calculator.getExistingFields());
    result.setMissingFields(calculator.getMissingFields());
    result.setEmptyFields(calculator.getEmptyFields());
    result.setTermsCollection(calculator.getTermsCollection());
} catch (InvalidJsonException e) {
   // handle exception
}

String resultAsJson = null;
if (result != null) {
   ObjectMapper mapper = new ObjectMapper();
   try {
      resultAsJson = mapper.writeValueAsString(result);
   } catch (IOException ex) {
      // handle exception
   }
}

return resultAsJson;
```

### Measuring language usage

```java
EdmCalculatorFacade calculator = new EdmCalculatorFacade();
calculator.abbreviate(true);
calculator.runCompleteness(false);
calculator.runFieldCardinality(false);
calculator.runFieldExistence(false);
calculator.runTfIdf(false);
calculator.runProblemCatalog(false);
calculator.runLanguage(true);
calculator.configure();

List<String> jsonRecords = ... // read JSON records from file/database
List<String> metrics = new ArrayList<>();
for (String jsonRecord : jsonRecords) {
   try {
      metrics.add(calculator.measure(jsonRecord));
   } catch (InvalidJsonException e) {
      // handle exception
   }
}
```

This CSV is a bit different in nature than the basic one. Here is an excerpt:

```CSV
31,558,02301/urn_imss_biography_300020,it:1;en:1,_1:1,it:1;en:1,_1:1,it:1,_1:1,it:1;en:1,_0:1,_0:2,_1:1,...
```

As you can see the first three fields are the same as for the basic one (data provider, dataset and record id). After that however there are special units, which takes the form:

```
[language 1]:[count];[language 2]:[count];[language 3]:[count]...
```

where

* _[language 1]_, _[language 2]_ etc. means the language code as it appears in the record. There are special codes as well:
    * _ _0_: no language code specified
    * _ _1_: the field is missing (the very same information that of field existence metric)
    * _ _2_: the field is a resource (it contains a URL and tagged as resource)
* _[count]_ means the number of times a language appears in field instances

For example the following JSON fragment 

```JSON
"dc:title": [
  "Hamlet",
  {
    "@lang": "en",
    "#value": "Hamlet"
  }
]
```

will produce

```CSV
_0:1;en:1
```

because the first Hamlet doesn't have any language code specified, and the second one has `"en"`.

# The REST API

## Measure a record

### JSON response

```
http://example.com/europeana-qa/07602/696BE60475DFAF290B7CD7759E840CD4FFF86E24.json
```

```json
{
   "existingFields":[
      "edm:ProvidedCHO/@about",
      "Proxy/dc:title",
      "Proxy/dc:creator",
      "Proxy/dc:publisher",
      "Proxy/dc:type",
      "Proxy/dcterms:spatial",
      "Proxy/dc:subject",
      "Proxy/dcterms:created",
      "Proxy/dcterms:extent",
      "Proxy/dcterms:isPartOf",
      "Proxy/dc:format",
      "Proxy/dc:rights",
      "Proxy/edm:type",
      "Aggregation/edm:rights",
      "Aggregation/edm:provider",
      "Aggregation/edm:dataProvider",
      "Aggregation/edm:isShownAt",
      "Aggregation/edm:isShownBy",
      "Aggregation/edm:object"
   ],
   "missingFields":[
      "Proxy/dcterms:alternative",
      "Proxy/dc:description",
      "Proxy/dc:contributor",
      "Proxy/dc:identifier",
      "Proxy/dc:language",
      "Proxy/dc:coverage",
      "Proxy/dcterms:temporal",
      "Proxy/dc:date",
      "Proxy/dcterms:issued",
      "Proxy/dcterms:medium",
      "Proxy/dcterms:provenance",
      "Proxy/dcterms:hasPart",
      "Proxy/dc:source",
      "Proxy/dc:relation",
      "Proxy/edm:isNextInSequence",
      "Aggregation/edm:hasView"
   ],
   "emptyFields":[],
   "labelledResults":{
      "fields":{
         "recordId":"/07602/696BE60475DFAF290B7CD7759E840CD4FFF86E24",
         "dataset":"07602_Ag_IT_Culturalitalia_RegioneMarche",
         "dataProvider":"Regione Marche / SchedeS:AN"
      },
      "completeness":{
         "TOTAL":0.5428571428571428,
         "MANDATORY":1.0,
         "DESCRIPTIVENESS":0.45454545454545453,
         "SEARCHABILITY":0.5555555555555556,
         "CONTEXTUALIZATION":0.45454545454545453,
         "IDENTIFICATION":0.5,
         "BROWSING":0.5,
         "VIEWING":0.75,
         "REUSABILITY":0.7272727272727273,
         "MULTILINGUALITY":0.4
      },
      "existence":{
         "edm:ProvidedCHO/@about":true,
         "Proxy/dc:title":true,
         "Proxy/dcterms:alternative":false,
         "Proxy/dc:description":false,
         "Proxy/dc:creator":true,
         "Proxy/dc:publisher":true,
         "Proxy/dc:contributor":false,
         "Proxy/dc:type":true,
         "Proxy/dc:identifier":false,
         "Proxy/dc:language":false,
         "Proxy/dc:coverage":false,
         "Proxy/dcterms:temporal":false,
         "Proxy/dcterms:spatial":true,
         "Proxy/dc:subject":true,
         "Proxy/dc:date":false,
         "Proxy/dcterms:created":true,
         "Proxy/dcterms:issued":false,
         "Proxy/dcterms:extent":true,
         "Proxy/dcterms:medium":false,
         "Proxy/dcterms:provenance":false,
         "Proxy/dcterms:hasPart":false,
         "Proxy/dcterms:isPartOf":true,
         "Proxy/dc:format":true,
         "Proxy/dc:source":false,
         "Proxy/dc:rights":true,
         "Proxy/dc:relation":false,
         "Proxy/edm:isNextInSequence":false,
         "Proxy/edm:type":true,
         "Aggregation/edm:rights":true,
         "Aggregation/edm:provider":true,
         "Aggregation/edm:dataProvider":true,
         "Aggregation/edm:isShownAt":true,
         "Aggregation/edm:isShownBy":true,
         "Aggregation/edm:object":true,
         "Aggregation/edm:hasView":false
      },
      "cardinality":{
         "edm:ProvidedCHO/@about":1,
         "Proxy/dc:title":1,
         "Proxy/dcterms:alternative":0,
         "Proxy/dc:description":0,
         "Proxy/dc:creator":1,
         "Proxy/dc:publisher":1,
         "Proxy/dc:contributor":0,
         "Proxy/dc:type":2,
         "Proxy/dc:identifier":0,
         "Proxy/dc:language":0,
         "Proxy/dc:coverage":0,
         "Proxy/dcterms:temporal":0,
         "Proxy/dcterms:spatial":1,
         "Proxy/dc:subject":3,
         "Proxy/dc:date":0,
         "Proxy/dcterms:created":1,
         "Proxy/dcterms:issued":0,
         "Proxy/dcterms:extent":2,
         "Proxy/dcterms:medium":0,
         "Proxy/dcterms:provenance":0,
         "Proxy/dcterms:hasPart":0,
         "Proxy/dcterms:isPartOf":1,
         "Proxy/dc:format":1,
         "Proxy/dc:source":0,
         "Proxy/dc:rights":1,
         "Proxy/dc:relation":0,
         "Proxy/edm:isNextInSequence":0,
         "Proxy/edm:type":1,
         "Aggregation/edm:rights":1,
         "Aggregation/edm:provider":1,
         "Aggregation/edm:dataProvider":1,
         "Aggregation/edm:isShownAt":1,
         "Aggregation/edm:isShownBy":1,
         "Aggregation/edm:object":1,
         "Aggregation/edm:hasView":0
      },
      "uniqueness":{
         "dc:title:sum":0.001084612782467948,
         "dc:title:avg":1.8076879707799135E-4,
         "dcterms:alternative:sum":0.0,
         "dcterms:alternative:avg":0.0,
         "dc:description:sum":0.0,
         "dc:description:avg":0.0
      },
      "problemCatalog":{
         "LongSubject":1.0,
         "TitleAndDescriptionAreSame":0.0,
         "EmptyStrings":0.0
      },
      "languages":{
         "Proxy/dc:title":{
            "_0":1
         },
         "Proxy/dcterms:alternative":{
            "_1":1
         },
         "Proxy/dc:description":{
            "_1":1
         },
         "Proxy/dc:creator":{
            "_0":1
         },
         "Proxy/dc:publisher":{
            "_0":1
         },
         "Proxy/dc:contributor":{
            "_1":1
         },
         "Proxy/dc:type":{
            "_0":2
         },
         "Proxy/dc:identifier":{
            "_1":1
         },
         "Proxy/dc:language":{
            "_1":1
         },
         "Proxy/dc:coverage":{
            "_1":1
         },
         "Proxy/dcterms:temporal":{
            "_1":1
         },
         "Proxy/dcterms:spatial":{
            "_0":1
         },
         "Proxy/dc:subject":{
            "_0":3
         },
         "Proxy/dc:date":{
            "_1":1
         },
         "Proxy/dcterms:created":{
            "_0":1
         },
         "Proxy/dcterms:issued":{
            "_1":1
         },
         "Proxy/dcterms:extent":{
            "_0":2
         },
         "Proxy/dcterms:medium":{
            "_1":1
         },
         "Proxy/dcterms:provenance":{
            "_1":1
         },
         "Proxy/dcterms:hasPart":{
            "_1":1
         },
         "Proxy/dcterms:isPartOf":{
            "_0":1
         },
         "Proxy/dc:format":{
            "_0":1
         },
         "Proxy/dc:source":{
            "_1":1
         },
         "Proxy/dc:rights":{
            "_0":1
         },
         "Proxy/dc:relation":{
            "_1":1
         },
         "Aggregation/edm:rights":{
            "_0":1
         },
         "Aggregation/edm:provider":{
            "_0":1
         },
         "Aggregation/edm:dataProvider":{
            "_0":1
         }
      }
   },
   "termsCollection":{
      "dc:title":[
         {
            "term":"ancona",
            "tf":1,
            "df":12388,
            "tfIdf":8.072328059412334E-5
         },
         {
            "term":"carta",
            "tf":1,
            "df":87048,
            "tfIdf":1.1487914713721165E-5
         },
         {
            "term":"della",
            "tf":1,
            "df":629250,
            "tfIdf":1.5891934843067143E-6
         },
         {
            "term":"di",
            "tf":1,
            "df":1837113,
            "tfIdf":5.443323301288489E-7
         },
         {
            "term":"marca",
            "tf":1,
            "df":15752,
            "tfIdf":6.348400203148806E-5
         },
         {
            "term":"topografica",
            "tf":1,
            "df":1079,
            "tfIdf":9.267840593141798E-4
         }
      ],
      "dcterms:alternative":[],
      "dc:description":[]
   }
}
```

### CSV response

```
http://example.com/europeana-qa/07602/696BE60475DFAF290B7CD7759E840CD4FFF86E24.csv
```

```csv
/07602/696BE60475DFAF290B7CD7759E840CD4FFF86E24,07602_Ag_IT_Culturalitalia_RegioneMarche,Regione Marche / SchedeS:AN,0.542857,1.0,0.454545,0.555556,0.454545,0.5,0.5,0.75,0.727273,0.4,1,1,0,0,1,1,0,1,0,0,0,0,1,1,0,1,0,1,0,0,0,1,1,0,1,0,0,1,1,1,1,1,1,1,0,0.001085,0.000181,0.0,0.0,0.0,0.0,1.0,0.0,0.0
```


## The Workflow API

Measuring of individual records has a serious some limitation: it doesn't cover the 
analysis phase, so we add a Workflow API, which helps collections to measure arbitrary
records, run the analysis, then download the results. The analysis is created by an R
script (from the [europeana-qa-r](http://github.com/pkiraly/europeana-qa-r) package), and 
it produces PNG images and JSON files.

The workflow has the following parts:

1. Measuring individual records
    1. Initializing the measuring session. The server returns a sessionId, which should be used in the whole session
    2. Measure individual records one-by-one
    3. Finishing the measuring session
2. Analyzing the records
    1. Initializing the analyzation phase
    2. Checking the current status perodically. While it is "in progress" the analyzation is running. When it returns "ready" the analyzation is done, and prepared to download.
    3. Downloading the results as a compressed package of JSON and image files.

Here is the workflow illustrating as communication between the client and the API:

1.i. Initializing the measuring session

```
   [client]                                         [server]
      || o- /batch/measuring/start  - - - - - - - - -> ||
      || <- - - - - - - - - - - - - - - [sessionId] -o ||
```

The returned information:

```json
{
  "sessionId": "61d62786-97c0-4b67-8f5d-fb38184a35be",
  "status": "MEASURING",
  "result": "success"
}
```

1.ii. Measure individual records one-by-one

```
   [client]                                         [server]
      || o- /batch/[recordId]?sessionId=[sessionId] -> ||
      || <- - - - - - - - - - - - - - - - - - [csv] -o ||
      || o- /[recordId].csv?sessionId=[sessionId] - -> ||
      || <- - - - - - - - - - - - - - - - - - [csv] -o ||
      || o- /[recordId].csv?sessionId=[sessionId] - -> ||
      || <- - - - - - - - - - - - - - - - - - [csv] -o ||
```

The returned information:

```json
{
  "sessionId": "61d62786-97c0-4b67-8f5d-fb38184a35be",
  "status": "MEASURING",
  "result": "success"
}
```

1.iii. Finishing the measuring session

```
   [client]                                         [server]
      || o- /measuring-session/[sessionId]/stop - - -> ||
      || <- - - - - - - - - - - - - - - - "success" -o ||
```

The returned information:

```json
{
   "sessionId": "09441177-566e-472c-93e8-7ca002bbaa09",
   "status": "IDLE",
   "result": "success"
}
```

2.i. Initializing the analyzation phase

```
   [client]                                         [server]
      || o- /batch/analyzing/[sessionId]/start  - - -> ||
      || <- - - - - - - - - - - - - - - - "success" -o ||
```

The returned information:

```json
{
   "sessionId": "61d62786-97c0-4b67-8f5d-fb38184a35be",
   "status": "ANALYZING",
   "result": "success"
}
```

2.ii. Checking the current status perodically.

```
   [client]                                         [server]
      || o- /batch/analyzing/[sessionId]/status - - -> ||
      || <- - - - - - - - - - - - - - "in progress" -o ||
      || o- /batch/analyzing/[sessionId]/status - - -> ||
      || <- - - - - - - - - - - - - - - - - "ready" -o ||
```

The returned information:

```json
{
   "sessionId": "61d62786-97c0-4b67-8f5d-fb38184a35be",
   "status": "ANALYZING",
   "result":"in progress"
}
```

and when ready

```json
{
   "sessionId": "61d62786-97c0-4b67-8f5d-fb38184a35be",
   "status": "ANALYZING",
   "result": "ready"
}
```

2.iii. Downloading the results as a compressed package of JSON and image files.

```
   [client]                                         [server]
      || o- /batch/analyzing/[sessionId]/retrieve - -> ||
      || <- - - - - - - - - -  [compressed package] -o ||
```

The returned information is a zipped package. Here is the HTTP header:

```
HTTP/1.1 200 OK
Server: Apache-Coyote/1.1
Content-Disposition: attachment; filename=analysis.zip
Content-Type: application/zip
Transfer-Encoding: chunked
Date: Wed, 29 Jun 2016 15:31:27 GMT
```

A full session with command line tools:
```
curl -i http://example.com/europeana-qa/batch/measuring/start
```
extract the `sessionId` from the response and apply to the consecutive calls. In this example we use `90836afd-c3ec-4718-bece-38df214b90a9` as `sessionId`.

```
curl -i "http://example.com/europeana-qa/batch/00718/plink__f_1_358116?sessionId=90836afd-c3ec-4718-bece-38df214b90a9"
curl -i "http://example.com/europeana-qa/batch/00719/plink__f_1_100466?sessionId=90836afd-c3ec-4718-bece-38df214b90a9"
curl -i "http://example.com/europeana-qa/batch/00720/plink__f_1_324593?sessionId=90836afd-c3ec-4718-bece-38df214b90a9"
curl -i "http://example.com/europeana-qa/batch/00721/plink__f_1_513237?sessionId=90836afd-c3ec-4718-bece-38df214b90a9"
curl -i "http://example.com/europeana-qa/batch/00722/plink__f_1_823046?sessionId=90836afd-c3ec-4718-bece-38df214b90a9"
curl -i "http://example.com/europeana-qa/batch/00723/plink__f_1_117537?sessionId=90836afd-c3ec-4718-bece-38df214b90a9"
curl -i "http://example.com/europeana-qa/batch/00724/plink__f_2_316301?sessionId=90836afd-c3ec-4718-bece-38df214b90a9"
curl -i "http://example.com/europeana-qa/batch/00725/plink__f_2_392027?sessionId=90836afd-c3ec-4718-bece-38df214b90a9"
curl -i "http://example.com/europeana-qa/batch/00732/plink__f_5_132900?sessionId=90836afd-c3ec-4718-bece-38df214b90a9"
curl -i "http://example.com/europeana-qa/batch/00733/plink__f_5_171135?sessionId=90836afd-c3ec-4718-bece-38df214b90a9"
curl -i "http://example.com/europeana-qa/batch/00734/plink__f_5_191118?sessionId=90836afd-c3ec-4718-bece-38df214b90a9"
curl -i "http://example.com/europeana-qa/batch/00735/plink__f_5_196907?sessionId=90836afd-c3ec-4718-bece-38df214b90a9"
curl -i "http://example.com/europeana-qa/batch/00736/plink__f_5_216082?sessionId=90836afd-c3ec-4718-bece-38df214b90a9"
curl -i "http://example.com/europeana-qa/batch/00737/plink__f_5_90496?sessionId=90836afd-c3ec-4718-bece-38df214b90a9"
curl -i "http://example.com/europeana-qa/batch/00738/plink__f_5_128247?sessionId=90836afd-c3ec-4718-bece-38df214b90a9"
curl -i "http://example.com/europeana-qa/batch/00739/plink__f_5_405012?sessionId=90836afd-c3ec-4718-bece-38df214b90a9"
curl -i "http://example.com/europeana-qa/batch/00740/plink__f_5_169255?sessionId=90836afd-c3ec-4718-bece-38df214b90a9"
curl -i "http://example.com/europeana-qa/batch/00741/plink__f_5_118287?sessionId=90836afd-c3ec-4718-bece-38df214b90a9"
curl -i "http://example.com/europeana-qa/batch/00742/plink__f_6_361080?sessionId=90836afd-c3ec-4718-bece-38df214b90a9"
curl -i "http://example.com/europeana-qa/batch/00743/plink__f_6_111738?sessionId=90836afd-c3ec-4718-bece-38df214b90a9"
curl -i "http://example.com/europeana-qa/batch/00744/plink__f_1_696030?sessionId=90836afd-c3ec-4718-bece-38df214b90a9"
curl -i "http://example.com/europeana-qa/batch/00746/plink__f_6_456644?sessionId=90836afd-c3ec-4718-bece-38df214b90a9"
curl -i "http://example.com/europeana-qa/batch/00747/plink__f_6_455430?sessionId=90836afd-c3ec-4718-bece-38df214b90a9"
curl -i http://example.com/europeana-qa/batch/measuring/90836afd-c3ec-4718-bece-38df214b90a9/stop
curl -i http://example.com/europeana-qa/batch/analyzing/90836afd-c3ec-4718-bece-38df214b90a9/start
curl -i http://example.com/europeana-qa/batch/analyzing/90836afd-c3ec-4718-bece-38df214b90a9/status
wget --content-disposition http://example.com/europeana-qa/batch/analyzing/90836afd-c3ec-4718-bece-38df214b90a9/retrieve
```

At the end it will save the analysis.zip into the current directory.

## The result

The `analysis.zip` file contains the following files:

```
.
├── 813158d3-a0f3-4620-8fc5-2ef3162cbd18.collector.json
├── 813158d3-a0f3-4620-8fc5-2ef3162cbd18.count.json
├── 813158d3-a0f3-4620-8fc5-2ef3162cbd18.freq.json
├── 813158d3-a0f3-4620-8fc5-2ef3162cbd18.hist.json
├── 813158d3-a0f3-4620-8fc5-2ef3162cbd18.json
├── browsing.png
├── contextualization.png
├── descriptiveness.png
├── entropy_dc_description_avg.png
├── entropy_dc_description_sum.png
├── entropy_dcterms_alternative_avg.png
├── entropy_dcterms_alternative_sum.png
├── entropy_dc_title_avg.png
├── entropy_dc_title_sum.png
├── identification.png
├── mandatory.png
├── multilinguality.png
├── reusability.png
├── searchability.png
├── total.png
└── viewing.png
```

### sessionId.hist.json -- the histograms of the measured features 

* _label_: the label of the bins
* _count_: the count of records in the bin
* _density_: the percent of records in the bin

```json
{
  "total":[
    {"label":"0.45 - 0.46","count":"3","density":"13.0434782608696"},
    {"label":"0.46 - 0.47","count":"0","density":"0"},
    {"label":"0.47 - 0.48","count":"0","density":"0"},
    {"label":"0.48 - 0.49","count":"14","density":"60.8695652173913"},
    {"label":"0.49 - 0.5","count":"0","density":"0"},
    {"label":"0.5 - 0.51","count":"0","density":"0"},
    {"label":"0.51 - 0.52","count":"3","density":"13.0434782608696"},
    {"label":"0.52 - 0.53","count":"0","density":"0"},
    {"label":"0.53 - 0.54","count":"0","density":"0"},
    {"label":"0.54 - 0.55","count":"3","density":"13.0434782608696"}
  ],
  "mandatory":[
    {"label":"0 - 1","count":"23","density":"100"}
  ],
  "descriptiveness":[
    {"label":"0.36 - 0.37","count":"15","density":"65.2173913043478"},
    {"label":"0.37 - 0.38","count":"0","density":"0"},
    ...
  ],
  ...
}
```

### sessionId.freq.json -- the field frequencies

* _field_: the name of the field
* _count_: how many records has the field
* _frequency_: the ratio of the field existence (between 0-1)

```json
[
  {"field":"identifier","count":23,"frequency":1},
  {"field":"proxy_dc_title","count":23,"frequency":1},
  {"field":"proxy_dcterms_alternative","count":0,"frequency":0},
  {"field":"proxy_dc_description","count":23,"frequency":1},
  {"field":"proxy_dc_creator","count":0,"frequency":0},
  {"field":"proxy_dc_publisher","count":0,"frequency":0},
  {"field":"proxy_dc_contributor","count":0,"frequency":0},
  {"field":"proxy_dc_type","count":1,"frequency":0.0435},
  {"field":"proxy_dc_identifier","count":23,"frequency":1},
  {"field":"proxy_dc_language","count":23,"frequency":1},
  {"field":"proxy_dc_coverage","count":0,"frequency":0},
  ...
]
```

### sessionId.count.json -- the count of records


```json
[{"count":23,"_row":"count"}]
```

### sessionId.json -- the descriptive statistics of the completeness sub-dimensions

* _min_: minimum value
* _max_: maximum value
* _range_: range between minimum and maximum
* _mean_: the mean
* _SE.mean_:
* _CI.mean_:
* _var_: variance
* _std.dev_: standard deviation
* _coaf.var_: coefficient variance
* _recMin_: record identifier with minimum value
* _recMax_: record identifier with maximum value
* _ _row_: the name of the metrics

```json
[
   {
      "min":0.4571,
      "max":0.5429,
      "range":0.0857,
      "median":0.4857,
      "mean":0.4932,
      "SE.mean":0.0051,
      "CI.mean.0.95":0.0107,
      "var":0.0006,
      "std.dev":0.0247,
      "coef.var":0.0501,
      "recMin":"[recordId]",
      "recMax":"[recordId]",
      "_row":"total"
   },
   {
      ...
      "_row":"mandatory"
   },
   {
      ...
      "_row":"descriptiveness"
   },
   {
      ...
      "_row":"searchability"
   },
   {
      ...
      "_row":"contextualization"
   },
   {
      ...
      "_row":"identification"
   },
   {
      ...
      "_row":"browsing"
   },
   {
      ...
      "_row":"viewing"
   },
   {
      ...
      "_row":"reusability"
   },
   {
      ...
      "_row":"multilinguality"
   },
   {
      ...
      "_row":"entropy_dc_title_sum"
   },
   {
      ...
      "_row":"entropy_dc_title_avg"
   },
   {
      ...
      "_row":"entropy_dcterms_alternative_sum"
   },
   {
      ...
      "_row":"entropy_dcterms_alternative_avg"
   },
   {
      ...
      "_row":"entropy_dc_description_sum"
   },
   {
      ...
      "_row":"entropy_dc_description_avg"
   }
]
```

### sessionId.collector.json -- an all-in-one JSON

It contains

* the count
* the frequencies
* general statistics about the completeness
* histograms

```json
{
   "count":[
      23
   ],
   "frequencies":[
     ...
   ],
   "stats":[
     ...
   ],
   "histograms":{
     ...
   }
}
```
