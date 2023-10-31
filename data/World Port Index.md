# World Port Index

## Overview

World Port Index (Pub 150) contains the location and physical characteristics of, and the facilities and services offered by major ports and terminals world-wide (approximately 3700 entries)

# Is it mappable?

Yes.  ``ycoord`` and ``xcoord`` fields.

# How this data is used

Show them on the map

# API

## Fields for display

These field names and groups come from the World Port Index Application: https://nga.maps.arcgis.com/apps/MapSeries/index.html?appid=f9515d53e3e24ae7919f02eb8f554c96

Data fields are defined in here: https://msi.nga.mil/api/publications/download?key=16920959/SFH00000/WPI_Explanation_of_Data_Fields.pdf&type=view

## Name and Location
World Port Index Number: `portNumber` (number)

Region Name: `regionName` - `regionNumber` (string - number)

Main Port Name: `portName` (string)

Alternate Port Name: `alternateName` (string)

UN/LOCODE: `unloCode` (string)

Country: `countryName` (string)

World Water Body: `dodWaterBody` (string)

IHO S-130 Sea Area: ?

Sailing Directions or Publication: `publicationNumber`(string)

Standard Nautical Chart: `chartNumber` (string)

IHO S-57 Electronic Navigational Chart: `s57Enc` (string)

IHO S-101 Electronic Navigational Chart: `s101Enc` (string)

Digital Nautical Chart: `dnc` (comma separated string)

## Depths
Tidal Range (m): `tide` (number)

Entrance Width (m): `entranceWidth` (number)

Channel Depth (m): `chDepth` (string number)

Anchorage Depth (m): `anDepth` (string number)

Cargo Pier Depth (m): `cpDepth` (string number)

Oil Terminal Depth (m): `otDepth` (string number)

Liquified Natural Gas Terminal Depth (m): `lngTerminalDepth` (string number)

## Maximum Vessel Size
Maximum Vessel Length (m): `maxVesselLength` (string number)

Maximum Vessel Beam (m): `maxVesselBeam` (string number)

Maximum Vessel Draft (m): `maxVesselDraft` (string number)

Offshore Maximum Vessel Length (m): `offMaxVesselLength` (number)

Offshore Maximum Vessel Beam (m): `offMaxVesselBeam` (number)

Offshore Maximum Vessel Draft (m): `offMaxVesselDraft` (number)

## Physical Environment
Harbor Size: `harborSize` (string V = Very Small; S = Small; M = Medium; L = Large)

Harbor Type: `harborType` (string CN = Coastal (Natural); ??)
Harbors are classified as: Coastal (Natural), Coastal (Breakwater), Coastal (Tide Gates), River (Natural), River (Basin), River (Tide Gates), Canal or Lake, or Open Roadstead. 

Harbor Use: `harborUse` (string UNK = Unknown; ??)

Shelter Afforded: `shelter` (string E = Excellent, G = Good, F = Fair, P = Poor, N = None.)

Entrance Restriction - Tide: `erTide` (string N = No; Y = Yes;)

Entrance Restriction - Heavy Swell: `erSwell` (string N = No; Y = Yes;)

Entrance Restriction - Ice: `erIce` (string N = No; Y = Yes;)

Entrance Restriction - Other: `erOther` (string N = No; Y = Yes;)

Overhead Limits: `overheadLimits` (string Y/N)

Underkeel Clearance Management System: `ukcMgmtSystem` (string UNK = Unknown; ??)

Good Holding Ground: `goodHoldingGround` (string Y/N)

Turning Area: `turningArea` (string U = Unknown; ??)

## Approach
*note all are Y/N/U

Port Security: `portSecurity`

Estimated Time of Arrival Message: `etaMessage`

Quarantine - Pratique: `qtPratique`

Quarantine - Sanitation: `qtSanitation`

Quarantine - Other: `qtOther`

Traffic Separation Scheme: `tss`

Vessel Traffic Service: `vts`

First Port Of Entry: `firstPortOfEntry`

US Representative: `usRep`

## Pilots, Tugs, Communications
*note all are Y/N/U

Pilotage - Compulsory: `ptCompulsory`

Pilotage - Available: `ptAvailable`

Pilotage - Local Assistance: `ptLocalAssist`

Pilotage - Advisable: `ptAdvisable`

Tugs - Salvage: `tugsSalvage`

Tugs - Assistance: `tugsAssist`

Communications - Telephone: `cmTelephone`

Communications - Telefax: `cmTelegraph`

Communications - Radio: `cmRadio`

Communications - Radiotelephone: `cmRadioTel`

Communications - Airport: `cmAir`

Communications - Rail: `cmRail`

Search and Rescue: `searchAndRescue`

NAVAREA: `navArea`

## Facilities
*note all are Y/N/U

Facilities - Wharves: `loWharves`

Facilities - Anchorage: `loAnchor`

Facilities - Dangerous Cargo Anchorage: `loDangCargo`

Facilities - Med Mooring: `loMedMoor`

Facilities - Beach Mooring: `loBeachMoor`

Facilities - Ice Mooring: `loIceMoor`

Facilities - RoRo: `loRoro`

Facilities - Solid Bulk: `loSolidBulk`

Facilities - Liquid Bulk: `loLiquidBulk`

Facilities - Container: `loContainer`

Facilities - Breakbulk: `loBreakBulk`

Facilities - Oil Terminal: `loOilTerm`

Facilities - LNG Terminal: `loLongTerm`

Facilities - Other: `loOther`

Medical Facilities: `medFacilities`

Garbage Disposal: `garbageDisposal`

Chemical Holding Tank Disposal: `cht`

Degaussing: `degauss`

Dirty Ballast Disposal: `dirtyBallast`

## Cranes
*note all are Y/N/U

Cranes - Fixed: `crFixed`

Cranes - Mobile: `crMobile`

Cranes - Floating: `crFloating`

Cranes - Container: `cranesContainer`

Lifts - 100+ Tons: `lifts100`

Lifts - 50-100 Tons: `lifts50`

Lifts - 25-49 Tons: `lifts25`

Lifts - 0-24 Tons: `lifts0`

## Services and Supplies
*note all are Y/N/U

Services - Longshoremen: `srLongshore`

Services - Electricity: `srElectrical`

Services - Steam: `srSteam`

Services - Navigational Equipment: `srNavigEquip`

Services - Electrical Repair: `srElectRepair`

Services - Ice Breaking: `srIceBreaking`

Services - Diving: `srDiving`

Supplies - Provisions: `suProvisions`

Supplies - Potable Water: `suWater`

Supplies - Fuel Oil: `suFuel`

Supplies - Diesel Oil: `suDiesel`

Supplies - Aviation Fuel: `suAviationFuel`

Supplies - Deck: `suDeck`

Supplies - Engine: `suEngine` 

Repairs: `repairCode` (string C = Limited; ??)
From the Data Fields PDF: Repairs that can be made to ocean-going vessels are classified as
Major (extensive overhauling and rebuilding in well equipped
shipyards), Moderate (extensive overhauling and rebuilding that
does not require drydocking, or where suitable facilities are lacking
or inadequate), Limited (small repair work in independent machine
shops or foundries), Emergency Only, None, or Unknown.

Dry Dock: `drydock`

Railway: `railway`

## World Port Index Database Queries
https://msi.om.east.paas.nga.mil/api/publications/world-port-index?output=json

```json
{
  "ports": [
    {
      "portNumber": 760,
      "portName": "Aasiaat",
      "regionNumber": 545,
      "regionName": "GREENLAND  WEST COAST",
      "countryCode": "GL",
      "countryName": "Greenland",
      "latitude": "68°42'00\"N",
      "longitude": "52°52'00\"W",
      "publicationNumber": "Sailing Directions Pub. 181 (Enroute) - Greenland and Iceland",
      "chartNumber": null,
      "navArea": "XVIII",
      "harborSize": "S",
      "harborType": "CN",
      "shelter": "G",
      "erTide": "N",
      "erSwell": "N",
      "erIce": "Y",
      "erOther": "Y",
      "overheadLimits": "U",
      "chDepth": "23",
      "anDepth": "23",
      "cpDepth": "8",
      "otDepth": null,
      "tide": 3,
      "maxVesselLength": null,
      "maxVesselBeam": null,
      "maxVesselDraft": null,
      "goodHoldingGround": "N",
      "turningArea": "U",
      "firstPortOfEntry": "N",
      "usRep": "N",
      "ptCompulsory": "N",
      "ptAvailable": null,
      "ptLocalAssist": null,
      "ptAdvisable": "Y",
      "tugsSalvage": "N",
      "tugsAssist": "N",
      "qtPratique": "U",
      "qtOther": "U",
      "cmTelephone": "U",
      "cmTelegraph": "U",
      "cmRadio": "Y",
      "cmRadioTel": "U",
      "cmAir": "Y",
      "cmRail": "U",
      "loWharves": "Y",
      "loAnchor": "U",
      "loMedMoor": "U",
      "loBeachMoor": "U",
      "loIceMoor": "U",
      "medFacilities": "Y",
      "garbageDisposal": "N",
      "degauss": "U",
      "dirtyBallast": "N",
      "crFixed": "U",
      "crMobile": "Y",
      "crFloating": "U",
      "lifts100": "U",
      "lifts50": "U",
      "lifts25": "U",
      "lifts0": "Y",
      "srLongshore": "U",
      "srElectrical": "U",
      "srSteam": "U",
      "srNavigEquip": "U",
      "srElectRepair": "U",
      "suProvisions": "Y",
      "suWater": "Y",
      "suFuel": "Y",
      "suDiesel": "U",
      "suDeck": "U",
      "suEngine": "U",
      "repairCode": "C",
      "drydock": "U",
      "railway": "S",
      "qtSanitation": "U",
      "suAviationFuel": "U",
      "harborUse": "UNK",
      "ukcMgmtSystem": "U",
      "portSecurity": "U",
      "etaMessage": "Y",
      "searchAndRescue": "U",
      "tss": "U",
      "vts": "U",
      "cht": "U",
      "globalId": "{2C117765-0922-4542-A2B9-333253552952}",
      "loRoro": "U",
      "loSolidBulk": "U",
      "loContainer": "U",
      "loBreakBulk": "U",
      "loOilTerm": "U",
      "loLongTerm": "U",
      "loOther": "U",
      "loDangCargo": "U",
      "loLiquidBulk": "U",
      "srIceBreaking": "U",
      "srDiving": "U",
      "cranesContainer": "U",
      "unloCode": "GL JEG",
      "dnc": "a2800670, coa28e, gen28b, h2800670",
      "s121WaterBody": "",
      "s57Enc": null,
      "s101Enc": "",
      "dodWaterBody": "Baffin Bay; Arctic Ocean",
      "alternateName": "Egedesminde",
      "entranceWidth": null,
      "lngTerminalDepth": null,
      "offMaxVesselLength": null,
      "offMaxVesselBeam": null,
      "offMaxVesselDraft": null,
      "ycoord": 68.70000000000005,
      "xcoord": -52.86666699999995
    },
    {
      "portNumber": 48430,
      "portName": "Abadan",
      "regionNumber": 48410,
      "regionName": "IRAN",
      "countryCode": "IR",
      "countryName": "Iran",
      "latitude": "30°20'00\"N",
      "longitude": "48°17'00\"E",
      "publicationNumber": "Sailing Directions Pub. 172 (Enroute) - Red Sea and the Persian Gulf",
      "chartNumber": "62594",
      "navArea": "IX",
      "harborSize": "M",
      "harborType": "RN",
      "shelter": "G",
      "erTide": "Y",
      "erSwell": "N",
      "erIce": "N",
      "erOther": "Y",
      "overheadLimits": "U",
      "chDepth": "9",
      "anDepth": "9",
      "cpDepth": "9",
      "otDepth": null,
      "tide": 1,
      "maxVesselLength": null,
      "maxVesselBeam": null,
      "maxVesselDraft": null,
      "goodHoldingGround": "U",
      "turningArea": "Y",
      "firstPortOfEntry": "Y",
      "usRep": "N",
      "ptCompulsory": "Y",
      "ptAvailable": null,
      "ptLocalAssist": null,
      "ptAdvisable": "Y",
      "tugsSalvage": "N",
      "tugsAssist": "Y",
      "qtPratique": "Y",
      "qtOther": "U",
      "cmTelephone": "Y",
      "cmTelegraph": "Y",
      "cmRadio": "Y",
      "cmRadioTel": "U",
      "cmAir": "Y",
      "cmRail": "U",
      "loWharves": "Y",
      "loAnchor": "U",
      "loMedMoor": "U",
      "loBeachMoor": "U",
      "loIceMoor": "U",
      "medFacilities": "Y",
      "garbageDisposal": "U",
      "degauss": "U",
      "dirtyBallast": "N",
      "crFixed": "U",
      "crMobile": "Y",
      "crFloating": "Y",
      "lifts100": "Y",
      "lifts50": "U",
      "lifts25": "U",
      "lifts0": "Y",
      "srLongshore": "Y",
      "srElectrical": "U",
      "srSteam": "U",
      "srNavigEquip": "U",
      "srElectRepair": "U",
      "suProvisions": "U",
      "suWater": "Y",
      "suFuel": "Y",
      "suDiesel": "Y",
      "suDeck": "U",
      "suEngine": "U",
      "repairCode": "C",
      "drydock": "S",
      "railway": "S",
      "qtSanitation": "Y",
      "suAviationFuel": "U",
      "harborUse": "UNK",
      "ukcMgmtSystem": "U",
      "portSecurity": "U",
      "etaMessage": "Y",
      "searchAndRescue": "U",
      "tss": "U",
      "vts": "U",
      "cht": "U",
      "globalId": "{361E3AAE-91D3-4564-B99A-A14B52D7E21B}",
      "loRoro": "U",
      "loSolidBulk": "U",
      "loContainer": "U",
      "loBreakBulk": "U",
      "loOilTerm": "U",
      "loLongTerm": "U",
      "loOther": "U",
      "loDangCargo": "U",
      "loLiquidBulk": "U",
      "srIceBreaking": "U",
      "srDiving": "U",
      "cranesContainer": "U",
      "unloCode": "IR ABD",
      "dnc": "coa10n, gen10a, h1048385",
      "s121WaterBody": "",
      "s57Enc": null,
      "s101Enc": "",
      "dodWaterBody": "Persian Gulf; Indian Ocean",
      "alternateName": null,
      "entranceWidth": null,
      "lngTerminalDepth": null,
      "offMaxVesselLength": null,
      "offMaxVesselBeam": null,
      "offMaxVesselDraft": null,
      "ycoord": 30.33333300000004,
      "xcoord": 48.28333300000003
    },
    ...
```

## ist Port, Region, and Country Names for World Port Indexes
https://msi.om.east.paas.nga.mil/api/publications/world-port-index/wpi-prc-names

List of countries, ports and region names.  Useless for us.