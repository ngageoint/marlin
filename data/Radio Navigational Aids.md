# Radio Navigational Aids

## Overview

Radio Navigational Aids (NGA Pub. 117) contains detailed lists of worldwide stations providing radio and electronic services used in marine navigation, including:
* Radio Direction Finder (RDF) and Radar Stations
* Radio Time Signal Stations
* Navigational Warning Broadcast Stations
* Distress, Emergency, and Safety Traffic Broadcast Stations
* Medical Advice Communication Stations
* Long Range Navigational Aids

All bearings are true and are measured in degrees clockwise from 000° (true north) to 359°. The sectors of radio direction finder stations are given as looking from the station to seaward in accordance with international practice; it should be noted that this is the reverse of the method used in the light lists for expressing the sectors of lights.

# Is it mappable?

DFRS are mappable via the ``txPosition`` property.
Time Signals only present an area not a specific location.
Warnings only present an area not a specific location.

# API Quirks

Some of the data contains text saying "(See below)" e.g. `system`: "(See below)", which works great in the book this data came from, not so much in API.

# API

## List NGA Country IDs for RNAids by Chapter
https://msi.om.east.paas.nga.mil/api/publications/radio-navaids/areas

This returns an object with the keys ``warn``, ``dfrs``, and ``ts`` which are arrays of arrays that look like this:

```
{
  "warn": [
    [
      "FAROE ISLANDS",
      19
    ],
    [
      "NORWAY",
      23
    ]
  ],
  "dfrs": [
    [
      "AUSTRALIA",
      26
    ],
    ...
  ],
  "ts": [
    [
      "CANADA",
      2
    ],
    ...
  ]
```

## Chapter 1 - Radio Direction Finder & Radar Stations Database Queries
https://msi.om.east.paas.nga.mil/api/publications/radio-navaids/dfrs?output=json

Returns an array of Radio Direction Finder & Radar Stations

```
{
  "radio-navaids": [
    {
      "stationNo": "1001.0",
      "stationName": "Cap-aux-Meules.",
      "stationType": "RDF",
      "rxPosition": " \n",
      "txPosition": "47°23'14\"N \n61°51'40\"W",
      "frequency": "",
      "range": null,
      "procedureText": null,
      "remarks": "MCTS Riviere-au-Renard (VCG).",
      "notes": "",
      "areaName": "CANADA"
    },
    ...
  ]
}
```

# Get Area Notes for Chapter 1
https://msi.om.east.paas.nga.mil/api/publications/radio-navaids/dfrs/areas

Returns an object with a key of ``areas`` which is an array of arrays, which has some almost duplicates.

These are used to provide a note above the areaName specified in the array
The array is tructured as follows:
[areaName, ?, commonInstructionsForArea, ?, stationNote]

The header for an area will be:

commonInstructionsForArea

stationNote1

stationNote2

....

stationNoteN

```
{
  "areas": [
      ...
    [
      "CANADA",
      30,
      "The VHF direction finding stations of Canada are for emergency use only. All stations are remotely controlled by a Marine Communications and Traffic Services Center (MCTS). The following details of operation are common to all of these stations:",
      3,
      "C. Ch.16 (distress only)."
    ],
    [
      "CANADA",
      30,
      "The VHF direction finding stations of Canada are for emergency use only. All stations are remotely controlled by a Marine Communications and Traffic Services Center (MCTS). The following details of operation are common to all of these stations:",
      1,
      "A. Ch.16."
    ],
    ...
  ]
}
```

# List all Station Names for Radio Navigation Aids
https://msi.om.east.paas.nga.mil/api/publications/radio-navaids/stations

This returns an object with the keys ``warn``, ``dfrs``, and ``ts`` which are arrays of strings.  Not sure what we would use these for since there is no way to map these to anything else.

```
{
  "warn": [
    "Torshavn (OXJ).",
    "Floro (LGL)."
  ],
  "dfrs": [
    "Die Elbe.",
    "Pointe Heath.",
    ...
  ],
  "ts": [
    ...
  ]
}
```

# Chapter 2 - Radio Time Signals Database Queries
https://msi.om.east.paas.nga.mil/api/publications/radio-navaids/ts?output=json

This returns the time signals items.  Unsure how these are used in real life.

Per Ed Stacy and Chris Janus: these are not used by real people

```
{
  "radio-navaids": [
    {
      "stationNo": 2020,
      "stationName": "Ottawa, Ont. (CHU).",
      "hours": "Continuous.",
      "system": "(See below)",
      "frequency": "3330 kHz, A2A, H3E, 3 kW;\n7850 kHz, A2A, H3E, 10 kW;\n14670 kHz, A2A, H3E, 3 kW.",
      "fNote": "DUT1: Marked seconds indicated by split pulses.\nSYSTEM: 00s.: 500ms second marker. From 01s. to 28s.: second markers of 300ms each, 1000 Hz tone. 29s.: silence. From 30s. to 50s.: second markers of 300ms each, 1000 Hz tone. From 51s. to 59s.: station identification and time (UTC) in English and French. At the beginning of the hour the first second marker lasts for 1s. and 500ms markers for seconds 01 to 09 are omitted. A binary time code is included in second markers 31-39.",
      "areaName": "CANADA"
    },
    ...
  ]
}
```

# Chapter 3 - Radio Navigational Warnings Database Queries
https://msi.om.east.paas.nga.mil/api/publications/radio-navaids/warn?output=json

This returns the warnings items.  Unsure how these are used in real life.  There also only appears to be 3.

```
{
  "radio-navaids": [
    {
      "stationNo": 3215,
      "stationName": "Torshavn (OXJ).",
      "frequency": "1641 kHz, A3E, Ch. 23, 24, 25, 26, F3E.",
      "times": "Every even hour +35m.",
      "broadcastNature": "Local navigational warnings and weather.",
      "areaName": "FAROE ISLANDS"
    },
    {
      "stationNo": 3251,
      "stationName": "Floro (LGL).",
      "frequency": "1680 kHz, J3E, Ch. 03, 20, 23, 27, 65, 78, G3E.",
      "times": "0233, 0633, 1033, 1433, 1833, 2233.",
      "broadcastNature": "Local navigational warnings and weather (ice on request).",
      "areaName": "NORWAY"
    },
    {
      "stationNo": 3251,
      "stationName": "Floro (LGL).",
      "frequency": "1680 kHz, J3E.",
      "times": "1215, 2315.",
      "broadcastNature": "Weather.",
      "areaName": "NORWAY"
    }
  ]
}
```
