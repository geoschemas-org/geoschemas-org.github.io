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
* [Named Individuals](#namedindividuals)
  * [geosci-time:BeforePresent](#BeforePresent)
  * [geosci-time:BeforePresentCalibrated](#BeforePresentCalibrated)
  * [geosci-time:RadiocarbonCalibrationCurve](#RadiocarbonCalibrationCurve)
  * [geosci-time:ThousandsOfYears](#ThousandsOfYears)
  * [geosci-time:MillionsOfYears](#MillionsOfYears)
  * [geosci-time:BillionsOfYears](#BillionsOfYears)
  * [geosci-time:Uncertainty](#Uncertainty)
  * [geosci-time:UncertaintySigma](#UncertaintySigma)
  * [geosci-time:UncertaintyOlder](#UncertaintyOlder)
  * [geosci-time:UncertaintyYounger](#UncertaintyYounger)
* [Using OWL Time](#owl-time)
  * [Intervals](#intervals)
  * [Instants](#instants)
    * [Geologic Time Scales](#geologic-time-scales)
      * [Before Present](#before-present)
      * [Millions of Years](#millions-of-years)
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

[back to top](#top)
<hr/>
<a name="namedindividuals"></a>

## Named Individuals

<a name="BeforePresent"></a>
__geosci-time:BeforePresent__ - For defining the 'Before Present' (BP) temporal reference system for use in OWL-Time ([time:hasTRS](https://www.w3.org/TR/owl-time/#time:hasTRS))

Type: [time:TRS](https://www.w3.org/TR/owl-time/#time:TRS)

Temporal position expressed numerically in years before January 1, 1950 AD.

<a name="BeforePresentCalibrated"></a>
__geosci-time:BeforePresentCalibrated__ - For defining the 'Before Present Calibrated' (BP-CAL) temporal reference system for use in OWL-Time ([time:hasTRS](https://www.w3.org/TR/owl-time/#time:hasTRS))

Type: [time:TRS](https://www.w3.org/TR/owl-time/#time:TRS)

Temporal position expressed numerically in years before January 1, 1950 AD determined by carbon dating calibrated by a specific [radiocarbon calibration curve](https://en.wikipedia.org/wiki/Radiocarbon_calibration). 

<a name="RadiocarbonCalibrationCurve"></a>
__geosci-time:RadiocarbonCalibrationCurve__ - For defining the 'Radiocarbon Calibration Curve' temporal reference system for use in OWL-Time ([time:hasTRS](https://www.w3.org/TR/owl-time/#time:hasTRS)).

Type: [time:TRS](https://www.w3.org/TR/owl-time/#time:TRS)

The [radiocarbon calibration curve](https://en.wikipedia.org/wiki/Radiocarbon_calibration) used to determine the __BeforePresentCalibrated__ date. Some examples are "INTCAL99", "INTCAL04", "INTCAL09", "INTCAL13", and "INTCAL20".
 
<a name="ThousandsOfYears"></a>
__geosci-time:ThousandsOfYears__ - For defining the 'Thousands of Years' (ka) temporal reference system for use in OWL-Time ([time:hasTRS](https://www.w3.org/TR/owl-time/#time:hasTRS))

Type: [time:TRS](https://www.w3.org/TR/owl-time/#time:TRS)

Temporal position expressed numerically scaled in thousands of years (ka) increasing backwards relative to 1950 AD.

<a name="MillionsOfYears"></a>
__geosci-time:MillionsOfYears__ - For defining the 'Millions of Years' (Ma) temporal reference system for use in OWL-Time ([time:hasTRS](https://www.w3.org/TR/owl-time/#time:hasTRS))

Type: [time:TRS](https://www.w3.org/TR/owl-time/#time:TRS)

Temporal position expressed numerically scaled in millions of years (Ma) increasing backwards relative to 1950 AD or the present.

<a name="BillionsOfYears"></a>
__geosci-time:BillionsOfYears__ - For defining the 'Billions of Years' (Ga) temporal reference system for use in OWL-Time ([time:hasTRS](https://www.w3.org/TR/owl-time/#time:hasTRS))

Type: [time:TRS](https://www.w3.org/TR/owl-time/#time:TRS)

Temporal position expressed numerically scaled in billions of years (Ga) increasing backwards from the present.

<a name="GeologicTimeUnit"></a>
__geosci-time:GeologicTimeUnitAbbreviation - Geologic time unit for use in OWL-Time ([time:hasTRS](https://www.w3.org/TR/owl-time/#time:hasTRS))

Type: [time:TRS](https://www.w3.org/TR/owl-time/#time:TRS)

Standard time unit abbreviation for the age. BP, ka, Ma, Ga are used for before present, thousands of years, millions of years, and billions of years respecitively.

<a name="Uncertainty"></a>
__geosci-time:Uncertainty__ - For defining the 'Uncertainty' in a geologic age/date for use in OWL-Time ([time:hasTRS](https://www.w3.org/TR/owl-time/#time:hasTRS)).

Type: [time:TRS](https://www.w3.org/TR/owl-time/#time:TRS)

The uncertainty in the value of the geologic age in the same units as the age. Usually expressed in the literature as &pm;. One should always pair this with __UncertaintySigma__ when the sigma of the uncertainty is known.

<a name="UncertaintySigma"></a>
__geosci-time:UncertaintySigma__ - For defining the 'Uncertainty Sigma' in a geologic age/date for use in OWL-Time ([time:hasTRS](https://www.w3.org/TR/owl-time/#time:hasTRS)).

Type: [time:TRS](https://www.w3.org/TR/owl-time/#time:TRS)

The sigma of the uncertainty of the geologic age. 1 for one-sigma uncertainties, 2 for two-sigma uncertainties, etc. For easy reference, sigma values to three decimal places for uncertainties of some widely used confidence levels are: 1.645 for a 90-percent confidence level, 1.960 for a 95-percent confidence level, and 2.576 for a 99-percent confidence level. 

<a name="UncertaintyOlder"></a>
__geosci-time:UncertaintyOlder__ - For defining the 'Uncertainty Older' in a geologic age/date for use in OWL-Time ([time:hasTRS](https://www.w3.org/TR/owl-time/#time:hasTRS)).

Type: [time:TRS](https://www.w3.org/TR/owl-time/#time:TRS)

If the uncertainties of an age are not symmetric around the age value, as is usually the case when Baysean methods are used, one can specify the older and younger uncertainties of the age value. One should always pair __UncertaintyOlder__ with __UncertaintyYounger__. In addition, __UncertaintySigma__ should always be used when the sigma of the uncertainty is known.
 
<a name="UncertaintyYounger"></a>
__geosci-time:UncertaintyYounger__ - For defining the 'Uncertainty Younger' in a geologic age/date for use in OWL-Time ([time:hasTRS](https://www.w3.org/TR/owl-time/#time:hasTRS)).

Type: [time:TRS](https://www.w3.org/TR/owl-time/#time:TRS)

If the uncertainties of an age are not symmetric around the age value, as is usually the case when Baysean methods are used, one can specify the older and younger uncertainties of the age value. One should always pair __UncertaintyYounger__ with __UncertaintyOlder__. In addition, __UncertaintySigma__ should always be used when the sigma of the uncertainty is known.

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
<a name="instants"></a>

### Instants

Instants in time are useful for describing a position in time where an event occurred. For Datasets, the temporal coverage may be an instant instead of an interval for cases where all observations were made in a single point in time.

<a name="geologic-time-scales"></a>
The Geoschemas context defines 4 geologic time scales:

#### Before Present

[http://schema.geoschemas.org/contexts/temporal#BeforePresent](http://schema.geoschemas.org/contexts/temporal#BeforePresent)

Temporal position expressed numerically in years before January 1, 1950. Usually used only for radiocarbon dates.

#### Thousands Of Years

[http://schema.geoschemas.org/contexts/temporal#ThousandsOfYears](http://schema.geoschemas.org/contexts/temporal#ThousandsOfYears)

Temporal position expressed numerically scaled in thousands of years increasing backwards relative to 1950 or the date of the age determination. Abbreviation ka."

#### Millions Of Years

[http://schema.geoschemas.org/contexts/temporal#MillionsOfYears](http://schema.geoschemas.org/contexts/temporal#MillionsOfYears)

Temporal position expressed numerically scaled in millions of years increasing backwards relative to 1950 or the date of the age determination. Abbreviation Ma."

#### Billions Of Years

[http://schema.geoschemas.org/contexts/temporal#MillionsOfYears](http://schema.geoschemas.org/contexts/temporal#BillionsOfYears)

Temporal position expressed numerically scaled in millions of years increasing backwards relative to 1950 or the the date of the age determination. Abbreviation Ga."

To specify a Geologic Time Scale, we use an OWL Time Instant. The example below specifies 2.45 million years before present:

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
      "time:numericPosition": { "@value": 2450000, "@type": "xsd:decimal" }</strong>
    }
  }
}
</pre>

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
      "time:numericDuration": { "@value": 2, "@type": "xsd:decimal" }</strong>
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

