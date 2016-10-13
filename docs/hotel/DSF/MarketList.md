---
title: MarketList
keywords: hotel, data structure, market list, market, markets, list
search: Hotel - Data Structure - MarketList
sidebar: mydoc_sidebar
permalink: /docs/hotel/DSF/MarketList
---



### Method Goals


This method aims to return a list of the available Markets, which will
be used in the availability request.



### Request Format


The request does not require any elements - empty request.



### Response Format


The result returns a list of *Market*.



### Remarks


The maximum time permitted in our system before the connection is closed is  **240000** milliseconds.
Most suppliers use a standard ISO - 3166_1_alfa_2, but it depends on each individual supplier.



### MarketListRQ Example


~~~xml
    <MarketListRQ>
    </MarketListRQ>
~~~


### MarketListRQ Description




| **Element**		| **Number** | **Type** | **Description**		|
| --------------------- | ---------- | -------- | ----------------------------- |
| MarketListRQ	| 1          |		| Root node.			|



### MarketListRS Example


~~~xml
    <MarketListRS>
        <Markets>
            <Market>
                <Code>ES</Code>
                <Name>Spain</Name>
            </Market>
            <Market>
                <Code>PT</Code>
                <Name>Portugal/Name>
            </Market>
            …
            <Market/>
        </Markets>
    </MarketListRS>
~~~


### MarketListRS Description




| **Element**		| **Number** | **Type** | **Description**	|
| --------------------- | ---------- | -------- | --------------------- |
| MarketListRS/Markets	| 1          |		| Root node, list of markets.		|
| Market	| 1..n          	| 		| Market.			|
| Market/Code	| 1         	| String		| Code.			|
| Market/Name	| 1          	| String		| Name.			|

                       

