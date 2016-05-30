---
title: CurrencyList
keywords: hotel, data structure, currency list, list
sidebar: mydoc_sidebar
permalink: /docs/hotel/DSF/CurrencyList
---



### Method Goals


This method returns a list of currencies, provided that the supplier has
this petition implemented in there systems on an availability level,
with this meaning that the provider can use different currencies in the
availability.



### Request Format


The request does not require any elements. Empty request.



### Response Format


The result returns a list of currencies.



### Remarks


This petition is still in a working progress. There are no integration
that have this petition implemented, but they will be added, provided
that the supplier returns said information.



### CurrenyListRQ Example


    <CurrenyListRQ>
    </CurrenyListRQ>



### CurrenyListRQ Description



| **Element**			| **Number**	| **Type**	| **Description**			|
| ----------------------------- | ------------- | ------------- | ------------------------------------- |
| CurrenyListRQ			| 1          	|		| Root node.				|




### CurrencyListRS Example


    <CurrencyListRS>
        <Currencies>
            <Currency>
                <Code>1</Code>
                <Name>EUR</Name>
            </Currency>
            <Currency>
                <Code>2</Code>
                <Name>USD</Name>
            </Currency>
        </Currencies>
    </CurrencyListRS>



### HotelListRS Description



| **Element**			| **Number**	| **Type**	| **Description**			|
| ----------------------------- | ------------- | ------------- | ------------------------------------- |
| CurrencyListRS		| 1          	|		| Root node.       			|
| Currencies 			| 1           	|		| Contains a list of currencies.	|
| Currency   			| 0..n       	|		| Contains details of the currency.	|
| @code 			| 1    		| String	| Code.    				|
| @Name 			| 1    		| String	| Name of the currency.			|



