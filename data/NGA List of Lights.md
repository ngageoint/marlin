# NGA List of Lights

## Overview

Contains List of Lights, Radio Aids and Fog Signals published as 7 volumes once a year as PDFs.  Corrections are published in the Notice to Mariners.  The 7 volumes, numbered 110 -> 116 correspond to areas of the world.  These areas are generally: 110 - western half of the Atlantic ocean north to south; 111 - Pacific ocean including around Australia, excluding the eastern coast of Asia; 112 - Indian Ocean; 113 - Eastern half of the Atlantic Ocean from the south pole to the southern tip of England; 114 - Area around the British Islands; 115 - Arctic ocean from eastern tip of Russia to Greenland excluding area north of the US/Canada; 116 - Baltic Sea

These features are for use as navigational aids.

Could be 1 of either a Light, Bouy, RACON (Radar Beacon) or RAMARK (? TODO)

Also in the API are Differential GPS stations which elminates errors in a GPS reciever to enhance the accuracy level.

When there are sectors defined for the light colors, 0 is at the bottom of the circle and goes around clockwise.

# Is it mappable?

All three data sources offered by this API (Lighted Aids, Radio Beacons, and Differential GPS Stations) are mappable.

# Questions

* If we query for all lights, do we get the most recent position of the light, or do we get all previous positions as well and we need to only use the latest one based on noticeWeek and noticeYear?

# API

## List All Geographic Header and Sub-Header Values for NGALOL
https://msi.om.east.paas.nga.mil/api/publications/ngalol/areas

Returns an array of Locations and what publication they exist in.  Might be useful for searching by place

```
[
  [
    "TOGO",
    "RADE DE LOME:",
    "PUB 113"
  ],
```

## List Geographic Header Values By Volume in NGALOL
https://msi.om.east.paas.nga.mil/api/publications/ngalol/areasByVolume

Returns an array of locations and what publication the exist in for each type of data in the ngalol api.  Might be useful for searching by place

```
{
  "lights-buoys": [
    [
      "PUB 110",
      "GREENLAND",
      4399
    ],
```

# List of Lights 
https://msi.om.east.paas.nga.mil/api/publications/ngalol/lights-buoys?includeRemovals=false&output=json

Returns
```
{
  "ngalol": [records]
}
```

## Columns Displayed in PDF and Query Page

### Number
U.S. assigned number to the feature potentially along with an international number presented on a separate line in italics

#### JSON
This means NGA number 4 and international number L5000

``featureNumber: "4\nL5000"``

### Name & Location
Name and descriptive location. - or -- is used to reduce repition of principal geographic name.  Bold faced = lights intended for landfall or > 15 miles of visibility; Italics = Floating aids; Capital Italics = Lightships and LANBYs (? TODO)

#### JSON
``name: "-Outer."``

### Position
Latitude Longitude of feature to nearest tenth of a minute

#### JSON
``position: "65°35'32.1\"N \n37°34'08.9\"W"``

### Characteristic
Characteristic of the feature; uses the abbreviations to shorten the text.  The following JSON means Flashing White light with a period of 5 seconds, 1 second on 4 seconds off.  For Radiobeacons this field has the More code, period in seconds, length of transmission and silence time

#### JSON
``characteristic: "Fl.W.\nperiod 5s \nfl. 1.0s, ec. 4.0s \n"``

### Height
Height of the feature in feet on the first line and meters on the second.  The following JSON is 36 feet which is also 11 meters

#### JSON
``heightFeetMeters: "36\n11"``

### Range
The distance, expressed in nautical miles, that a light can be seen in clear weather or that a RACON or RAMARK can be received.

#### JSON
``range: "7"``

### Structure
Description of the structure and its height in feet measured from the top of the structure to the ground. Note–Stripes are vertical. Bands are horizontal. The use of the term “diagonal stripes” is the exception.

#### JSON
``structure: "Yellow pedestal, red band; 7.\n"``

### Remarks
Remarks about the feature, could indicate light color directions or other pertinant information

#### JSON
``remarks: "(3 & 10cm).\n"``

## JSON Example
``` 
{
aidType: "Lighted Aids",
charNo: 1,
characteristic: "Fl.W.\nperiod 5s \nfl. 1.0s, ec. 4.0s \n",
deleteFlag: "Y",
featureNumber: "4\nL5000",
geopoliticalHeading: "GREENLAND",
heightFeetMeters: "36\n11",
localHeading: null,
name: "-Outer.",
noticeNumber: 201507,
noticeWeek: "07",
noticeYear: "2015",
position: "65°35'32.1\"N \n37°34'08.9\"W",
postNote: null,
precedingNote: null,
range: "7",
regionHeading: "ANGMAGSSALIK:",
remarks: null,
removeFromList: "N",
structure: "Yellow pedestal, red band; 7.\n",
subregionHeading: null,
volumeNumber: "PUB 110"
}
```

## API Quirks

It appears that when requesting an output of `html` the ``geopoliticalHeading`` is populated for all results, however the ``regionHeading`` is only populated for the first result in the list for that region.

2472
G 1425
-Segunda Angostura. 52° 44.1´ S
70° 10.9´ W
Fl.W.
period 10s
fl. 0.7s, ec. 9.3s
66
20
9 White octagonal concrete tower,
red band; 20.
Visible 086°-278°.
-RACON M(– –)
period 48s
fl. 3s, ec. 45s
1

light in PUB111 has three chracteristics, but only 2 real ones

### Primary Key
The primary key is volumeNumber + featureNumber + charNo

A single structure could have different characteristics which are indicated by the charNo.  These different characteristics should be combined into one map feature and one detail feature showing all different characteristics.

For Example this light house has a light and a radar beacon:
```
{
      "volumeNumber": "PUB 110",
      "aidType": "Lighted Aids",
      "geopoliticalHeading": "GREENLAND",
      "regionHeading": null,
      "subregionHeading": null,
      "localHeading": null,
      "precedingNote": null,
      "featureNumber": "8\nL5100",
      "name": "Prins Christians Sund.",
      "position": "60°03'31.4\"N \n43°09'27.4\"W",
      "charNo": 1,
      "characteristic": "Fl.W.R.G.\nperiod 5s \nfl. 1.0s, ec. 4.0s \n",
      "heightFeetMeters": "295\n90",
      "range": "W. 14 \nR. 11 \nG. 11",
      "structure": "Orange tower; 15.\n",
      "remarks": "W. 000°-180°, R.-255°, G.-263°, W.-288°, R.-295°, G.-000°.\n",
      "postNote": null,
      "noticeNumber": 201507,
      "removeFromList": "N",
      "deleteFlag": "Y",
      "noticeWeek": "07",
      "noticeYear": "2015"
    },
    {
      "volumeNumber": "PUB 110",
      "aidType": "Lighted Aids",
      "geopoliticalHeading": "GREENLAND",
      "regionHeading": null,
      "subregionHeading": null,
      "localHeading": null,
      "precedingNote": null,
      "featureNumber": "8\nL5100",
      "name": "RACON",
      "position": "60°03'31.4\"N \n43°09'27.4\"W",
      "charNo": 2,
      "characteristic": "T(- )\nperiod 60s \n",
      "heightFeetMeters": null,
      "range": null,
      "structure": null,
      "remarks": "(3 & 10cm).\n",
      "postNote": null,
      "noticeNumber": 201507,
      "removeFromList": "N",
      "deleteFlag": "Y",
      "noticeWeek": "07",
      "noticeYear": "2015"
    },
```

## Abbreviations

### Countries

Where lights of different countries intermingle in the list they are distinguished by the following letters:
(A.) Argentina (Hon.) Honduras
(Aus.) Australia (M.) Mexico
(C.) Chile (Nic.) Nicaragua
(Can.) Canada (N.Z.) New Zealand
(Col.) Columbia (P.) Panama
(C.R.) Costa Rica (Sal.) El Salvador
(F.) France (U.K.) United Kingdom
(Gu.) Guatemala (U.S.) United States

### Other
Other abbreviations:
Al.—alternating 
lt.—lit
bl.—blast 
Mo.—Morse code
Bu.—blue 
min.—minute
Dir.—directional 
obsc.—obscured
ec.—eclipsed 
Oc.—occulting
ev.—every 
Or.—orange
F.—fixed 
Q.—quick flashing
Fl.—flashing 
R.—red
fl.—flash 
s.—seconds
G.—green 
si.—silent
horiz.—horizontal 
U.Q.—ultra quick
flashing 
intens.—intensified
I.Q.— interrupted quick
flashing
 unintens.—unintensified
 vert.—vertical
Iso.—isophase 
Vi.—violet
I.V.Q.—interrupted very
quick flashing
vis.—visible
V.Q.— very quick
Km.— kilometer flashing
(0.62137 mile) 
W.—white
L.Fl.—long flashing 
Y.—yellow 

# Radio Beacons
https://msi.om.east.paas.nga.mil/api/publications/ngalol/radiobeacons?includeRemovals=false&output=json

Returns
```
{
  "ngalol": [records]
}
```

## Columns Displayed in PDF and Query Page

### Number
U.S. assigned number to the feature

#### JSON
This means NGA number 4 and international number L5000

``featureNumber: 240``

### Name & Location
Name and/or descriptive location

#### JSON
``name: "Natashquan, Que."``

### Position
Latitude Longitude of feature to nearest tenth of a minute (this is not true based on the following returned from the API)

#### JSON
``position: "50°13'23.99\"N \n61°50'36\"W"``

### Characteristic
This field has the Morse code, period in seconds, length of transmission and silence time

#### JSON
``characteristic: "G\n(- - • ).\nperiod 360s\ntr(3) 60s\nsi 120s\nrepeats(1) 180s"``

### Range
The distance in nautical miles

#### JSON
``range: "7"``

### Sequence
Group sequence. Selected radiobeacons are grouped together on the same operating frequency and are assigned a specific sequence of transmission within this group.

#### JSON
``sequenceText: "III, VI"``

### Frequency
Frequency (given in kilohertz) and amplitude modulation (see Table Symbols).

#### JSON
``frequency: "343\nNON, A2A."``

### Remarks
Remarks. Transmission synchronization, type
of radiobeacon (marine, aero, etc.), calibration, antenna lead-in, calling frequencies, distance-finding information, service charges, hours of transmission, directional signals and other pertinent information. 

#### JSON
``stationRemark: "AERO."``

## JSON Example
``` 
{
aidType: "Radiobeacons",
characteristic: "NA\n(- •  • - ).\n",
deleteFlag: "Y",
featureNumber: 240,
frequency: "385",
geopoliticalHeading: "CANADA - ATLANTIC COAST",
name: "Natashquan, Que.",
noticeNumber: 200050,
noticeWeek: "50",
noticeYear: "2000",
position: "50°13'23.99\"N \n61°50'36\"W",
postNote: null,
precedingNote: null,
range: "150",
regionHeading: null,
removeFromList: "N",
sequenceText: null,
stationRemark: "AERO.",
volumeNumber: "PUB 110"
}
```

# Differential GPS Stations (DGPS)
https://msi.om.east.paas.nga.mil/api/publications/ngalol/dgpsstations?includeRemovals=false&output=html


Returns
```
{
  "ngalol": [records]
}
```

## Columns Displayed in PDF and Query Page

### Number
U.S. assigned number to the feature

#### JSON

``featureNumber: 4``

### Name & Location
Name of the DGPS station

#### JSON
``name: "Cape Ray (Port aux Basques), Newfoundland"``

### Position
Latitude Longitude of feature to nearest tenth of a minute (not true based on the following from the API)

#### JSON
``position: "47°38'00.01\"N \n59°14'00\"W""``

### Station ID
Station ID which can be found in the IALA Master list. No two stations have the same ID. T denotes the Transmitting Station, R denotes the Reference Station.

#### JSON
``stationID: "T942\nR340\nR341\n"``

### Range
The distance in nautical miles

#### JSON
``range: 189``

### Frequency
Frequency in kHz.

#### JSON
``frequency: 288``

### Transfer Rate
Transfer Rate which equates to the baud rate and will be published as a whole number without any additional abbreviations such as “bps” (bits per second)

#### JSON
``transferRate: 200``

### Remarks
Remarks. This column contains information about the reference stations and messages types transmitted. GPS Message Type Numbers are 1, 3, 4, 5, 6, 7, 9, 15 and 16.
```
GPS MESSAGE TYPE NUMBER INDICATORS
1 Differential GNSS corrections (full set of satellites)
3 Reference stations parameters
4 Datum used
5 Constellation health
6 Null frame (no information)
7 Radiobeacons Almanacs
9 Sub-set differential GNSS corrections
15 Ionospheric corrections
16 Special messages
```

#### JSON
``remarks: "Message types: 3,5,6,7,9,16."``


## JSON Example
``` 
{
aidType: "Differential GPS Stations",
deleteFlag: "N",
featureNumber: 115,
frequency: 310,
geopoliticalHeading: "CANADA-ATLANTIC COAST",
name: "Cape Norman, Newfoundland",
noticeNumber: 199904,
noticeWeek: "04",
noticeYear: "1999",
position: "51°30'00\"N \n54°49'00\"W",
postNote: null,
precedingNote: null,
range: 189,
regionHeading: null,
remarks: "Message types: 3,5,6,7,9,16.",
removeFromList: "N",
stationID: "T944\nR342\nR343\n",
transferRate: 200,
volumeNumber: "PUB 110"
}
```

## API Quirks

 * You must specify includeRemovals=false to get any data back
 * Feature numbers are only unique when paired with volumeNumber



