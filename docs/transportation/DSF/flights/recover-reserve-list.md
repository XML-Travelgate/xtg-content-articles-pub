---
title: RetrieveReservationList
keywords: transportation, data structure, flights, recover reserve, retrieve list, list, reservation
search: Transportation - Flights - Data Structure - RetrieveReservationList
sidebar: mydoc_sidebar
permalink: /docs/transportation/DSF/flights/recover-reserve-list
---



### Method Goals


This method aims to return a list of bookings for a given time period
being that either booking date or the travelling date, among other filters available.


### Request Format

The filter can be set between two time periods, search by email, origin, destination, agency, passenger name/surname, etc.


### Response Format

The result return a briefing of the basic information of the bookings that match the query's filters.


### Remarks


Not implemented by all suppliers


### RetrieveReservationListRQ Description



| **Element**						| **Number**| **Type**	| **Description**													|
| --------------------------------- | --------- | ----------|------------------------------------------------------------------	|
| RetrieveReservationListRQ         | 1    		|			| Root node.|
| ReservationDate                   | 0..1 		| Date		| Reservation date.|
| DepartureDate                     | 0..1 		| Date		| First journey departure date.|
| fechaReservaDesde                 | 0..1 		| Date		| .|
| fechaReservaHasta                 | 0..1 		| Date		| .|
| fechaSalidaDesde                  | 0..1 		| Date		| .|
| fechaSalidaHasta                  | 0..1 		| Date		| .|
| ClientEmail                       | 0..1 		| String	| Email.|
| OriginCode                       	| 0..1 		| String	| First journey origin code.|
| DestinationCode                   | 0..1 		| String	| First journey destination code.|
| AgencyCode                       	| 0..1 		| String	| Agency code.|
| numTransporte                     | 0..1 		| String	| .|
| Passenger							| 0..1 		|			| Contains information of the Passenger.|
| @id								| 0..1  	| Integer	| Unique identifier of the passenger.|
| @title							| 0..1  	|[Title type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#title-type)|Title type|
| @name								| 1  		| String 	| Name of the Passenger.|
| @surname        					| 1  		| String 	| Surname/s of the Passenger.|
| @bithDate							| 0..1  	| Date 		| Date of birth.|
| @codeDCO     						| 0..1  	| Integer 	| Consolidate document number.|
| @documentType						| 0..1  	|[Document type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#document-type)|Document type.|
| @documentId						| 0..1  	| String 	| Unique identifier of the documentation.|
| @documentExpiration  				| 0..1		| Date 		| Expiration date of the documentation.|
| @documentExpedition  				| 0..1		| Date 		| Expedition date of the documentation.|
| @nationality						| 0..1  	| String 	| Nationality.|
| @gender							| 0..1  	| Char		| Gender.|
| @language							| 0..1  	| String 	| Language.|



### RetrieveReservationListRS Description



| **Element**						| **Number**| **Type**	| **Description**													|
| --------------------------------- | --------- | ----------|------------------------------------------------------------------	|
| RetrieveReservationListRS     	| 1    		|			| Root node.|
| ReservationList               	| 1    		|			| Contains a list of Reservations.|
| ReservationList/PaymentInfo   	| 1..n   	|			| Contains some basic information of the booking.|
| @locator                 			| 1 		| String	| Booking locator.|
| @totalAmount             			| 0..1 		| Decimal	| Total amount.|
| @currency                			| 0..1 		| String	| Currency code of the fare.|
| ReservationList/PaymentInfo<br>/ReservationStatus			| 1    || Current status of the reservation.|
| ReservationList/PaymentInfo<br>/ReservationStatus/ReservationStatusType	| 1 | String | Reservation Status type: CONFIRMED, CANCELLED.|
| ReservationList/PaymentInfo<br>/OriginCode				| 0..1 	| String	| First journey origin code.|
| ReservationList/PaymentInfo<br>/DestinationCode			| 0..1 	| String	| First journey destination code.|
| ReservationList/PaymentInfo<br>/ReservationDate			| 0..1 	| Date		| Reservation date.|
| ReservationList/PaymentInfo<br>/DepartureDate				| 0..1 	| Date		| First journey departure date.|
| ReservationList/PaymentInfo<br>/MainPaxName				| 0..1 	| String	| Name and surname of the main passenger of the reservation.	|
| ReservationList/PaymentInfo<br>/HolderName				| 0..1 	| String	| Name of the holder of the reservation.			|
| Locators                       	| 0..n  	|    		| Contains details of the locator.|
| Locators/Locator/Id            	| 1  		| String 	| Unique identifier of the locator.|
| Locators/Locator/Type          	| 1  		| [Locator type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#locator-type)| The locator's type	| 
| Version          					| 0..1  	| String 	| Booking version.|



