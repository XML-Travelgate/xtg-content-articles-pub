---
title: Flights Data Structure
keywords: transportation, flights data structure
search: Transportation - Flights Data Structure
sidebar: mydoc_sidebar
permalink: /docs/transportation/flights
---

### API Structure

The structure of the API specification follows a standard. This document
intends to explain every aspect of this structure and their fields.



The integration will have the following methods:



| **Element**											| **Input**					| **Output**				| **Required**	|**Description**									|
| ------------------------------------------------------|---------------------------|---------------------------|---------------|---------------------------------------------------|
| [Availability](/docs/transportation/DSF/flights/avail)| AvailabilityRQ			| AvailabilityRS			| Yes			| Return all the available options for a given date and itinerary. It does not filter different classes, times or fares. It will always return all of the results returned by the provider.|
| [Valuation](/docs/transportation/DSF/flights/valuation)				| ValuationRQ				| ValuationRS				| Yes			| Return the total price of the selected Option, plus the extra supplements (price and information required in ReservationRQ) available in the Option. This Option **must** be selected in the previous step (Availability).|
| [Reservation](/docs/transportation/DSF/flights/reservation)			| ReservationRQ				| ReservationRS				| Yes			| Book one or more Itineraries.|
| [Emit (Issuance)](/docs/transportation/DSF/flights/emit)				| EmitRQ					| EmitRS					| Yes*			| Issue the tickets. *Some suppliers don't require the Emit operation. The payment is already resolved at Reservation step.|
| [Refund](/docs/transportation/DSF/flights/refund)					| RefundRQ					| RefundRS					| No			| This method aims to return all the available options for a given date and itinerary. It does not filter different classes, times or fares. It will always return all of the results returned by the provider.|
| [Cancellation](/docs/transportation/DSF/flights/cancel)					| CancellationRQ			| CancellationRS			| No			| Cancel a booking.|
| [RetrieveReservation](/docs/transportation/DSF/flights/recover-reserve)	| RetrieveReservationRQ		| RetrieveReservationRS		| No			| Retrieve a booking with its full details.|
| [RetrieveReservationList](/docs/transportation/DSF/flights/recover-reserve-list) | RetrieveReservationListRQ	| RetrieveReservationListRS	| No			| Return a list of bookings for a given time period being that either booking date or the travelling date, among other filters available.|
| [Supplements](/docs/transportation/DSF/flights/supplements)			| SupplementsRQ				| SupplementsRS				| No			| Search for supplements (seat, baggage, etc).|
| [ReservationSupplements](/docs/transportation/DSF/flights/supplementsReservation) | SupplementsReservationRQ	| SupplementsReservationRS	| No			| Add supplements (seats, baggage, etc) to a reservation done previously.|


Each request sent to the **service url** requires a node called rqXML. Inside this node travels the current method's Input object.

The data structure will always have common elements in all objects and the specific objects related to the operation. Therefore, all the RQ and RS presented in the previous table, will have the following common structures:

### Common RQ Structure Description

| **Element**						| **Number**| **Type**	| **Description**													|
| --------------------------------- | --------- | ----------|------------------------------------------------------------------	|
| timeoutMillisencods				| 1   		| Integer	| Timeout in milliseconds that the client will be waiting for the response.|
| source          					| 1			|			| Information about source requesting the operation.|
| source/agencyCode					| 0..1		| String	| Agency code that requests the operation.|
| source/languageCode				| 1   		| String	| Language code (ISO 3166-1 alpha-2) format lowercase.|
| filterAuditData 					| 1			|			| Enables or disables information returned in audit data.|
| filterAuditData/registerTransactions						| 1   		| Boolean	| Returns all the transactions (XMLs) exchanged with the provider.|
| optionsQuota						| 1   		| Integer	| Sets the maximum number of Options returned.|
| Configuration   					| 1        	|			| Information about source requesting the operation.|
| @providerCode						| 1   		| String	| Provider (supplier) code of the connection.|
| Configuration/Credentials			| 0..1		|			| Required credentials for the conection with this provider.|
| @user								| 1   		| String	| User for the connection.|
| @password							| 1   		| String	| Password for the connection.|
| @officeId							| 0..1   	| String	| .|
| @iataCode							| 0..1   	| String	| .|
| Configuration/Credentials/<br>UrlGeneric					| 1			| String	| Url generic connection.|
| Configuration/Credentials/<br>UrlIdentification			| 0..1		| String	| Url for login/identification connection.|
| Configuration/Credentials/<br>UrlAvail					| 0..1		| String	| Url for Avail method.|
| Configuration/Credentials/<br>UrlValuation				| 0..1		| String	| Url for Valuation method.| 
| Configuration/Credentials/<br>UrlReservation				| 0..1		| String	| Url for Reservation method.|
| Configuration/Credentials/<br>UrlSpecifics				| 0..1     	|| Parameters for additional information.|
| Configuration/Credentials/<br>UrlSpecifics/Attribute		| 1..n     	|| List of parameter.|
| @key       						| 1   		| String	| Contains the keyword/Id to identify a parameter.|
| @value     						| 1   		| String	| Contains the value of the parameter.|
| Configuration/Attributes			| 0..1     	|			| Specific configuration parameters to this connector.|
| Configuration/Attributes/<br>Attribute					| 1..n     	|| List of parameter.|
| @key       						| 1   		| String	| Contains the keyword/Id to identify a parameter.|
| @value     						| 1   		| String	| Contains the value of the parameter.|
| ClientConfiguration				| 1        	|			| Client's configuration.|
| @agency    						| 1   		| String	| Agency name.|
| @currencyCode						| 1   		| String	| Currency code.|
| @mark      						| 0..1   	| String	| Mark.|
| @businessLine						| 0..1   	| String	| Business line.|
| @accessLevel						| 0..1   	| String	| Access level.|
| @mean      						| 0..1   	| String	| Mean.|
| @accessType						| 0..1   	| String	| Access type: WEB (Web) and WS (WebService).|


### Common RS Structure Description

| **Element**						| **Number**| **Type**	| **Description**													|
| --------------------------------- | --------- | ----------|------------------------------------------------------------------	|
| auditData 					    | 0..1		|			| Returns the provider transaction logs if filterAuditData/registerTransactions has been set to true.|
| auditData/processTimeMilliseconds | 1		    | Integer	| Time spend in the operation.|
| auditData/timeStamp 				| 1		    | Date		| Timestamp when the operation begins.|
| auditData/transactions 			| 1		    |			| Contains the RQ and RS of the provider transaction.|
| auditData/transactions/RQ 		| 1		    | String	| Provider's request transaction.|
| auditData/transactions/RS 		| 0..1		| String	| Provider's response transaction. In case of timeout/server communication failure with the provider, this field may not be returned.|
| auditData/transactions/timeStamp 	| 1		    | Date		| Timestamp when the provider transaction begins.|
| operationImplemented 				| 1		    | Boolean	| If true, the operation requested is implemented. Some suppliers does not have all the operations implemented. In that case, this filed will return false.|
| ResponseStatus 					| 0..1		|			| Contains information regarding the operation executed.|
| @direction 					    | 0..1		| String	| Direction of the journey about to checkin: OUTBOUND, INBOUND, OUTBOUND_INBOUND (Outbound and Inbound).|
| @tripType 					    | 0..1		| String	| Indicates the travel type: one way (OW), round trip (RT), open jaw (OJ) and circle trip (CT).|
| @status 					        | 1		    | String	| OK, ERROR, TIMEOUT.|
| applicationErrors 				| 0..n		|			| List of errors occurred during the operation execution.|
| applicationErrors/code 			| 0..1		| String			| Provider error code.|
| applicationErrors/description 	| 0..1		| String			| Error description.|
| applicationErrors/type 			| 0..1		| [Error types](/docs/transportation/error)			| API error type.|
| Warnings 					        | 0..1		|			| Contains a list of warnings.|
| Warnings/Warning 					| 1..n		|			| Warning occurred during the operation execution.|
| @code 					        | 0..1		| [Error types](/docs/transportation/error)			| API Warning code.|
| Warnings/Warning/text 			| 1		    | String	| Warning description.|



### Enumerate values

All the possible enumerate values are explained [here](/docs/transportation/enum).