# Electronic Nautical Publications

## Overview

Lists and allows downloading of all publications

# How this data is used

Save an offline copy of the PDF

# Questions we need answered

* ``pubTypeId`` groups the files, what do these numbers mean, is there an API to call to get information about them?

# Types
Currently it appears the types are as follows:

9 = List of Lights

30 = Atlas of Pilot Charts

3 = Chart No. 1

2 = American Practical Navigator

11 = Radio Navigation Aids

10 = Radar Navigation and Maneuvering Board Manual

13 = Sight Reduction Tables for Air Navigation

17 = World Port Index

14 = Sight Reduction Tables for Marine Navigation

22 = Sailing Directions Enroute

16 = USCG Light List

21 = Sailing Directions Planning Guides

7 = International Code of Signals

15 = Notice To Mariners and corrections

5 = Distances Between Ports

6 = I keep getting Forbidden for these but this is one of the titles "Pub. 940 - Fleet Guide (Atlantic) - 10th Edition 2020 (25 January 2020)"

27 = NOAA Tidal Current Tables

40 = Issue accessing the files.  One of the titles "British Admiralty - Black Sea and Sea of Azov Pilot"

26 = Forbidden; maybe tide tables?

# API

## List Nautical Publications available in storage.
https://msi.om.east.paas.nga.mil/api/publications/stored-pubs

Can be called without any parameters to get the entire list of stored publications as an array.  ``pubTypeId`` groups the files.

```
[
  ...
  {
    "pubTypeId":9,
    "pubDownloadId":3,
    "fullPubFlag":false,
    "pubDownloadOrder":1,
    "pubDownloadDisplayName":"Pub. 110 - Greenland, East Coasts of North and South America, and West Indies",
    "pubsecId":130,
    "odsEntryId":22626,
    "sectionOrder":2,
    "sectionName":"Pub110bk",
    "sectionDisplayName":"Pub 110",
    "sectionLastModified":"2021-09-16T16:29:21.656+0000",
    "contentId":16694312,
    "internalPath":"NIMA_LOL/Pub110",
    "filenameBase":"Pub110bk",
    "fileExtension":"pdf",
    "s3Key":"16694312/SFH00000/NIMA_LOL/Pub110/Pub110bk.pdf",
    "fileSize":2450198,
    "uploadTime":"2021-09-23T12:23:57.776+0000",
    "fullFilename":"Pub110bk.pdf",
    "pubsecLastModified":"2021-09-16T16:29:21.656Z"
  }
...
]
```

## Download Publications that have been stored (requires filepath key)
https://msi.om.east.paas.nga.mil/api/publications/download?key=<s3key or odsKey>&type=download

We will always use ``type=download``

## View HTML Files that have been stored (returns parsed html)
https://msi.om.east.paas.nga.mil/api/publications/download?key=<s3key or odsKey>

I don't see any html files in the list of publications, not sure what this is used for
