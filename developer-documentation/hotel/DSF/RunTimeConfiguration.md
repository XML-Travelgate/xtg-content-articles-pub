---
title: RuntimeConfiguration
keywords: hotel, data structure, run time configuration, time
sidebar: mydoc_sidebar
permalink: /developer-documentation/hotel/DSF/RuntimeConfiguration
---



### Method Goals


This message lets you know the provider configuration template.



### Request Format


The request does not require any elements empty request.



### Response Format


The returned XML contains a template of all fields used by the provider.



### RuntimeConfigurationRQ Example


    <RuntimeConfigurationRQ>
    </RuntimeConfigurationRQ>



### RuntimeConfigurationRQ Description



| **Element**			| **Number**	| **Type**	| **Description**	|
| ----------------------------- | ------------- | ------------- | --------------------- |
| RuntimeConfigurationRQ	| 1          	|		| Root node.		|
                 



### RuntimeConfigurationRS Example


    <RuntimeConfigurationRS>
        <Configuration>
            <User/>
            <Password/>
            <UrlGeneric/>
            <Parameters>
                <Parameter key = "agencia" value = ""/>
            </Parameters>
        </Configuration>
    </RuntimeConfigurationRS>



### ConfiguracionRunTimeRS Description


 
| **Element**			| **Number**	| **Type**	| **Description**			|
| ----------------------------- | ------------- | ------------- | ------------------------------------- |
| RuntimeConfigurationRS	| 1          	|		| Root node.				|
 
