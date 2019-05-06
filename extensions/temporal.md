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

The [OWL Time](https://www.w3.org/TR/owl-time/) vocabulary defines useful ways for describing the temporal coverage.

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

