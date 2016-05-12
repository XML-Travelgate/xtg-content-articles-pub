---
title: HotelList
keywords: hotel, data structure, hotel list, list
sidebar: mydoc_sidebar
permalink: /developer-documentation/hotel/DSF/HotelList
---

|

Method Goals
============

This method returns a list of hotels, where every hotel contains basic
information ( code, name, address, phone...)

|

Request Format
==============

The request does not require any elements. Empty request.

|

Response Format
===============

The result returns a list of *Hotel* (hotels).

|

Remarks
=======

The maximum time, that is permitted in our system, before the connection
is closed, is of **240000** milliseconds.

This method may be preloaded in **XML Travelgate**'s system if it takes
more than 4 minutes to download.

The **ContinuationToken** can be used in this call, the specification
can be see in Common-Elements section\_.

|

HotelListRQ Example
===================

    <HotelListRQ>
    </HotelListRQ>

|

HotelListRQ Description
=======================

| **Element**		| **Number**	| **Type** | **Description**	|
| --------------------- | ------------- | -------- | ------------------ |
| HotelListRQ		| 1          	|	   | Root node.		|

|

HotelListRS Example
===================

    <HotelListRS>
        <Hotels>
            <Hotel>
                <Code>5</Code>              
                <GiataId source = "http://urlGiata">1200</GiataId>
                <Name>BADAJOZ</Name>
                <Address>CTRA.NACIONAL V, KM 393</Address>
                <Town>BADAJOZ</Town>
                <ZipCode>06002</ZipCode>
                <CountryISOCode>ES</CountryISOCode>
                <AvailDestination code = "06" name = "BADAJOZ"/>
                <GeographicDestination code = "06" name = "BADAJOZ" avail = "true"/>
                <Latitude>38.893839</Latitude>
                <Longitude>-7.014112</Longitude>
                <Contact>
                    <Email>badajoz@xxx.com</Email>
                    <Telephone>91425891</Telephone>
                    <Fax>910200200</Fax>
                </Contact>
                <CategoryCode>4 Estrellas</CategoryCode>
                <PaymentOptions cash="false" bankAcct="false">
                    <Cards>
                        <Card code="VI"/>
                        <Card code="AX"/>
                        <Card code="CA"/>  
                    </Cards> 
                <PaymentOptions/>               
                <ExclusiveDeal>true</ExclusiveDeal>     
                <PropertyCategory>
                     <Code>1</Code>
                     <Name>Hotel</Name>             
                </PropertyCategory>                 
            </Hotel>
            <Hotel>
                <Code>65#7</Code>
                <ProviderCode>7</ProviderCode>              
                <GiataId source = "http://urlGiata">1200</GiataId>
                <Name>ILLA</Name>
                <Address>AVDA. ILLA S/N</Address>
                <Town>HUELVA</Town>
                <ZipCode>21449</ZipCode>
                <CountryISOCode>ES</CountryISOCode>
                <AvailDestination code = "2" name = "HUELVA"/>
                <GeographicDestination code = "2" name = "HUELVA" avail = "true"/>
                <Latitude>37.207295</Latitude>
                <Longitude>-7.23768</Longitude>
                <Contact>
                    <Email>emailhotel@xxx.es</Email>
                    <Telephone>95124578</Telephone>
                    <Fax>910200200</Fax>
                </Contact>
                <CategoryCode>4 Estrellas</CategoryCode>   
                <PropertyCategory>
                     <Code>2</Code>
                     <Name>Home</Name>              
                </PropertyCategory>                 
            </Hotel>
            <Hotel>...</Hotel>
        </Hotels>
    </HotelListRS>

|

HotelListRS Description
=======================

| **Element**				| **Number**	| **Type**	| **Description**				|
| ------------------------------------- | ------------- | ------------- | --------------------------------------------- |
| HotelListRS/Hotels/Hotel		| 0..n       	| 		| Root node. Hotel sheet.			|
| Code       				| 1    		| String	| Internal code to perform availability and/or provider code. |
| ProviderCode				| 0..1 		| String	| Internal code established by the provider (see  StaticConfiguration). |
| GiataId    				| 0..1       	|		| Giata System.					|
| @source    				| 0..1 		| String	| Giata url, endpoint access where we obtain a Giata id. |
| @value     				| 0..1 		| String	| Giata code, depends on the product of each provider is in a Giata System. |
| Name       				| 1    		| String	| Name.						|
| Address    				| 1    		| String	| Address.     					|
| Town       				| 1    		| String	| Town.						|
| ZipCode    				| 1    		| String	| ZipCode.  					|
| CountryISOCode			| 1    		| String	| CountryISOCode.				|
| AvailDestination			| 0..1       	|		| Avail Destination (will come only if it is attackable on availability, and the type is CTY). |
| @code      				| 1    		| String	| Destination code.  				|
| @name      				| 1    		| String	| Destination name.   				|
| GeographicDestination			| 1          	|		| Geographic Destination.    			|
| @code      				| 1    		| String	| Destination code.    				|
| @name      				| 1    		| String	| Destination name. 				|
| @avail     				| 1    		| Boolean	| Indicates if it is attackable on availability.|
| Latitude   				| 1    		| String	| Latitude.  					|
| Longitude  				| 1    		| String	| Longitude.   					|
| Contact    				| 1          	|		| Contact.					|
| Contact/Email				| 1    		| String	| Email.					|
| Contact/Telephone			| 1    		| String	| Telephone.   					|
| Contact/Fax				| 1    		| String	| Fax.  					|
| CategoryCode				| 1    		| String	| CategoryCode.					|
| Type       				| 0..1 		| String	| Hotel type: H (hotel) A (apartment) AH (aparthotel) C (club) AT (agritourism) HS (hostel) CA (house) V (Ville) B (Bungalows). |
| PaymentOptions			| 0..1 		| String	| Type of cards allowed by the provider. This tag only is mandatory if payment type is different  that *MerchantPay*. |
| @cash 				| 1    		| Boolean	| Deprecated attribute. 			|
| @bankAcct				| 1    		| Boolean	| Deprecated attribute.				|
| PaymentOptions/Cards			| 1          	|		| List of cards allowed.			|
| PaymentOptions/Cards/Card		| 1..n       	|		| Type card allowed.				|
| @code					| 1    		| String	| Code card (see in *Lists of Data* (VI,AX,BV,CA...)).|
| ExclusiveDeal				| 0..1 		| Boolean	| Indicates that a Hotel is an Exlusive Deal. The provider has formed partnerships with select Hotels in order to bring you list rates and superior prime availability in locations. The provider suggests with provide the best value. |
| PropertyCategory			| 0..1       	|		| Hotels property type. Similar to Type, but on providers side. |
| PropertyCategory/Code			| 1    		| String	| Provider property code.			|
| PropertyCategory/Name			| 1    		| String	| Provider property name.			|

|

Detailed Description
====================

**Giata Code:**

A Giata code is a hotel code that provides information of said hotel.
This code is common for all of the providers.

*For example:*

For the provider TravellingTest:

    <Hotel>
        <Code>5</Code>
        <GiataFormatCode>254</GiataFormatCodez>
        <Name>BADAJOZ</Name>
    </Hotel>

For the provider TestOnTour:

    <Hotel>
        <Code>14</Code>
        <GiataFormatCode>254</GiataFormatCodez>
        <Name>BADAJOZ</Name>
    </Hotel>

Please note that for the same hotel, the internal code of each provider
is different, but the Giata code stays the same. Giata system it is an
external company that does an generic mapping of all of the hotels
information.

|

**AvailDestination & GeographicDestination:**

Please note that the code for these parameters needs to be the lowest
destination level. And these values are available in the
AvailDestinationTree & GeographicDestinationTree call respectively.

|

**Hotel types:**

H (Hotel)

A (apartment)

AH (apartment Hotel)

C (Club)

AT (agritourism)

HS (hostel)

CA (House)

V (Ville)

B (Bungalows)

D (Disco club)

|

**Provider Code:**

The hotel code could come concatenated with other codes, like the city
code. In these case, it's necessary to perform an availability call.
I.e, if you are making an availability search by hotel code and, the
city code is also needed, our system will concatenate them so you can
use it in Availability process. In this case, the code will be the one
generated by us, concatenating the hotel code and the city code, and not
the providers native code. It can also happen with other code types
instead of city code (i.e. country code). Only in these cases we return
the *ProviderCode* tag, that contains the internal code used by the
provider (see StaticConfiguration).

|
