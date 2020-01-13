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

__Namespace URI__: 	[http://schema.geoschemas.org/contexts/temporal#](http://geoschemas.org/contexts/temporal.jsonld)


* [OWL Time](#owl-time)
  * [Intervals](#intervals)
  * [Instants](#instants)
    * [Geologic Time Scales](#geologic-time-scales)
      * [Before Present](#before-present)
      * [Millions of Years](#millions-of-years)
  * [Durations](#durations)
  * [Seasonality](#seasonality)
  
## OWL Time

The [OWL Time](https://www.w3.org/TR/owl-time/) vocabulary defines useful ways for describing the temporal coverage. The temporalCoverage of a Dataset indicates the period of time that the contents of the dataset apply. This extension to schema:Dataset allows for the description of temporal coverages that cannot be described using a ISO 8601 formatted date (and time). Some examples of such coverages are geologic time scales, seasonal coverages across multiple years, or certain days of the week. The coverage is expressed as a time:TemporalEntity, typcially a time:Interval or a time:Instant.
[OWL Time in RDF Turtle](http://www.w3.org/2006/time#)

![https://www.w3.org/TR/owl-time/](https://www.w3.org/TR/owl-time/images/TemporalEntity.png)

### Intervals

#### Simple Date Time Temporal Coverage

To express an interval of time as the coverage for a [schema:Dataset](http://schema.org/Dataset), schema.org provides the [schema:temporalCoverage](http://schema.org/temporalCoverage) which allows for defining a coverage using ISO 
Example: Expressing a time interval using a [time:TemporalEntity](https://www.w3.org/TR/owl-time/#time:TemporalEntity)
```
{
  "@context": {
    "@vocab": "http://schema.org/",
    "time": "http://www.w3.org/2006/time",
    "geosci-time": "http://schema.geoschemas.org/contexts/temporal#"
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

### Instants

Instants in time are useful for describing a position in time where an event occurred. For Datasets, the temporal coverage may be an instant instead of an interval for cases where all observations were made inn a single point in time or for observations in geologic time scales.

<a name="geologic-time-scales"></a>
The Geoschemas context defines 2 geologic time scales:

#### Before Present

[http://schema.geoschemas.org/contexts/temporal#BeforePresent](http://schema.geoschemas.org/contexts/temporal#BeforePresent)

Temporal position expressed numerically in years before January 1, 1950

#### Millions Of Years

[http://schema.geoschemas.org/contexts/temporal#MillionsOfYears](http://schema.geoschemas.org/contexts/temporal#MillionsOfYears)

Temporal position expressed numerically scaled in millions of years increasing backwards relative to 1950"

To specify a Geologic Time Scale, we use an OWL Time Instant. The example below specifies 2 million years before present:

<pre>
{
  "@context": {
    "@vocab": "http://schema.org/",
    "time": "http://www.w3.org/2006/time",
    "geosci-time": "http://schema.geoschemas.org/contexts/temporal#"
  },
  "@type": "Dataset",
  ...
  "geosci-time:temporalCoverage": {
    "@type": "time:Instant",
    "time:inTimePosition": {
      "@type": "time:TimePosition",
      <strong>"time:hasTRS": { "@id": "geosci-time:BeforePresent" },
      "time:numericPosition": { "@value": 2000000, "@type": "xsd:decimal" }</strong>
    }
  }
}
</pre>

### Durations

Sometimes, the temporal coverage of a Dataset is measured as a duration in time. For example, let's say the Dataset is the most recent data starting two weeks from the time the data is requested. Such a duration can be expressed as:

<pre>
{
  "@context": {
    "@vocab": "http://schema.org/",
    "time": "http://www.w3.org/2006/time",
    "geosci-time": "http://schema.geoschemas.org/contexts/temporal#"
  },
  "@type": "Dataset",
  ...
  "geosci-time:temporalCoverage": {
    "@type": "time:TemporalEntity",
    "time:hasDuration": {
      "@type": "time:Duration",
      <strong>"time:unitType": { "@id": "time:weeks" },
      "time:numericDuration": { "@value": 2, "@type": "xsd:decimal" }</strong>
    }
  }
}
</pre>

### Seasonality ###

_Seasonality should work when https://github.com/w3c/sdw/issues/1140 is completed. For now, the original idea for describing is defined below._

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
  "@context": {
    "@vocab": "http://schema.org/",
    "time": "http://www.w3.org/2006/time",
    "geosci-time": "http://schema.geoschemas.org/contexts/temporal#"
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

See: https://github.com/schemaorg/schemaorg/issues/1186#issuecomment-226838348

