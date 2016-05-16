---
title: Data Structure
keywords: activities, data structure
sidebar: mydoc_sidebar
permalink: /developer-documentation/activities/data-structure
---

The structure of the API specification follows a standard. This document
intends to explain every aspect of this structure and their fields.

The integration will have the following methods:

|

| **Method**		| **Input**		| **Output**		| **Required**	| **Description**		|
| --------------------- | --------------------- | --------------------- | ------------- | ----------------------------- |
| Search    		| SearchRQ   		| SearchRS   		| Yes  		| Gets destinations and events available |
| Avail     		| AvailRQ    		| AvailRS    		| Yes  		| Makes an availability call	|
| Valuation 		| ValuationRQ		| ValuationRS		| Yes  		| Makes a valuation for refresh ticket price (pre-book) |
| Reservation		| ReservationRQ		| ReservationRS		| Yes  		| Makes a booking		|
| ReservationRead	| ReservationReadRQ	| ReservationReadRS	| No    	| Information about one reservation |
| Cancel    		| CancelRQ   		| CancelRS   		| No   		| Cancel a reservation		|
| ReservationsList	| ReservationsListRQ	| ReservationsListRS	| No   		| List of Reservations		|
                       
|

Each request sent to the **service url** requires a node called rqXML .
Inside this node travels the current method's Input object.

The data structure will always have common elements in all objects and
the specific objects related to the operation

|

**Data structure content:**

1. [Common-Elements](/developer-documentation/activities/DSF/common-elements)
2. [Avail](/developer-documentation/activities/DSF/avail)
3. [Valuation](/developer-documentation/activities/DSF/valuation)
4. [Reservation](/developer-documentation/activities/DSF/reservation)
5. [ReservationRead](/developer-documentation/activities/DSF/reservation-read)
6. [ReservationList](/developer-documentation/activities/DSF/reservation-list)
7. [Cancel](/developer-documentation/activities/DSF/cancel)
8. [StaticConfiguration](/developer-documentation/activities/DSF/static-configuration)
9. [RunTimeConfiguration](/developer-documentation/activities/DSF/runtimeconfiguration)



