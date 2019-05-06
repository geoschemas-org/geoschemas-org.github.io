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

* [Intervals](#intervals)
* [Instants](#instants)

The [OWL Time](https://www.w3.org/TR/owl-time/) vocabulary defines useful ways for describing the temporal coverage. The temporalCoverage of a Dataset indicates the period of time that the contents of the dataset apply. This extension to schema:Dataset allows for the description of temporal coverages that cannot be described using a ISO 8601 formatted date (and time). Some examples of such coverages are geologic time scales, seasonal coverages across multiple years, or certain days of the week. The coverage is expressed as a time:TemporalEntity, typcially a time:Interval or a time:Instant.

<a id="intervals"></a>
## Intervals

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

<a id="instants"></a>
## Instants
