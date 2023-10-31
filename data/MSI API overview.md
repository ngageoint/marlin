# MSI API overview

# TEM June 13, 2022

* we need to add things to 4.2.2
* we will start an email communication with the API questions and put those answers on confluence

## Users
* who are the users?
  * merchant marines?

* merchant marines carry lots of things on their ships.  This should supplement those paper charts.     
* For example, I am navigating around and i need to see what is around where i am.  
* I need to plan a route and need to know what is at the port or where pirate activity is taking place.
* provide amplifying information to the static information which allows the watchstander? or bridgestander to make more informed decisions.
* provide better information to those individuals to make better decisions
* know where the modus are for recreational mariners (fishermen, etc)
* navy people will want updates to modu information and they can get it from the app

## Connectivity
* very limited bandwidth on most boats
* satelite internet is a possibility that people have
* starlink
* cell when close

## Mockups
* share sheet will share as text or geospatially
* text for a navigation warning should be selectable to be copied somewhere else


# Design

* Should allow the user to sort by distance to feature.  Some features do not have an actual location but they do have a subregion or a nav area and those should act as distance zero if the user is in that area.  This should probably be the default that they can change.

## Navigational Warnings defaults
* section by `navArea` and sort with current navArea first

## Lights / Buoys defaults
* section by `geopoliticalHeading` + `regionHeading`
* sort by distance to feature

## ASAM defualts
* sort by date
* section by distance to feature in buckets maybe?

## MODU
* sort by distance to feature

## World Port Index
* sort by distance to feature
* Should we have a tree structure starting at `dodWaterBody` -> `countryName` ending with `regionName` as sections? or maybe `navArea` as the top level, or maybe just `countryName`, or `dodWaterBody` but start them within the body of water they are currently in?
* Should be able to configure what is shown about the port on the list view secondary lines, ie port features like depth etc.

## Would be cool
* "Around Me" list which could show all things around your current position sorted by distance

# Questions

## List of lights
* If we query for all lights, do we get the most recent position of the light, or do we get all previous positions as well and we need to only use the latest one based on `noticeWeek'`and `noticeYear`?
* JSON is returned with the following feature number: `featureNumber: "4\nL5000"`  This means US feature 4 and international feature L5000.  The feature number appears to be unique when paired with `volumeNumber`.  Is that true?
* the `geopoliticalHeading` is populated for all results, however the `regionHeading` is only populated for the first result in the list for that region, why?
* As far as I can tell, you must specify includeRemovals=false to get any data back.  What is supposed to happen with includeRemovals=true?

## MODU
* Is the name the primary key which we can use to track when they move?

## Navigational Warnings
* is the `text` parameter formatted according to some spec?
* what is `status`?
* Does NGA have something that can parse this into something useful? They do provide a KML file which seems to indicate there can be some parsing

## Electronic Nautical Publications
* `pubTypeId` groups the files, what do these numbers mean, is there an API to call to get information about them?

# Mappable Data Sources

* ASAM
* MODU
* World Ports
* Lighted Aids
* Radio Beacons
* Differential GPS Stations
* Radio Direction Finders (DFRS) / Radar Stations

# Not Mappable

## Not Mappable due to the nature of the data

* Time Signals (only an area)
* Warnings (only an area)
* Notice to Mariners
* Electronic Publications

## Not Mappable because it needs to be parsed

* Navigational Warnings

# UI things

* layers button for OSM and operating system maps
* should the list view filter based on the map viewport?
  * maybe with an option to filter based on a radius, and also an option to view all
* should the filter button always be shown?
* should iOS have tabs just like mage, and android have hamburger like mage?
  * maybe android has the hamburger with all of them and settings to set their tabs
* maybe a wizard for initial set up that puts the things they care about on the map and sets the tabs
* might need to have a way to show things on the map too and not on the tabs.
* have to have a tab for the map
* pull to refresh
  ** set defaults for new pulls
* do we need a loading page or shoudl we just show on the map somewhere that we are pulling data
  ** probably better to show pulling status on the map
* maybe a switch box on the list view to decide to show on the map
* maybe put a switch box on the hamburger for show on map, use a map marker that is greyed out or not based on if it was on the map or not
* on the main map we should use bottom sheets
* should we have a "importance" to decide what to show as an icon ie a small dot or a big icon etc
* start with no clustering for now but if we do cluster, we should do pie chart type marker
* we need colors for each data source
* for lighted aids with sectors, maybe we show it.  put the radius on the map temprorarily when they click on a feature for example if a light can be seen a certain distance away.  could also flash the radius if that is what the light does
  ** maybe the radii get turned on automatically when they are zoomed in enough
* in the wizard when they select a data source maybe ask how many they want or how far back they want to see
* maybe for radio beacons we can show the morse code they are broadcasting on the icon when the click the feature
* bottom sheet should expand up to a big view, keep in mind if there are features close to other features it should still be slideable sidewaysy in the big view
* non mappable things should be in the side drawer and also could be on a tab
* should have a "media library" in the app that links to previously downloaded files that are stored in the "files" app or wherever the OS
* in the detail view of a publication we should have a download button to either download it or open it in whatever app if it is already downloaded

# TODO
* Settings
  * attributions/contact
  * for some data sources, maybe show dot or full marker
* Map Markers / Colors
* matomo callouts for views and certain button clicks
  * metrics for what they are picking
