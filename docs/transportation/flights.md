---
title: Flights Data Structure
keywords: transportation, flights data structure
sidebar: mydoc_sidebar
permalink: /developer-documentation/transportation/flights
---

The structure of the API specification follows a standard. This document
intends to explain every aspect of this structure and their fields.



The integration will have the following methods:



| **Method**			| **Input**			| **Output**			| **Required** | **Description**	|
| ----------------------------- | ----------------------------- | ----------------------------- | ------------ | ---------------------- |
| Availability  		| AvailabilityRQ 		| AvailabilityRS 		| Yes 	       | Makes a availability call |
| Valuation     		| ValuationRQ    		| ValuationRS    		| Yes 	       | Makes a pre-booking	|
| Reservation   		| ReservationRQ  		| ReservationRS  		| Yes 	       | Makes a booking	|
| RetrieveReservation		| RetrieveReservation RQ		| RetrieveReservation RS		| No 	       | Gets booking details	|
| RetrieveReservation List	| RetrieveReservation ListRQ	| RetrieveReservation ListRS	| No 	       | Gets booking list	|
| Cancellation  		| CancellationRQ 		| CancellationRS 		| No 	       | Cancels a booking	|



Each request sent to the **service url** requires a node called rqXML .
Inside this node travels the current method's Input object.



The data structure will always have common elements in all objects and
the specific objects related to the operation



**Data structure content:**

1. [Flights](/developer-documentation/transportation/flights)
2. [Avail](/developer-documentation/transportation/DSF/flights/avail)
3. [Valuation](/developer-documentation/transportation/DSF/flights/valuation)
4. [Reservation](/developer-documentation/transportation/DSF/flights/reservation)
5. [RetrieveReservation](/developer-documentation/transportation/DSF/flights/recover-reserve)
6. [RetrieveReservationList](/developer-documentation/transportation/DSF/flights/recover-reserve-list)
7. [Cancellation](/developer-documentation/transportation/DSF/flights/cancel)
