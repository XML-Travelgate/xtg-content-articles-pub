---
title: Territories
keywords: activities, data structure, Territories
search: Activities - Data Structure - Territories
sidebar: mydoc_sidebar
permalink: /docs/activities/DSF/Territories
---



### Method Goals


This method returns all the Territories.



### Request Format


The request only requires the provider code and credentials.



### Response Format

The response contains a list of territories.


### StaticConfigurationRQ Description




| **Element**				| **Number**	| **Type**	| **Description**				|
| ------------------------------------- | ------------- | ------------- | --------------------------------------------- |
|Territories| 0..1|   | List of Territories |
|Territories/territory| 1..n |    |Elements of the list for each territory |
|@id | 1..1 |string| Territory code.|
|@name | 1..1 |string| Territory name.|
|@parentId|0..1|string|Territory code parent.|
|@type|1..1|Enum|TABLE|
|Territories/territory/geometry|0..1|  |List of coordinate.|
|Territories/territory/geometry/coordinate|1..n|  |Coordinates of the territory.|
|@latitude|1..1|string|latitude|
|@longitude|1..1|string|longitude|




### StaticConfigurationRS Example



~~~xml   
	<GetTerritoriesRS xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <Territories>
	<Territory id="0" name="España" type="Country"/>
    <Territory id="1" name="Francia" type="Country"/>
    <Territory id="10" name="Palma" type="Region" parentId="0"/>
  </GetTerritoriesRS>
~~~


### StaticConfigurationRS Description




| **Element**				| **Number**	| **Type**	| **Description**				|
| ------------------------------------- | ------------- | ------------- | --------------------------------------------- |
|Territories| 0..1|   | List of Territories |
|Territories/territory| 1..n |    |Elements of the list for each territory |
|@id | 1..1 |string| Territory code.|
|@name | 1..1 |string| Territory name.|
|@parentId|0..1|string|Territory code parent.|
|@type|1..1|Enum|TABLE|
|Territories/territory/geometry|0..1|  |List of coordinate.|
|Territories/territory/geometry/coordinate|1..n|  |Coordinates of the territory.|
|@latitude|1..1|string|latitude|
|@longitude|1..1|string|longitude|


### Types tables

#### eTerritotyType
| **Type** | **Description** |
| ---------| --------------- | 
|Country   | Territory is a country|
|Region	   | Region can be a city, a zone, etc.|
|Other     | Territory which is not a Country or a Region|
|UNKNOWN   | Territory type not specified by supplier |
