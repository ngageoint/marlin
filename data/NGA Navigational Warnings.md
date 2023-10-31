# NGA Navigational Warnings

## Overview

In support of the Global Maritime Distress and Safety System (GMDSS), Broadcast Warnings are promulgated by the Worldwide Navigational Warnings Service (WWNWS) to provide rapid dissemination of information critical to navigation and the safety of life at sea.

Navigational Warnings are issued regularly and contain information about persons in distress, or objets and events that pose an immediate hazard to navigation.

The five types of Navigation Warnings: NAVAREA IV, HYDROLANT, HYDROARC, NAVAREA XII, and HYRDOPAC are categorized by their location. As of 26 January 2017, maritime security alerts and advisories are issued by the US Maritime Advisory System, replacing Special Warnings and MARAD Advisories.

Also Known As Broadcast Warnings.

# Is it mappable?

Some of the navigation warnings are not mappable at all.  Some of them could be easily mapped to a ``subregion``, since that is a property in the JSON.  A lot of them have locations, either points, lines or polygons, but the features are embedded in the ``text`` property and would need to be parsed.

# How this data is used

People on ships would normally get these warnings, look at them and determine if they needed to plot them.  If so they would.  These warnings could be plotted in different colors based on the urgency of the message, which is subjective.

We should allow the warnings to be sectioned by nav area, with the current nav area at the top by default.

# Questions we need answered

* is the ``text`` parameter formatted according to some spec?
* what is ``status``?
* Does NGA have something that can parse this into something useful? They do provide a KML file which seems to indicate there can be some parsing
* are there standard words in the text which would allow us to show the data in different ways?

# API

It appears there are new, in force, and cancelled warnings.

## Quirks
* Date formats in here are https://en.wikipedia.org/wiki/Date-time_group
  * DDHHMMSSZmmmYY - Full time (used for software timestamps)
  * DDHHMMZmmmYY - shortened time (used e.g. for timestamps manually written)
  * DDHHMMZ - short time (e.g. used for planning)

Some navigation warnings are not mappable:
```
{
  "broadcast-warn": [
    {
      "msgYear": 2020,
      "msgNumber": 947,
      "navArea": "P",
      "subregion": "GEN",
      "text": "201616Z MAR 20\nNGA MARITIME SAFETY OFFICE STATUS AND SUPPORT.\nCOVID-19 UPDATE.\n 1. NGA IS EXECUTING A MISSION CRITICAL POSTURE\n    FOR MANNING AND SUPPORT DURING THE COVID-19\n    PANDEMIC. NGA WILL MAINTAIN THE REQUISITE\n    STAFFING AND CAPACITY TO OPERATE THE 24/7\n    NAVSAFETY WATCH, PUBLISH THE WEEKLY NOTICE\n    TO MARINERS AND PROVIDE DNC CRITICAL\n    CORRECTIONS.\n 2. ALL OTHER SERVICES AND PRODUCTS WILL BE\n    SUPPORTED ON A CASE BY CASE BASIS AS MISSION\n    NEEDS DICTATE.\n 3. NGA REMAINS ACCESSIBLE THROUGH ITS NORMAL\n    POINTS OF CONTACT.\n 4. FOR URGENT SERVICE, CONTACT NGA NAVSAFETY,\n    DSN: 547 5455,\n    COMM: 800 362 6289 OR 571 557 5455,\n    E-MAIL: NAVSAFETY@NGA.MIL OR\n    MSG TO NGA NAVSAFETY WASHINGTON DC.\n",
      "status": "A",
      "issueDate": "201628Z MAR 2020",
      "authority": "SFH 201459Z MAR 20.",
      "cancelDate": null,
      "cancelNavArea": null,
      "cancelMsgYear": null,
      "cancelMsgNumber": null,
      "year": 2020,
      "area": "P",
      "number": 947
    }
  ]
}
```

## Query Database for Navigational Warnings
https://msi.om.east.paas.nga.mil/api/publications/broadcast-warn?output=json

```
{
  "broadcast-warn": [
    {
      "msgYear": 2022,
      "msgNumber": 469,
      "navArea": "4",
      "subregion": "24",
      "text": "CARIBBEAN SEA.\nCOLOMBIA.\nF/V SANTO AMARO II , WHITE AND RED HULL,\nFIVE PERSONS ON BOARD, UNREPORTED.\nLAST KNOWN POSITION IN 12-27.00N 071-14.00W.\nVESSELS IN VICINITY REQUESTED TO KEEP A\nSHARP LOOKOUT, ASSIST IF POSSIBLE.\nREPORTS TO ANY COASTAL RADIO STATION.\n",
      "status": "A",
      "issueDate": "160029Z MAY 2022",
      "authority": "COLOMBIA 153/22 160001Z MAY 22.",
      "cancelDate": null,
      "cancelNavArea": null,
      "cancelMsgYear": null,
      "cancelMsgNumber": null,
      "year": 2022,
      "area": "4",
      "number": 469
    },
    ...
```

## List Most Recent Warning Messages for Broadcast Warnings
https://msi.om.east.paas.nga.mil/api/publications/broadcast-warn/current-warnings

Array of arrays defined as [navArea, msgNumber, msgYear, subRegion, text, issueDate]

```
Response body
Download
[
  [
    "4",
    469,
    2022,
    "24",
    "CARIBBEAN SEA.\nCOLOMBIA.\nF/V SANTO AMARO II , WHITE AND RED HULL,\nFIVE PERSONS ON BOARD, UNREPORTED.\nLAST KNOWN POSITION IN 12-27.00N 071-14.00W.\nVESSELS IN VICINITY REQUESTED TO KEEP A\nSHARP LOOKOUT, ASSIST IF POSSIBLE.\nREPORTS TO ANY COASTAL RADIO STATION.\n",
    "160029Z MAY 2022"
  ],
  [
    "12",
    316,
    2022,
    "GEN",
    "1. NAVAREA XII WARNINGS IN FORCE AS OF 131450Z MAY.\n   ALL THE INFORCE WARNINGS ARE LISTED HERE.\n   315/22, 314/22, 312/22, 309/22, 305/22, 302/22,\n   297/22, 294/22, 278/22, 277/22, 276/22, 244/22,\n   243/22, 219/22, 183/22, 166/22, 165/22, 162/22,\n   111/22.\n   729/21, 621/21, 472/21, 340/21, 339/21, 269/21,\n   145/21, 144/21, 143/21.\n2. THE COMPLETE TEXT OF ALL IN-FORCE NAVAREA XII\n   BROADCAST WARNINGS ARE AVAILABLE ON THE NGA\n   MARITIME SAFETY INFORMATION WEBSITE AT:\n   MSI.NGA.MIL/NAVWARNINGS.\n   ALTERNATIVELY, THESE MAY BE REQUESTED BY E-MAIL\n   FROM THE NAVAREA XII COORDINATOR AT\n   NAVSAFETY@NGA.MIL.\n3. CANCEL NAVAREA XII 250/22, 289/22, 301/22.\n",
    "131411Z MAY 2022"
  ],
```

## List all current In-Force Warning Numbers
https://msi.om.east.paas.nga.mil/api/publications/broadcast-warn/inforce

JSON object with location names as keys with an array of "``msgNumber``/``msgYear``" strings

```
{
  "HYDROLANT": [
    "1287/2022",
    "1285/2022",
    ....
```

## /api/publications/broadcast-warn/navareas
https://msi.om.east.paas.nga.mil/api/publications/broadcast-warn/navareas

Unnecessary for our app I think

```
{
  "NAVAREA IV": "4",
  "HYDROLANT": "A",
  "NAVAREA XII": "12",
  "HYDROPAC": "P",
  "HYDROARC": "C"
}
```

## List Subregion Values for Broadcast Warnings
https://msi.om.east.paas.nga.mil/api/publications/broadcast-warn/subregions

Unnecessary for our app I think

```
[
  11,
  12,
  13,
  14,
...
]
```