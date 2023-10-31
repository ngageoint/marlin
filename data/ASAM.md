# ASAM

## Overview

(ASAM) include the locations and descriptive accounts of specific hostile acts against ships and mariners and may be useful for recognition, prevention and avoidance of potential hostile activity.

# Is it mappable?

Yes.  ``latitude`` and ``longitude`` fields.

# How this data is used

Show it on the map.

# Questions we need answered

# API

* why do we have to include both minOccurDate and maxOccurDate? why can't we provide just minOccurDate in the /api/publications/asam route?

## Anti-shipping Activity Messages (ASAM) database queries
https://msi.om.east.paas.nga.mil/api/publications/asam?sort=date&output=json

```
{
  "asam": [
    {
      "reference": "2021-302",
      "date": "2021-12-19",
      "latitude": 1.2333333330890355,
      "longitude": 104.04999999997807,
      "position": "1°14'00\"N \n104°03'00\"E",
      "navArea": "XI",
      "subreg": "71",
      "hostility": "Boarding",
      "victim": "Hong Kong-flagged bulk carrier SEACON 8",
      "description": "INDONESIA: On 19 December, at 0020 local time, four robbers boarded the Hong Kong-flagged bulk carrier SEACON 8 underway in the eastbound lane of the Singapore Strait Traffic Separation Scheme (TSS), near position 01-14N 104-03E. The alarm was raised, and the crew mustered. A subsequent search of the ship did not find any of the perpetrators still onboard. The master reported that nothing was stolen and that all crew were safe. The ship resumed her voyage following the search."
    },
    ...
```

## Anti-shipping Activity Messages (ASAM) navigation areas and sub regions
https://msi.om.east.paas.nga.mil/api/publications/asam/areas

Useless.

```
{
  "navAreas": [
    {
      "roman": "I",
      "int": "1"
    },
    {
      "roman": "II",
      "int": "2"
    },
    ...
```