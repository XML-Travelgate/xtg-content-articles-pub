---
title: Data Structure
keywords: transfers, data structure
sidebar: mydoc_sidebar
permalink: /developer-documentation/transfers/data-structure
---

The structure of the API specification follows a standard. This document
intends to explain every aspect of this structure and their fields. The
integration will have the following methods:

| 

| **Method**		| **Input**		| **Output**		|  **Required**	| **Description**				| **Endpoint**					|
| --------------------- | --------------------- | --------------------- | ------------- | --------------------------------------------- | --------------------------------------------- |
| Availability		| AvailabilityRQ	| AvailabilityRS	| Yes		| Makes an availability search   		| Transfers Booking Endpoint                    |
| RateRule		| RateRuleRQ		| RateRuleRS		| Yes 		| Makes a pre-booking      			| Transfers Booking Endpoint			|
| Book    		| BookRQ   		| BookRS   		| Yes 		| Creates a booking        			| Transfers Booking Endpoint			|
| RetrieveBooking	| Retrieve BookingRQ	| Retrieve BookingRS	| No  		| Retrieves Booking details			| Transfers Booking Endpoint			|
| CancelBooking		| Cancel BookingRQ	| Cancel BookingRS	| No  		| Cancels a booking        			| Transfers Booking Endpoint			|
| Destinations Tree	| Destinations TreeRQ	| Destinations TreeRS	| Yes 		| Gets a hierarchical list of destinations	| Transfers Booking Endpoint			|
| HotelList		| HotelListRQ		| HotelListRS		| No  		| Gets a list of the hotels with a basic information | Transfers Booking Endpoint		|
| GetRates		| GetRatesRQ		| GetRatesRS		| No  		| Gets a list of the rates with a basic information | Transfers Booking Endpoint		|
| GetSupplements	| GetSupplements RQ	| GetSupplements RS	| No  		| Gets a list of the supplements with a basic information | Transfers Booking Endpoint		|
| GetSupplier RateTransfers Type | Getsupplier RateTransfers TypeRQ | Getsupplier RateTransfers TypeRS | No | Gets a list of the types of suppliers transfers rates with a basicinformation | Transfers Booking Endpoint |
| GetSupplier TransfersType | GetSupplier TransfersTypeRQ | GetSupplier TransfersTypeRS | No | Gets a list of the suppliers transfers types with a basic information | Transfers Booking Endpoint |
| GetTransfersTypes  	| GetTransfers TypesRQ	| GetTransfers TypesRQ	| No  		| Gets a list of the transfers types with a basic information | Transfers Booking Endpoint	|
| GetVehicles     	| GetVehiclesRQ		| GetVehiclesRS		| No  		| Gets a list of the vehicles with a basic information | Transfers Booking Endpoint		|
                             
|

Each request sent to the **service url** requires a node called rqXML .
Inside this node travels the current method's Input object.

The data structure will always have common elements in all objects and
the specific objects related to the operation.

|

**Data structure content:**

1. [Common-Elements](/developer-documentation/transfers/DSF/common-elements)
2. [Avail](/developer-documentation/transfers/DSF/avail)
3. [Rate Rule](/developer-documentation/transfers/DSF/rate-rule)
4. [Booking](/developer-documentation/transfers/DSF/reservation)
5. [Retrieve Booking](/developer-documentation/transfers/DSF/retrieve-booking)
6. [Cancel Booking](/developer-documentation/transfers/DSF/cancel-booking)
7. [DestinationTree](/developer-documentation/transfers/DSF/destionationtree)
8. [HotelList](/developer-documentation/transfers/DSF/hotel-list)
9. [GetRates](/developer-documentation/transfers/DSF/GetRates)
10. [GetSupplements](/developer-documentation/transfers/DSF/GetSupplements)
11. [GetSupplierRateTransferTypes](/developer-documentation/transfers/DSF/GetSupplierRateTransfersTypes)
12. [GetSupplierTransferTypes](/developer-documentation/transfers/DSF/GetSupplierTransferTypes)
13. [GetTransferTypes](/developer-documentation/transfers/DSF/GetTransferTypes)
14. [GetVehicles](/developer-documentation/transfers/DSF/GetVehicles)





