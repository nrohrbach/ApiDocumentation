# Access the metadata of SFOE datasets using CKAN-API of opendata.swiss
All OGD-datasets of the [Swiss Federal Office of Energy (SFOE)](https://www.bfe.admin.ch/bfe/en/home/supply/statistics-and-geodata/geoinformation.html) are listed in the National OGD portal [opendata.swiss](https://opendata.swiss/en). It is possible to access the information using the [CKAN-API](https://handbook.opendata.swiss/de/content/nutzen/api-nutzen.html) of opendata.swiss. Here we show you some examples how to query the CKAN-API:

## General information
A detailled documentation of CKAN-API is found [here](https://docs.ckan.org/en/latest/contents.html).

## List all datasets of an organization
Use the [organization_show](https://docs.ckan.org/en/latest/api/index.html#ckan.logic.action.get.organization_show) endpoint.

E.G [List all datasets of Federal Office of Energy](https://ckan.opendata.swiss/api/3/action/organization_show?id=bundesamt-fur-energie-bfe&include_datasets=True):
```
https://ckan.opendata.swiss/api/3/action/organization_show?
id=bundesamt-fur-energie-bfe&
include_datasets=True 
```
You can also use the [package_search](https://docs.ckan.org/en/latest/api/index.html#ckan.logic.action.get.package_search) endpoint for a more detailed answer.

E.G [List all datasets of Federal Office of Energy](https://ckan.opendata.swiss/api/3/action/package_search?fq=organization:(bundesamt-fur-energie-bfe)&rows=1000):
```
https://ckan.opendata.swiss/api/3/action/package_search?
fq=organization:(bundesamt-fur-energie-bfe)
&rows=1000
```
E.G [List the most recent modified datasets of Federal Office of Energy](https://ckan.opendata.swiss/api/3/action/package_search?fq=organization:(bundesamt-fur-energie-bfe)&sort=modified+desc):
```
https://ckan.opendata.swiss/api/3/action/package_search?
fq=organization:(bundesamt-fur-energie-bfe)
&sort=modified+desc
```

## Get details of a dataset
Use the [package_show](https://docs.ckan.org/en/latest/api/index.html#ckan.logic.action.get.group_package_show) endpoint. You can use *name* or *id* for the id parameter.

E.G. [Get details of *Statistics on hydropower plants (WASTA)*](https://ckan.opendata.swiss/api/3/action/package_show?id=statistik-der-wasserkraftanlagen-wasta):
```
https://ckan.opendata.swiss/api/3/action/package_show?
id=statistik-der-wasserkraftanlagen-wasta
```

You can also use the [package_search](https://docs.ckan.org/en/latest/api/index.html#ckan.logic.action.get.package_search) endpoint for a more detailed answer.

E.G. [Get details of *Statistics on hydropower plants (WASTA)*](https://ckan.opendata.swiss/api/3/action/package_search?fq=name:statistik-der-wasserkraftanlagen-wasta):
```
https://ckan.opendata.swiss/api/3/action/package_search?
fq=name:statistik-der-wasserkraftanlagen-wasta 
```

## Get details of a resource
Use the [resource_show](https://docs.ckan.org/en/latest/api/index.html#ckan.logic.action.get.resource_show) endpoint.

E.G. [Get details of the Geopackage download from *Statistics on hydropower plants (WASTA)*](https://ckan.opendata.swiss/api/3/action/resource_show?id=09b51573-ac87-4c2f-b9dd-bdb7d4dc4853):
```
https://ckan.opendata.swiss/api/3/action/resource_show?
id=09b51573-ac87-4c2f-b9dd-bdb7d4dc4853
```

## Get a list of resources available in csv format
Use the [package_search](https://docs.ckan.org/en/latest/api/index.html#ckan.logic.action.get.package_search) endpoint.

E.G. [Get all resources available in csv format (globally)](https://ckan.opendata.swiss/api/3/action/package_search?fq=res_format:CSV&rows=10000):
```
https://ckan.opendata.swiss/api/3/action/package_search?
fq=res_format:CSV
&rows=10000
```
E.G. [Get all resources available in csv format of Federal Office of Energy](https://ckan.opendata.swiss/api/3/action/package_search?fq=organization:bundesamt-fur-energie-bfe%20AND%20res_format:CSV&rows=10000):
```
https://ckan.opendata.swiss/api/3/action/package_search?
fq=organization:bundesamt-fur-energie-bfe%20AND%20res_format:CSV
&rows=10000
```

## Get a list of available licenses for datasets
Use the [license_list](https://docs.ckan.org/en/latest/api/index.html#ckan.logic.action.get.license_list) endpoint.

E.G. [Get all available licenses](https://ckan.opendata.swiss/api/3/action/license_list):
```
https://ckan.opendata.swiss/api/3/action/license_list
```
