# Access sonnendach.ch data using GeoAdmin API
The suitability of roofs and façades for use of solar energy can be checked on [sonnendach.ch](https://www.uvek-gis.admin.ch/BFE/sonnendach/?lang=en) and [sonnenfassade.ch](https://www.uvek-gis.admin.ch/BFE/sonnenfassade/?lang=en). The data is published as Open Government Data on [opendata.swiss](https://opendata.swiss/en/dataset/?q=suitability&sort=score%20desc,%20metadata_modified%20desc&organization=bundesamt-fur-energie-bfe). To use the data in applications, the [GeoAdmin REST services](https://api3.geo.admin.ch/services/sdiservices.html) can be used. Here we show you, how you query the REST API:

## General information
You find detailled information on potential analysis and data model on the [SFOE website](https://www.bfe.admin.ch/solar-energy-suitability-roofs)

The following technical layer names can be used to query the api:
* suitability of roofs: ch.bfe.solarenergie-eignung-daecher
* suitability of façades: ch.bfe.solarenergie-eignung-fassaden

## 1. Get the coordinates of an address
You can use the [SearchServer](https://api3.geo.admin.ch/services/sdiservices.html#search) endpoint in order to get the coordinates of an address:

E.G: [Get the address of *Hauptstrasse 45 in 6260 Reiden*](https://api3.geo.admin.ch//rest/services/api/SearchServer?lang=de&searchText=Hauptstrasse%2045%206260%20Reiden&type=locations&sr=2056):
```
https://api3.geo.admin.ch//rest/services/api/SearchServer?
lang=de&
searchText=Hauptstrasse%2045
%206260%20Reiden
&type=locations
&sr=2056
```

## 2. Get the roof at the x/y location
Now use the [Identify](https://api3.geo.admin.ch/services/sdiservices.html#identify-features) endpoint to get the roof at location from 1.
Use the resulting *x and y* variables from the first query.

E.G: [Get the roof at *x=2640325.75 and y=1232914.625*](https://api3.geo.admin.ch//rest/services/api/MapServer/identify?geometryType=esriGeometryPoint&returnGeometry=true&layers=all:ch.bfe.solarenergie-eignung-daecher&geometry=2640325.75,1232914.625&tolerance=0&order=distance&lang=de&sr=2056):
```
https://api3.geo.admin.ch//rest/services/api/MapServer/identify?
geometryType=esriGeometryPoint&
returnGeometry=true&
layers=all:ch.bfe.solarenergie-eignung-daecher&
geometry=2640325.75,1232914.625&
tolerance=0&
order=distance&
lang=de&
sr=2056
```

## 3. Get all roofs of a building
Now use the [Find](https://api3.geo.admin.ch/services/sdiservices.html#find) endpoint to get all roofs of a building. Use the resulting *building_id* variable from the second query.

E.G. [Get all roofs of the building with *building_id=229760*](https://api3.geo.admin.ch//rest/services/api/MapServer/find?layer=ch.bfe.solarenergie-eignung-daecher&searchField=building_id&searchText=229760&contains=false):
```
https://api3.geo.admin.ch//rest/services/api/MapServer/find?
layer=ch.bfe.solarenergie-eignung-daecher&
searchField=building_id&
searchText=229760&
contains=false
```
