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

* Classes
* [Properties](#properties)
  * [geosci-time:temporalCoverage](#temporalCoverage)
  * [geosci-time:geologicTimeUnitAbbreviation](#geologicTimeUnitAbbreviation)
  * [geosci-time:radiocarbonCalibrationCurve](#radiocarbonCalibrationCurve)
  * [geosci-time:uncertainty](#uncertainty)
  * [geosci-time:uncertaintySigma](#uncertaintySigma)
  * [geosci-time:uncertaintyOlder](#uncertaintyOlder)
  * [geosci-time:uncertaintyYounger](#uncertaintyYounger)
* [Using OWL Time](#owl-time)
  * [Intervals](#intervals)
  * [Durations](#durations)
  * [Seasonality](#seasonality)
  
<a name="classes"></a>

## Classes

*none*

[back to top](#top)
<hr/>
<a name="properties"></a>

## Properties

<a name="temporalCoverage"></a>
__geosci-time:temporalCoverage__ - Use the [OWL-Time vocabulary](https://www.w3.org/TR/owl-time/) to describe the temporal coverage of a Dataset.

Domain: [schema:Dataset](http://schema.org/Dataset)
Range: [time:TemporalEntity](https://www.w3.org/TR/owl-time/#time:TemporalEntity)

<a name="radiocarbonCalibrationCurve"></a>
__geosci-time:radiocarbonCalibrationCurve__ - For defining the 'Radiocarbon Calibration Curve' temporal reference system for use in OWL-Time.

Domain: [time:Instant](https://www.w3.org/TR/owl-time/#time:Instant)
Range: [xsd:string](http://www.w3.org/2001/XMLSchema#string)

The [radiocarbon calibration curve](https://en.wikipedia.org/wiki/Radiocarbon_calibration) used to determine the __BeforePresentCalibrated__ date. Some examples are "INTCAL99", "INTCAL04", "INTCAL09", "INTCAL13", and "INTCAL20".

<a name="geologicTimeUnitAbbreviation"></a>
__geosci-time:geologicTimeUnitAbbreviation__ - Geologic time unit for use in OWL-Time 

Domain: [time:TemporalEntity](https://www.w3.org/TR/owl-time/#time:TemporalEntity)
Range: [xsd:string](http://www.w3.org/2001/XMLSchema#string)

Standard time unit abbreviation for the age. BP, BP-CAL, ka, Ma, Ga are used for before present, before present calibrated, thousands of years, millions of years, and billions of years respecitively.

<a name="uncertainty"></a>
__geosci-time:uncertainty__ - For defining the 'Uncertainty' in a geologic age/date for use in OWL-Time. 

Domain: [time:TemporalEntity](https://www.w3.org/TR/owl-time/#time:TemporalEntity)
Range: [xsd:decimal](http://www.w3.org/2001/XMLSchema#decimal)

The uncertainty in the value of the geologic age in the same units as the age. Usually expressed in the literature using the symbol ± before the value. One should always pair this with __UncertaintySigma__ when the sigma of the uncertainty is known.

<a name="uncertaintySigma"></a>
__geosci-time:uncertaintySigma__ - For defining the 'Uncertainty Sigma' in a geologic age/date for use in OWL-Time.

Domain: [time:TemporalEntity](https://www.w3.org/TR/owl-time/#time:TemporalEntity)
Range: [xsd:decimal](http://www.w3.org/2001/XMLSchema#decimal)

The sigma of the uncertainty of the geologic age. 1 for one-sigma uncertainties, 2 for two-sigma uncertainties, etc. For easy reference, sigma values to three decimal places for uncertainties of some widely used confidence levels are: 1.645 for a 90-percent confidence level, 1.960 for a 95-percent confidence level, and 2.576 for a 99-percent confidence level. 

<a name="uncertaintyOlder"></a>
__geosci-time:uncertaintyOlder__ - For defining the 'Uncertainty Older' in a geologic age/date for use in OWL-Time.

Domain: [time:TemporalEntity](https://www.w3.org/TR/owl-time/#time:TemporalEntity)
Range: [xsd:decimal](http://www.w3.org/2001/XMLSchema#decimal)

If the uncertainties of an age are not symmetric around the age value, as is usually the case when Baysean methods are used, one can specify the older and younger uncertainties of the age value. One should always pair __uncertaintyOlder__ with __uncertaintyYounger__. In addition, __uncertaintySigma__ should always be used when the sigma of the uncertainty is known.
 
<a name="uncertaintyYounger"></a>
__geosci-time:uncertaintyYounger__ - For defining the 'Uncertainty Younger' in a geologic age/date for use in OWL-Time.

Domain: [time:TemporalEntity](https://www.w3.org/TR/owl-time/#time:TemporalEntity)
Range: [xsd:decimal](http://www.w3.org/2001/XMLSchema#decimal)

If the uncertainties of an age are not symmetric around the age value, as is usually the case when Baysean methods are used, one can specify the older and younger uncertainties of the age value. One should always pair __uncertaintyYounger__ with __uncertaintyOlder__. In addition, __uncertaintySigma__ should always be used when the sigma of the uncertainty is known.

[back to top](#top)

<hr/>
<a name="owl-time"></a>

## Using OWL Time

The [OWL Time](https://www.w3.org/TR/owl-time/) vocabulary defines useful ways for describing the temporal coverage. The temporalCoverage of a Dataset indicates the period of time that the contents of the dataset apply. This extension to schema:Dataset allows for the description of temporal coverages that cannot be described using a ISO 8601 formatted date (and time). Some examples of such coverages are geologic time scales, seasonal coverages across multiple years, or certain days of the week. The coverage is expressed as a time:TemporalEntity, typcially a time:Interval or a time:Instant.
[OWL Time in RDF Turtle](http://www.w3.org/2006/time#)

![https://www.w3.org/TR/owl-time/](https://www.w3.org/TR/owl-time/images/TemporalEntity.png)

[back to top](#top)
<hr/>
<a name="intervals"></a>

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
[back to top](#top)
<hr/>
<a name="durations"></a>

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
      "time:numericDuration": { "@value": 2.0, "@type": "xsd:decimal" }</strong>
    }
  }
}
</pre>

[back to top](#top)
<hr/>
<a name="seasonality"></a>

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

