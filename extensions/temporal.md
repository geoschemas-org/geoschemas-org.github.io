---
title: Temporal Coverage
nav-section: Extensions
nav:
  - title: Home 
    url: /
  - title: Extensions 
    url: /extensions/
  - title: Temporal Coverage 
---

__Namespace Prefix__: geosci-time

__Namespace URI__: 	[http://geoschemas.org/contexts/temporal.jsonld](http://geoschemas.org/contexts/temporal.jsonld)


* [Classes](#classes)
* [Properties](#properties)
  * [geosci-time:temporalCoverage](#temporalCoverage)
* [Named Individuals](#namedindividuals)
  * [geosci-time:BeforePresent](#BeforePresent)
  * [geosci-time:MillionsOfYears](#MillionsOfYears)
* [Examples](#examples)  
  * [Describing Time Intervals](#intervals)
  * [Describing Time Instants](#instants)

<a name="classes"></a>

## Classes

*none*

[back to top](#top)
<a name="properties"></a>
<hr/>


<a name="temporalCoverage"></a>
## Properties

__geosci-time:temporalCoverage__ - Use the [OWL-Time vocabulary](https://www.w3.org/TR/owl-time/) to describe the temporal coverage of a Dataset.

Domain: [schema:Dataset](http://schema.org/Dataset)

Range: [time:TemporalEntity](https://www.w3.org/TR/owl-time/#time:TemporalEntity)

The [OWL Time vocabulary](https://www.w3.org/TR/owl-time/) defines useful ways for describing the temporal coverage. The temporalCoverage of a Dataset indicates the period of time that the contents of the dataset apply. This extension to schema:Dataset allows for the description of temporal coverages that cannot be described using a ISO 8601 formatted date (and time). Some examples of such coverages are geologic time scales, seasonal coverages across multiple years, or certain days of the week. The coverage is expressed as a time:TemporalEntity, typcially a time:Interval or a time:Instant.

[back to top](#top)

<a name="namedindividuals"></a>
<hr/>

<a name="BeforePresent"></a>
## Named Individuals

__geosci-time:BeforePresent__ - For defining the 'Before Present' (BP) temporal reference system for use in OWL-Time ([time:hasTRS](https://www.w3.org/TR/owl-time/#time:hasTRS))

Type: [time:TRS](https://www.w3.org/TR/owl-time/#time:TRS)

Temporal position expressed numerically in years before January 1, 1950

<a name="MillionsOfYears"></a>
__geosci-time:MillionsOfYears__ - For defining the 'Millions of Years' (Ma) temporal reference system for use in OWL-Time ([time:hasTRS](https://www.w3.org/TR/owl-time/#time:hasTRS))

Type: [time:TRS](https://www.w3.org/TR/owl-time/#time:TRS)

Same As: http://resource.geosciml.org/classifier/cgi/geologicage/ma

Temporal position expressed numerically scaled in millions of years increasing backwards relative to 1950

[back to top](#top)

<a name="examples"></a>
<hr/>

<a id="intervals"></a>
## Examples


### Intervals

### Simple Date Time Temporal Coverage ###

To express an interval of time as the coverage for a [schema:Dataset](http://schema.org/Dataset), schema.org provides the [schema:temporalCoverage](http://schema.org/temporalCoverage) which allows for defining a coverage using ISO 
Example: Expressing a time interval using a [time:TemporalEntity](https://www.w3.org/TR/owl-time/#time:TemporalEntity)
```
{
  "@context":  {
      "@vocab": "http://schema.org/",
      "time": "http://www.w3.org/2006/time#",
      "geosci-time": "http://geoschemas.org/contexts/temporal.jsonld"
   },
  "@type": "Dataset",
  ...
  "temporalCoverage": {"@value": "2019-03-31T00:00:00Z/2019-04-30T06:00:00Z"},
  "geosci-time:temporalCoverage": {
    "@type": "time:TemporalEntity",
    "time:hasBeginning": {
      "@type": "time:Instant",
      "time:inXSDDateTimeStamp": "2019-03-31T00:00:00Z"
    },
    "time:hasEnd": {
      "@type": "time:Instant",
      "time:inXSDDateTimeStamp": "2019-04-30T06:00:00Z"
    }
  }
}
```

### Seasonal Coverage ###

A dataset that collected measurements every Summer between 2012 and 2015. For discovery, if a data searcher was more interested in data collected during the Winter, a dataset with measurements in the summer can be excluded to improve precision and recall. Conversely, searchers looking for data in the Summer months is enabled.

A table of the begin and end dates of data collection from 2012 to 2015.

| Year | Begin | End |
| ---- | ----- | --- |
| 2012 | 2012-06-30 | 2012-09-09 |
| 2013 | 2013-07-06 | 2013-09-03 |
| 2014 | 2014-07-03 | 2014-09-06 |
| 2015 | 2015-06-29 | 2015-09-04 |


To describe a seasonal coverage, we define the full temporal coverage using the first and last date of collection

Temporal Coverage: 2012-06-30 to 2015-09-04

Then, we use the [time:intervalContains](https://www.w3.org/TR/owl-time/#time:intervalContains) property to describe the begin and end date of each year for this full temporal coverage.
```
{
  "@context":  {
      "@vocab": "http://schema.org/",
      "time": "http://www.w3.org/2006/time#",
      "geosci-time": "http://geoschemas.org/contexts/temporal.jsonld"
   },
  "@type": "Dataset",
  ...
  "temporalCoverage": {"@value": "2012-06-30/2015-09-04"},
  "geosci-time:temporalCoverage": {
    "@type": "time:ProperInterval",
    "time:hasBeginning": {
      "@type": "time:Instant",
      "time:inXSDDate": "2012-06-30"
    },
    "time:hasEnd": {
      "@type": "time:Instant",
      "time:inXSDDate": "2015-09-04"
    },
    "time:intervalContains":[
      {
        "@type": "time:ProperInterval",
        "time:hasBeginning": {
          "@type": "time:Instant",
          "time:inXSDDate": "2012-06-30"
        },
        "time:hasEnd": {
          "@type": "time:Instant",
          "time:inXSDDate": "2012-09-09"
        }
      },
      {
        "@type": "time:ProperInterval",
        "time:hasBeginning": {
          "@type": "time:Instant",
          "time:inXSDDate": "2013-07-06"
        },
        "time:hasEnd": {
          "@type": "time:Instant",
          "time:inXSDDate": "2013-09-03"
        }
      },
      {
        "@type": "time:ProperInterval",
        "time:hasBeginning": {
          "@type": "time:Instant",
          "time:inXSDDate": "2014-07-03"
        },
        "time:hasEnd": {
          "@type": "time:Instant",
          "time:inXSDDate": "2014-09-06"
        }
      },
      {
        "@type": "time:ProperInterval",
        "time:hasBeginning": {
          "@type": "time:Instant",
          "time:inXSDDate": "2015-06-29"
        },
        "time:hasEnd": {
          "@type": "time:Instant",
          "time:inXSDDate": "2015-09-04"
        }
      }
    ]
  }
}
```
[back to top](#top)
<a id="instants"></a>
### Instants

[back to top](#top)
