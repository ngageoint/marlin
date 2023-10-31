# Notice To Mariners

## Overview

The US Notice to Mariners provides timely marine safety information for the correction of all US Government navigation charts and publications from a wide variety of sources, both foreign and domestic. To ensure the safety of life at sea, the information published in the Notice to Mariners is designed to provide for the correction of unclassified nautical charts.

The US Notice to Mariners corrects NGA and NOS charts using information collected from many sources, among them the Local Notice to Mariners published by the nine US Coast Guard Districts. The US Notice to Mariners will contain only those chart corrections of interest to ocean-going vessels.

# Is it mappable?

No.  Not really sure what to do with any of these as they are just corrections to existing products.

# API

## Get Chartlets, Depth Tabs, Notes file mapping CSV
https://msi.om.east.paas.nga.mil/api/publications/cdn_filename_mapping?output=json

Not sure what this is used for...

```
{
  "cdn-filename-mapping": [
    {
      "noticeNumber": 197751,
      "cdnFileName": "N804037_197751_U.jpg"
    },
    ...
  ]
}
```

## List all available Unclassifed Notice to Mariners (NTM) Notice Numbers with available publications
https://msi.om.east.paas.nga.mil/api/publications/ntm/ls-notice-numbers

Returns an array of notice numbers.  Maybe query to find new ones?

```
{
  "notice_numbers": [
    "22/2022",
    "21/2022",
    "20/2022",
    ...
  ]
}
```

## List All Notice Numbers between [min] and [max]
https://msi.om.east.paas.nga.mil/api/publications/ntm/notice-numbers-between


Returns an array of notice numbers.  Maybe query to find new ones?  This call takes a minNoticeNumber and maxNoticeNumber as query parameters.  Note the different format from the previous api call

```
{
  "notice_numbers": [
    "202222",
    "202221",
    "202220",
    ...
  ]
}
```

## Available Corrections for NGA List of Lights
https://msi.om.east.paas.nga.mil/api/publications/ntm/ntm-available-corr

Just an array of the list of lights pulications and the last correction for the particular publication.

```
{
  "availCorr": [
    {
      "pubTypeId": 16,
      "pubName": "USCG Light List",
      "volumeName": "Atlantic Coast (St. Croix River, Maine to Shrewsbury River, New Jersey)",
      "volumeNumber": "I",
      "editionYear": "2020",
      "dbLastNotice": 202004,
      "lastNotice": "04/2020"
    },
    ...
  ]
}
```

# NTM Chart Corrections Database Queries
https://msi.om.east.paas.nga.mil/api/publications/ntm/ntm-chart-corr

This API call just hangs...

# NTM Chart Corrections (Geographic Area Search)
https://msi.om.east.paas.nga.mil/api/publications/ntm/ntm-chart-corr/geo

This returns a 503

```
{
  "timestamp": "2022-05-20T20:55:54.914+0000",
  "status": 500,
  "error": "Internal Server Error",
  "message": "could not extract ResultSet; SQL [n/a]; nested exception is org.hibernate.exception.SQLGrammarException: could not extract ResultSet",
  "path": "/api/publications/ntm/ntm-chart-corr/geo"
}
```

# NTM Charts Affected Database Queries
https://msi.om.east.paas.nga.mil/api/publications/ntm/ntm-chart-corr

This API call takes forever

```
{
  "chartsAff": [
    {
      "chartId": 1572,
      "chartNumber": "10",
      "correctionType": null,
      "noticeNumber": 199628,
      "edition": "2",
      "region": "10",
      "subregion": "10",
      "portCode": null,
      "actionCode": "NEW EDITION",
      "priceCategory": "D",
      "noticeYear": 1996,
      "noticeWeek": 28
    },
    ...
  ]
}
```

# NTM Chartlets/Depth Tabs/Notes Graphics Database Queries
https://msi.om.east.paas.nga.mil/api/publications/ntm/ntm-graphics?subregion=10

This is a subregion query.

Not sure what to do with this

```
{
  "ntmGraphics": [
    {
      "chartNumber": "106",
      "priceCategory": "D",
      "subregion": 10,
      "noticeNumber": 198544,
      "noticeYear": 1985,
      "noticeWeek": 44,
      "graphicType": "Chartlet",
      "seqNum": 1,
      "fileName": "C106_198544_U.jpg",
      "fileSize": "564270"
    },
    ...
  ]
}
```

# NTM Hydrographic Products Corrections Database Queries
https://msi.om.east.paas.nga.mil/api/publications/ntm/ntm-hydro-corr?subregion=11&output=json

This is a subregion query.

Not sure what to do with this

```
{
  "hydroCorr": [
    {
      "noticeNumber": 202004,
      "seriesStockNumber": "11ACO11300",
      "nationalStockNumber": "7642014010097",
      "prodNumber": "11300",
      "region": "1",
      "subRegion": 11,
      "productType": "charts",
      "noticeYear": 2020,
      "noticeWeek": 4,
      "title": [
        {
          "insetTitle": "Galveston to Rio Grande",
          "insetScale": "460,732",
          "changeIndicator": {
            "col1Updated": false,
            "col2Updated": false,
            "col3Updated": false,
            "col4Updated": true,
            "col5Updated": true,
            "col6Updated": false
          }
        }
      ],
      "titleGroup": "Galveston to Rio Grande Scale: 460,732\n",
      "edition": "45",
      "editionDate": "12/19",
      "priceCategory": "NOS"
    },
    ...
  ]
}
```

# NTM Navigation Publication Corrections Database Queries
https://msi.om.east.paas.nga.mil/api/publications/ntm/ntm-nav-pub-corr?output=json

```
{
  "navPubCorr": [
    {
      "publicationTypeGroup": "Coast Pilot",
      "publicationTypeSubGroup": "Edition 50",
      "publicationNumber": "1",
      "publicationName": "United States Coast Pilot",
      "volumeNumber": null,
      "editionNumber": 50,
      "editionYear": "2020",
      "noticeYear": 2020,
      "noticeWeek": 11,
      "filename": "38445202011"
    },
    ...
  ]
}
```

# NTM Pubs Affected Database Query
https://msi.om.east.paas.nga.mil/api/publications/ntm/ntm-pubs-affected?output=json

```
{
  "pubsAff": [
    {
      "publicationId": 39065,
      "pubGroup": "Almanacs",
      "publicationName": "Air Almanac",
      "pubOrVolNumber": "AIR ALMANAC",
      "edition": "2021",
      "noticeNumbers": "36/20*"
    },
    ...
  ]
}
```

# List All NTM Publications Stored
https://msi.om.east.paas.nga.mil/api/publications/ntm/pubs?noticeWeek=11&noticeYear=2020&output=json

This query is for a week and year.  Not sure if we can request all at once.

```
{
  "pubs": [
    {
      "publicationIdentifier": 38385,
      "noticeNumber": 202011,
      "title": "Front Cover",
      "odsKey": "16694429/SFH00000/UNTM/202011/Front_Cover.pdf",
      "sectionOrder": 20,
      "limitedDist": false,
      "odsEntryId": 24637,
      "odsContentId": 16694429,
      "internalPath": "UNTM/202011",
      "filenameBase": "Front_Cover",
      "fileExtension": "pdf",
      "fileSize": 62781,
      "isFullPublication": false,
      "uploadTime": "2020-03-05T19:17:05.204+0000",
      "lastModified": "2020-03-05T19:17:05.204Z"
    },
    ...
  ]
}
```