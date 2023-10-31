# MODU

## Overview

(MODU) includes drilling vessels, semisubmersibles, submersibles, jack-ups, and similar facilities that can be moved without substantial effort.

# Is it mappable?

Yes.  ``latitude`` and ``longitude`` fields.

# How this data is used

Show it on the map.

# Questions we need answered

* Is the name the primary key which we can use to track when they move?

# API

## MODU database queries
https://msi.om.east.paas.nga.mil/api/publications/modu?output=json

```
{
  "modu": [
    {
      "name": "590021",
      "date": "2021-04-16",
      "rigStatus": "Active",
      "specialStatus": "Specific Berth Requested",
      "distance": 0.3,
      "latitude": 53.23333333300002,
      "longitude": 3.241666667000004,
      "position": "53°14'00\"N \n3°14'30\"E",
      "navArea": "HYDROLANT",
      "region": 3,
      "subregion": 37
    },
    ...
```

## MODU sub regions
https://msi.om.east.paas.nga.mil/api/publications/modu/areas

Useless.

```
{
  "subregions": [
    11,
    14,
    23,
    24,
    28,
    35,
    ...
```