---
title: MetaData
keywords: hotel, data structure, meta data
search: Hotel - Data Structure - Metadata
sidebar: mydoc_sidebar
permalink: /docs/hotel/DSF/MetaData
---

### Method Goals


This method provides information about the meta data of the
supplier so that it can be effectively configured.



### Request Format


The request does not require any elements - empty request.



### Response Format


The XML response contains many elements of the supplier's meta data: number of
hotels, number of cities and number of areas available, maximum number of
*roomcandidate*, maximum number of paxes in a *roomcandidate*, release days,
minimum stay, list of languages supported ...



### MetaDataRQ Example


~~~xml
    <MetaDataRQ>
    </MetaDataRQ>
~~~


### MetaDataRQ Description


  
| **Element**			| **Number**	| **Type**	| **Description**	|
| ----------------------------- | ------------- | ------------- | --------------------- |
| MetaDataRQ		| 1          	|		| Root node.		|
