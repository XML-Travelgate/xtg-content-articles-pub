---
title: Avail
keywords: transportation, data structure, flights, avail
search: Transportation - Flights - Data Structure - Avail
sidebar: mydoc_sidebar
permalink: /docs/transportation/DSF/flights/avail
---



### Method Goals


This method aims to return all the available options for a given date
and itinerary. It does not filter different classes, times or fares. It
will always return all of the results returned by the provider.



### Request Format


The common part of an availability request is very straight forward. It
only requires the destination/s, the travelling dates, the paxes and the
indication of the trip type.



### Response Format


The response format will always be delivered in the node Transportation,
which will be organized by two main nodes: 

-   Segments:

A list with all of the Segments including details, returned by the
supplier, such as dates, number, etc.



-   Fares:

A list with all of the prices returned for each Segment in the above
list. Each Fare has a referenced SegmentReference inside the node
Option, to identify the Segment. A Fare will have one or more Segments
associated and every Segment will refer to at least one Option.

There will always be one PaxBreakdown per passenger type.

The price returned is "all inclusive". All fares, taxes and discounts
are already included in the total price.



### Remarks


This method **must** be called **before** the Valuation method.


### AvailabilityRQ Description


| **Element**				| **Number**	| **Type**	| **Description**						|
| ------------------------- | ------------- | --------- | -------------- |
| AvailabilityRQ        		| 1      	|		| Root node.	|
| @travelType      			| 1  		| String	| Indicates the travel type: one way (OW), round trip (RT), open jaw (OJ) and circle trip (CT).	|
| Journeys              		| 1      	|		| Contains a list of Journeys.				|
| Journeys/Journey      		| 1..n    	|		| Contains the information about the requested Journey in the availability. |
| @id              			| 1  		| Integer	| Unique identifier of the Journey.			|
| @departureDate   			| 1  		| String	| Departure date.					|
| @arrivalDate				| 1			| String	| Arrival date.		|
| @departureTime   			| 0..1  		| String	| Departure time.	|
| @arrivalTime				| 0..1			| String	| Arrival time.		|
| @action					| 0..1			| String	| Indicates the type of modification to be made in a reservation (works only for AvailabilityBookingModificationRQ): N(None), KF(Keep flights and fares), K(Only keep flights), C(Change), A(Add) and R(Remove).	|
| Journeys/Journey/AlternativeDates		| 0..1		|	| Contains a range of days (before/after) the departure of the journey.|
| @daysBefore			| 0..1		| Integer	| Range of days to travel before the departure of the journey.|
| @daysAfter			| 0..1		| Integer	| Range of days to travel after the departure of the journey.|
| Journeys/Journey/OriginLoc		| 1      	|		| Origin location.					|
| @code            			| 1  		| String	| Location code.					|
| @cityCode        			| 1  		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.	|
| @latitude					| 0..1	| String	| Indicates the latitude coordinades.	|
| @longitude					| 0..1	| String	| Indicates the longitude coordinades.	|
| @name						| 0..1			| String	| Location long name.|
| @radius					| 0..1			| Integer	| Area radius from location.|
| @type						| 1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).|
| Journeys/Journey/OriginLoc/<br>AlternativeLocations	| 0..1		|	| Contains a list of AlternativeLocations.|
| Journeys/Journey/OriginLoc/<br>AlternativeLocations/AlternativeLocation	| 1..n	|	| Contains the information of the alternative location.|
| @code						| 1			| String	| Location code.|
| @cityCode        			| 1  		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.|
| @name						| 0..1			| String	| Location long name.|
| @type						| 1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).|
| Journeys/Journey/DestinationLoc	| 1      	|		| Destination location.					|
| @code            			| 1  		| String	| Location code.					|
| @cityCode        			| 1  		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.	|
| @name						| 0..1			| String	| Location long name.|
| @radius					| 0..1			| Integer	| Area radius from location.|
| @type						| 1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).|
| Journeys/Journey/DestinationLoc/<br>AlternativeLocations	| 0..1		|	| Contains a list of AlternativeLocations.|
| Journeys/Journey/DestinationLoc/<br>AlternativeLocations/AlternativeLocation	| 1..n	|	| Contains the information of the alternative location.|
| @code						| 1			| String	| Location code.|
| @cityCode        			| 1  		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.|
| @name						| 0..1			| String	| Location long name.|
| @type						| 1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).|
| Passengers            		| 1      	|		| Contains a list of Passengers.			|
| Passengers/Passenger  		| 1..n    	|		| Contains information of the Passenger. 		|
| @id              			| 1  		| Integer	| Unique identifier of the Passenger.			|
| @age             			| 1  		| Integer	| Age of the Passenger.					|
| Passengers/Passenger/Bonuses		| 0..1    	|		| Possible discount or bonuses.				|
| @resident        			| 1  		| String	| [Resident discount type.](#availability-enumerate-description)						|
| @largeFamily     			| 1  		| String	| Family discount type: N(None), F1(Large family), F2 (Special large family).|
| @discountCardCode		| 0..1	| String	| Discount card code.|
| @discountCard		| 1	| String	| [Discount card type.](#availability-enumerate-description)|
| Passengers/Passenger/Bonuses/<br>DiscountCards	| 0..1	|	| Contains a list of DiscountCards.|
| Passengers/Passenger/Bonuses/<br>DiscountCards/DiscountCard|1..n	|	| DiscountCard details.|
| @code	| 0..1	| String | Discount card code.|
| @id	| 1	| String	| Unique identifier of discound card.|
| @type	| 1	| String	| [Discount card type.](#availability-enumerate-description)|
| Passengers/Passenger/Bonuses/<br>PaxTypeCodes		| 0..1	|		| Contains a list of PaxTypeCodes.|
| Passengers/Passenger/Bonuses/<br>PaxTypeCodes/PaxTypeCode	| 1..n	|	| Contains the code type of the passenger.|
| @code		| 1		| String	| Code type of the passenger.|
| Preferences           		| 0..1      	|		| Availability Preferences.				|
| @cabinClass      			| 1  		| String	| Preferred cabin class: N(None: don't apply by default), F(First), C(Business), Y(Economy), CAMAROTE(Cabin), YP(Economy Plus). 	|
| @allowOverNight	| 1	| Boolean	| If true, allows to the provider to return flights with overnight scales.|
| @brandedFares		| 1	| Boolean	| If true, the fares will contain extra information.|
| @lowCostIncluded	| 1	| Boolean	| If true, lowcost options will also be requested.|
| @trainIncluded	| 1	| Boolean	| If true, train options will also be requested.|
| @lightAvail	| 1 | Boolean	| If true, light options will also be requested.|
| @airLine	| 0..1	| String	| If specified, the search will request only fares of this airline.|
| @onlyNonStop	| 1	| Boolean	| If true, only nonStop journeys will be requested.|
| @onlyTrain	| 1	| Boolean	| If true, only train journeys will be requested.|
| @cheapestFares	| 1	| Boolean	| If true, the search will be based on the cheapest fares.|
| Preferences/ConnexionCompanies    		| 0..1      	|		| List of preferred companies.			|
| Preferences/ConnexionCompanies/<br>ConnexionCompany      		| 1..n      	|		| Preferred company.	|
| @carrier         			| 1  		| String	| Airline code.						|
| @mode            			| 1  		| String	| Mode: INCLUDED include preferred company and exclude all the others. EXCLUDED exclude only preferred company. ETK	|
| Preferences/ConnexionCompanies/<br>ConnexionCompany/Attributes	| 0..1	|	| List of attributes.
| Preferences/ConnexionCompanies/<br>ConnexionCompany/Attributes/Attribute	| 1..n	|	| Additional information key-value.
| @key	| 1	| String	| Attribute key.
| @value	| 1	| String	| Attribute value.
| SpecialSupplements	| 0..1	|	|	Contains a list of SpecialSupplements.
| SpecialSupplements/SpecialSupplement		| 1..n	|	|	Contains information about the Special Supplement
| @id	| 1	| String	| Unique identifier of the supplement.|
| @code	| 1	| String	| Supplement code.|
| @height	| 0..1	| Integer	| Dimension of the supplement: height.|
| @width	| 0..1	| Integer	| Dimension of the supplement: width.|
| @length	| 0..1	| Integer	| Dimension of the supplement: length.|
| @weight	| 0..1	| Integer	| Dimension of the supplement: weight.|
| @quantity	| 0..1	| Integer	| Quantity of supplements.|
| @description	| 0..1	| String	| Description of the supplement|
| @carrier	| 0..1	| String	| Carrier selling the supplement.|
| @estado	| 1	| String	| Status of the supplement: N(None), INC(Included in the price), CHA(Avalilable with charges), NOF(Not offered).|
| @needToken	| 1	| Boolean	| If true, the field @reservationToken should be filled|
| @type	| 1	| String	| Type of supplement: Miscelaneous, Seat, Meal, Pet, Lounge, Baggage, Canoe, PreferentialBoarding, Bike, Trailer, Seguro, Embarque_Prioritario, Acceso_Preferente, Bloqueo_Tarifa, Special_Assistance.|
| @reservationToken	| 0..1	| String	| Reservation Token of the supplement.|
| @ownTransportation	| 1	| Boolean	| If true, the supplement includes own transportation cage.|
| Vehicles	| 0..1	|	| Contains a list of vehicles.|
| Vehicles/Vehicle	| 1..n	|	| Contains details of the vehicle.|
| @id	| 1	| Integer	| Unique identifier of the vehicle.|
| @height	| 0..1	| Integer	| Dimension of the vehicle: height.|
| @length	| 0..1	| Integer	| Dimension of the vehicle: length.|
| @type	| 1	| String	| [Type of vehicle.](#availability-enumerate-description)|



### AvailabilityRS Description


| **Element**				| **Number**	| **Type**	| **Description**						|
| ------------------------- | ------------- | --------- | ---------------- |
| AvailabilityRS              		| 1     	|		| Root node.						|
| OptionalCharges	| 0..1 |	| Contains a list of OptionalCharges.	|
| OptionalCharges/OptionalCharge | 1..n	|	| Contains information about the optional service that could be added to the fares of availability.	|
|  @affectsADT	| 1	| Boolean	| True if the optional charge affects to the adults (ADT) passengers.	|
|  @affectsCHD	| 1	| Boolean	| True if the optional charge affects to the childs (CHD) passengers.	|
|  @affectsINF	| 1	| Boolean	| True if the optional charge affects to the infants (INF) passengers.	|
|  @description	| 0..1	| String	| Description of the optional charge.	|
|  @amount	| 1	| Decimal	| Charge amount of the optional charge.	|
|  @currency	| 1	| String	| Currency of the amount that the optional charge is in.	|
|  @elemNum	| 0..1	| Integer	| Number of elements included in the optional charge.	|
|  @weight	| 0..1	| Decimal	| Weight of the optional charge.	|
|  @forEachPax	| 1	| Boolean	| True if the charge applies for each passenger.	|
|  @forEachSeg	| 1	| Boolean	| True if the charge applies for each segment.	|
|  @type	| 1	| String	| Optional charge type: CARGO_TARJETA (credit/debit card charge), CARGO_MALETAS (baggage charge), CARGO_VEHICULO (vehicle charge), TASAS_VEHICULO (vehicle taxes).	|
| Transportation              		| 1     	|		| Contains all of the Segments and Fares.		|
| @totalFares            		| 1 		| Integer	| Total number of Fares. 				|
| Transportation/Segments     		| 1     	|		| Contains a list of the Segments.			|
| Transportation/Segments/Segment	| 1..n    	|		| Contains the information of the segment.		|
| @id                    		| 1 		| Integer	| Unique identifier of the segment. 			|
| @transportationId      		| 1 		| String	| Unique Id of the transportation. 			|
| @transportationType    		| 1 		| String	| Transport type: V ( Flight ), T ( Train ), B ( Bus ), S() & F ( Ferry ).	|
| @transportationName    		| 0..1 		| String	| Name of the transportation.	|
| @transportationCode	| 0..1	| String	| Code of the transportation. |
| @operatingCarrier      		| 1 		| String	| Company which operates the transportation.		|
| @marketingCarrier      		| 1 		| String	| Company which commercializes the transportation.	|
| @departureTerminal     		| 0..1 		| String	| Departure terminal. 					|
| @arrivalTerminal       		| 0..1 		| String	| Arrival terminal.					|
| @departureDate         		| 1 		| Date		| Departure date.					|
| @arrivalDate           		| 1 		| Date		| Arrival date. 					|
| @segmentDuration       		| 0..1 		| Integer	| Transport duration ( in minutes ). 			|
| @segmentStatus	| 1	| String	| Segment status: HK (Holding confirmed), TK(Confirming new flight times), UC(Unable to confirm), UN(Flight cancelled by airline), NO (No action taken), UD (Undefined). |
| @planeType             		| 0..1 		| String	| Plane type. Flights parameter.			|
| @maxCheckinDate        		| 0..1 		| String	| Maximum date to make the check-in. 			|
| @hasTechnicalStop      		| 1 		| Boolean	| If true, the segment has a technical stop. 		|
| @electronicTicket      		| 1 		| Boolean	| If true, the segment uses a electronic ticket. 	| 
| @secureFlight          		| 1		| Boolean	| If true, the provider requires extra information of the passengers. Flights parameter.	|
| Transportation/Segments/Segment/<br>OriginLoc | 1     	|		| Origin location.					|
| @type                  		| 1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).	|
| @code                  		| 1 		| String	| Location code.					|
| @name	| 0..1 		| String	| Location full name.	|
| @radius					| 0..1			| Integer	| Area radius from location.|
| @cityCode              		| 1 		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.	|
| Transportation/Segments/Segment/<br>OriginLoc/AlternativeLocations	| 0..1		|	| Contains a list of AlternativeLocations.|
| Transportation/Segments/Segment/<br>OriginLoc/AlternativeLocations/<br>AlternativeLocation	| 1..n	|	| Contains the information of the alternative location.|
| @code						| 1			| String	| Location code.|
| @cityCode        			| 1  		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.|
| @name						| 0..1			| String	| Location long name.|
| @type						| 1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).|
| Transportation/Segments/Segment/<br>DestinationLoc | 1   |  		| Destination location.					|
| @type                  		| 1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).	|
| @code                  		| 1 		| String	| Location code.|
| @name	| 0..1 		| String	| Location full name.	|
| @radius					| 0..1			| Integer	| Area radius from location.|
| @cityCode              		| 1 		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.	||
| Transportation/Segments/Segment/<br>DestinationLoc/AlternativeLocations	| 0..1		|	| Contains a list of AlternativeLocations.
| Transportation/Segments/Segment/<br>DestinationLoc/AlternativeLocations/<br>AlternativeLocation	| 1..n	|	| Contains the information of the alternative location.|
| @code						| 1			| String	| Location code.|
| @cityCode        			| 1  		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.|
| @name						| 0..1			| String	| Location long name.|
| @type						| 1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).|
| Transportation/Segments/Segment/<br>TechnicalStops | 0..1 |   		| Contains a list of TechnicalStops.		|
| @totalTechnicalStops   		| 1 		| Integer	| Total number of TechnicalStops. 			|
| Transportation/Segments/Segment/<br>TechnicalStops/TechnicalStop | 0..n | | Contains the details of the TechnicalStop.	|
| @location              		| 1 		| String	| TechnicalStop location.				|
| @stopDate              		| 1 		| Date		| Approx. stop date and time. 				|
| @departureDate         		| 1 		| Date		| Approx. departure date and time.  			|
| Transportation/Fares                       		| 1     	|		| Contains a list of Fares.		|
| Transportation/Fares/Fare                  		| 1..n    	|		| Contains details of Fare.		|
| @id                    		| 1 		| Integer	| Unique identifier of the Fare.  			|
| @providerCode          		| 1 		| String	| Provider code.					|
| @fareType              		| 1 		| String	| Fare type: OW ( one way ), RT ( round trip ), OJ ( Open jaw ) & CT ( Circle trip ).	|
| @familyFare            		| 0..1 		| String	| Family fare name of the Fare. |
| Transportation/Fares/Fare/HasObFees        		| 1 		| Boolean	| If true then there is an extra fee for using credit card.   |
| Transportation/Fares/Fare/Conditions	| 0..1 |	| Contains a list of Fare Conditions. |
| Transportation/Fares/Fare/Conditions/<br>Condition	| 1..n |	| Contains details of the Condition that applies to the condition. |
| @cia	| 0..1	| String	| Carrier applying the condition.	|
| @code	| 0..1	| String	| Code of the condition.	|
| @id	| 1	| String	| Unique id of the condition.	|
| @language	| 1	| String	| Language in which the condition is written.	|
| @Text | 0..1	| String	| Description of the condition.	|
| Transportation/Fares/Fare/Conditions/<br>Condition/Paragraph	| 0..n | | List of Sentences and titles. |
| @title | 0..1	| String	| Title content.	|
| Transportation/Fares/Fare/Conditions/<br>Condition/Paragraph/Sentence	| 0..n | String	| List of Sentences contents. |
| Transportation/Fares/Fare/Options          		| 1     	|		| Contains a list of Fare Options.	|
| Transportation/Fares/Fare/Options/Option   		| 1..n    	|		| Contains details of the Fare Option.	|
| @id                    		| 1 		| Integer	| Unique identifier of the Option.	|
| @availJourneyRef       		| 1  		| Integer	| Reference id of the AvailabilityRQ Journey. 		|
| @numStopOver           		| 1 		| Integer	| Number of StopOvers. If -1, then we cannot know how many StopOvers via XML. |
| @carrier               		| 1 		| String	| Validating carrier.					|
| @familyFare            		| 0..1 		| String	| Family fare name of the Option. |
| Transportation/Fares/Fare/Options/Option/<br>SegmentReferences | 1  	|    		| Contains a list of SegmentReferences.	|
| Transportation/Fares/Fare/Options/Option/<br>SegmentReferences/SegmentReference | 1..n | | Contains details of the SegmentReference of each option.|
| @segmentRef            		| 1 		| Integer	| Reference of the Segment. 				|
| Transportation/Fares/Fare/Options/Option/<br>SegmentReferences/SegmentReference/<br>SegmentClasses | 1 | | Contains a list of SegmentClasses.	|
| Transportation/Fares/Fare/Options/Option/<br>SegmentReferences/SegmentReference/<br>SegmentClasses/SegmentClass | 1..n | | Contains details of the SegmentClass.   |
| @cabinClass            		| 1 		| String	| Cabin class of the seat: N (Not specified), Y (Tourist), C (Business), F (First), CA (Cabin, only for ferries), YP (Tourist Plus).	|
| @class                 		| 1 		| String	| Fare class. |
| @paxRef               	 	| 1 		| Integer	| Passenger reference. 					|
| @fareBasis             		| 0..1 		| String	| Identifier of the fare.				|
| @fareType              		| 1 		| String	| Fare type: PUB ( Public ), PRI ( Private ), NEGO ( Negotiated ) and CORP ( Corporate ).	|
| @avail                 		| 0..1 		| Integer	| Available seats remaining for this class (In flights, the maximum is 9).  |
| Transportation/Fares/Fare/Options/Option/<br>SegmentReferences/SegmentReference/<br>SegmentClasses/SegmentClass/Modifiable | 0..1 |  | Contains the information of the modifiable fare.	|
| @Description                 		| 0..1 		| String	| Modification description. |
| @amount                 			| 0..1 		| Decimal	| Modification amount. |
| @modifiable                 		| 1 		| Boolean	| If true, the fare allows this modification. |
| @currency                 		| 0..1 		| String	| Modification currency. |
| @amountType                 		| 1 		| String	| Modification amount type: AMOUNT (Fare amount), FEE (Fee amount), TOTAL (Total fare amount), PERCENTUAL (Percentual amount). |
| Transportation/Fares/Fare/Options/Option/<br>SegmentReferences/SegmentReference/<br>SegmentClasses/SegmentClass/<br>CancellationPolicies | 0..1 |  | Contains a list of CancellationPolicies.	|
| Transportation/Fares/Fare/Options/Option/<br>SegmentReferences/SegmentReference/<br>SegmentClasses/SegmentClass/<br>CancellationPolicies/CancellationPolicy | 1..n |  |Contains details of the CancelationPolicy.	|
| @fromDate                 		| 0..1 		| Date	| Date of the begining of the policy. |
| @amount                 			| 0..1 		| Decimal	| Policy amount. |
| @refundable                 		| 1 		| Boolean	| If true, the fare allows the refundation. |
| @currency                 		| 0..1 		| String	| Policy currency. |
| @amountType                 		| 1 		| String	| Policy amount type: AMOUNT (Fare amount), FEE (Fee amount), TOTAL (Total fare amount), PERCENTUAL (Percentual amount). |
| Transportation/Fares/Fare/Options/Option/<br>SegmentReferences/SegmentReference/<br>ReservationTokens | 0..1 |  | Specific attribute used for each provider.	|
| Transportation/Fares/Fare/Options/Option/<br>SegmentReferences/SegmentReference/<br>ReservationTokens/Attribute | 1..n |  | Type of attribute.	|
| @key                   		| 1 		| String	| Contains the keyword/ Id to identify a parameter.	|
| @value                 		| 1 		| String	| Contains the value of the parameter.			|
| Transportation/Fares/Fare/Options/Option/<br>BaggageTypes | 0..1    	|		| Contains a list of BaggageTypes.	|
| Transportation/Fares/Fare/Options/Option/<br>BaggageTypes/BaggageType	| 1..n |  	| Contains details of BaggageType.	|
| @checkInType        | 1  		| String	| Check-in type: OnLine & Airport.|
| @appliesSegments        		| 1  		| String	| Segments in which is applied: All, Departure, Return, Ref (only the segment references indicated in the node SegmentReferences).|
| Transportation/Fares/Fare/Options/Option/<br>BaggageTypes/BaggageType/<br>References		| 0..1	|	|	References for the Baggage Type.|
| Transportation/Fares/Fare/Options/Option/<br>BaggageTypes/BaggageType/<br>References/SegmentReferences		| 0..1	|	|	Contains a list of segment references for the Baggage Type.|
| Transportation/Fares/Fare/Options/Option/<br>BaggageTypes/BaggageType/<br>References/SegmentReferences/<br>SegmentReference		| 1..n	|	|	Segment reference.|
| @itineraryRef | 1 		| Integer| Unique identifier of the Itinerary.|
| @journeyRef | 1 		| Integer| Unique identifier of the Journey.|
| @segmentRef | 1 		| Integer| Unique identifier of the Segment.|
| Transportation/Fares/Fare/Options/Option/<br>BaggageTypes/BaggageType/<br>References/PaxReferences		| 0..1	|	|	Contains a list of passenger references for the Baggage Type.|
| Transportation/Fares/Fare/Options/Option/<br>BaggageTypes/BaggageType/<br>References/PaxReferences/<br>PaxReference		| 1..n	|	|	Passenger reference.|
| @paxRef | 1 		| String| Reference to the passenger.|
| Transportation/Fares/Fare/Options/Option/<br>BaggageTypes/BaggageType/Baggage | 1..n |    | Details of the baggage. 		|
| @id                    		| 1 		| String	| Unique identifier of the Baggage.			|
| @type                  		| 1 		| String	| Type of baggage: Bag, Bike, Wheelchair, Skis, BabyTrolley and HandBaggage.|
| @quantity              		| 0..1 		| Integer	| Baggage quantity.  					|
| @maxWeightPerUnit      		| 0..1 		| Integer	| Maximum weight of the baggage.  			| 
| @maxTotalWeight        		| 0..1 		| Integer	| Maximum weight of ALL the baggage.			|
| @paymentInAirpot       		| 1 		| Boolean	| Determines whether the pay is in station. 		|
| @code                  		| 0..1 		| String	| Code of the Baggage.					|
| @carrier               		| 1 		| String	| Carrier.						|
| @needToken             		| 1 		| Boolean	| Reserve token mandatory.				|
| @reservationToken             | 0..1 		| String| Reserve token.|
| @description             		| 0..1 		| String| Baggage description.|
| Transportation/Fares/Fare/Options/Option/<br>BaggageTypes/BaggageType/Baggage/<br>BaggageCharge | 0..1 |    | Details of the baggage charge.|
| @fixAmount             		| 0..1 		| Decimal| Total fixed amount.|
| @appliesFixAmount             | 1 		| String| The fixed amount applies to: PorReserva(Reservation), PorPasajero(Passenger), PorSegmento(Segment), TarifaBase(Base Fare), Tasas(Taxes), ForAdt(Adult passengers), ForChd(Children passengers), ForInf(Infant passengers).|
| @minFixAmount             		| 0..1 		| Decimal| Minimal fixed amount.|
| @maxFixAmount             		| 0..1 		| Decimal| Maximal fixed amount.|
| @minAmountPercentage             		| 0..1 		| Decimal| Minimal percentage amount.|
| @maxAmountPercentage             		| 0..1 		| Decimal| Maximal percentage amount.|
| @currency             		| 1 		| String| Currency.|
| @percentage             		| 0..1 		| Decimal| Total percentage amount.|
| @percentageApplied             		| 1 		| String| The percentage amount applies to: PorReserva(Reservation), PorPasajero(Passenger), PorSegmento(Segment), TarifaBase(Base Fare), Tasas(Taxes), ForAdt(Adult passengers), ForChd(Children passengers), ForInf(Infant passengers).|
| Transportation/Fares/Fare/Options/Option/<br>SpecialSupplements	| 0..1	|	|	Contains a list of SpecialSupplements.
| Transportation/Fares/Fare/Options/Option/<br>SpecialSupplements/SpecialSupplement		| 1..n	|	|	Contains information about the Special Supplement	|
| @id	| 1	| String	| Unique identifier of the supplement.|
| @code	| 0..1	| String	| Supplement code.|
| @height	| 0..1	| Integer	| Dimension of the supplement: height.|
| @width	| 0..1	| Integer	| Dimension of the supplement: width.|
| @length	| 0..1	| Integer	| Dimension of the supplement: length.|
| @weight	| 0..1	| Integer	| Dimension of the supplement: weight.|
| @quantity	| 0..1	| Integer	| Quantity of supplements.|
| @description	| 0..1	| String	| Description of the supplement|
| @carrier	| 1	| String	| Carrier selling the supplement.|
| @estado	| 1	| String	| Status of the supplement: N(None), INC(Included in the price), CHA(Avalilable with charges), NOF(Not offered).|
| @needToken	| 1	| Boolean	| If true, the field @reservationToken should be filled|
| @type	| 1	| String	| Type of supplement: Miscelaneous, Seat, Meal, Pet, Lounge, Baggage, Canoe, PreferentialBoarding, Bike, Trailer, Seguro, Embarque_Prioritario, Acceso_Preferente, Bloqueo_Tarifa, Special_Assistance.|
| @reservationToken	| 0..1	| String	| Reservation Token of the supplement.|
| @ownTransportation	| 1	| Boolean	| If true, the supplement includes own transportation cage.|
| Transportation/Fares/Fare/Options/Option/<br>SpecialSupplements/SpecialSupplement/<br>References		| 0..1	|	|	References for the Special Supplement.|
| Transportation/Fares/Fare/Options/Option/<br>SpecialSupplements/SpecialSupplement/<br>References/SegmentReferences		| 0..1	|	|	Contains a list of segment references for the Special Supplement.|
| Transportation/Fares/Fare/Options/Option/<br>SpecialSupplements/SpecialSupplement/<br>References/SegmentReferences/<br>SegmentReference		| 1..n	|	|	Segment reference.|
| @itineraryRef | 1 		| Integer| Unique identifier of the Itinerary.|
| @journeyRef | 1 		| Integer| Unique identifier of the Journey.|
| @segmentRef | 1 		| Integer| Unique identifier of the Segment.|
| Transportation/Fares/Fare/Options/Option/<br>SpecialSupplements/SpecialSupplement/<br>References/PaxReferences		| 0..1	|	|	Contains a list of passenger references for the Special Supplement.|
| Transportation/Fares/Fare/Options/Option/<br>SpecialSupplements/SpecialSupplement/<br>References/PaxReferences/PaxReference		| 1..n	|	|	Passenger reference.|
| @paxRef | 1 		| String| Reference to the passenger.|
| Transportation/Fares/Fare/Options/Option/<br>SpecialSupplements/SpecialSupplement/<br>SupplementCharge		| 0..1	|	|	Details of the special supplement charge.|
| @fixAmount             		| 0..1 		| Decimal| Total fixed amount.|
| @appliesFixAmount             | 1 		| String| The fixed amount applies to: PorReserva(Reservation), PorPasajero(Passenger), PorSegmento(Segment), TarifaBase(Base Fare), Tasas(Taxes), ForAdt(Adult passengers), ForChd(Children passengers), ForInf(Infant passengers).|
| @minFixAmount             		| 0..1 		| Decimal| Minimal fixed amount.|
| @maxFixAmount             		| 0..1 		| Decimal| Maximal fixed amount.|
| @minAmountPercentage             		| 0..1 		| Decimal| Minimal percentage amount.|
| @maxAmountPercentage             		| 0..1 		| Decimal| Maximal percentage amount.|
| @currency             		| 1 		| String| Currency.|
| @percentage             		| 0..1 		| Decimal| Total percentage amount.|
| @percentageApplied             		| 0..1 		| String| The percentage amount applies to: PorReserva(Reservation), PorPasajero(Passenger), PorSegmento(Segment), TarifaBase(Base Fare), Tasas(Taxes), ForAdt(Adult passengers), ForChd(Children passengers), ForInf(Infant passengers).|
| Transportation/Fares/Fare/Options/Option/<br>Emissions  		| 0..1     	|		| Contains a list of Issuances.	|
| Transportation/Fares/Fare/Options/Option/<br>Emissions/Emission  		| 1..n     	|		| Contains the key of the Issuance.|
| @key		| 1		| String	| Key of the Issuance.|
| Transportation/Fares/Fare/<br>AmountBreakdown  		| 1     	|		| Breakdown of the fare amount.		|
| @currency              		| 1 		| String	| Currency code of the fare.				|
| @totalAmount           		| 1 		| Decimal	| Total amount. with taxes and other charges included.	|
| @notCommissionableAmount		| 1 		| Decimal	| Total amount that can not be commissioned.  		|
| @commission            		| 1 		| Decimal	| Commission. 						|
| Transportation/Fares/Fare/<br>AmountBreakdown/ChargeBreakdowns | 0..1   |		| Contains a list of breakdown amounts ( taxes, mandatory charges.. ).	|
| Transportation/Fares/Fare/<br>AmountBreakdown/ChargeBreakdowns/<br>ChargeBreakdown | 1..n |	| Contains details of the BreakdownAmount.	|
| @type                  		| 1 		| String	| [Type of charge.](#availability-enumerate-description) |
| @amount                		| 1    	 	| Decimal	| Charge amount.				|
| @included				| 1		| Boolean	| If true, the charge is included to the total fare amount |
| Transportation/Fares/Fare/<br>AmountBreakdown/ChargeBreakdowns/<br>ChargeBreakdown/Concept | 0..1 | | Contains details of the charge.|
| @id                    		| 1 		| String	| Unique id of the Concept	|
| @language              		| 1 		| String	| Language.			|
| @cia              		| 0..1 		| String	| Carrier.			|
| @code              		| 0..1 		| String	| Concept code.			|
| Transportation/Fares/Fare/<br>AmountBreakdown/ChargeBreakDowns/<br>ChargeBreakdown/Concept/Text | 0..1 | String | Remarks.	|
| Transportation/Fares/Fare/<br>AmountBreakdown/ChargeBreakDowns/<br>ChargeBreakdown/Concept/Paragraph | 0..n |  | Contains a list of Sentences and titles.	|
| @title	| 0..1	| String	| Title.	|
| Transportation/Fares/Fare/<br>AmountBreakdown/ChargeBreakDowns/<br>ChargeBreakdown/Concept/Paragraph/<br>Sentence | 0..n | String | Sentence|
| Transportation/Fares/Fare/<br>AmountBreakdown/PaxBreakdown | 1    	|		| Contains a list of breakdown amounts for each passenger ( ADT amount, etc. ).|
| Transportation/Fares/Fare/<br>AmountBreakdown/PaxBreakdowns/<br>PaxBreakdown | 1..n | 	| Contains details of breakdown amounts for each passenger.|
| @paxType               		| 1 		| String	| Passenger type: ADT ( Adult ), CHD ( Child ) & INF ( Infant ).|
| @amount                		| 1 		| Decimal	| Total amount, with taxes included, associated to the passenger.	|
| @taxes                 		| 1 		| Decimal	| If they exist, taxes are applied for this passenger type. |
| @tasaDU                		| 0..1 		| Decimal	| DU taxes. 						|
| @fees                			| 0..1 		| Decimal	| Fees. 						|
| Transportation/Fares/Fare/<br>AmountBreakdown/PaxBreakdowns/<br>PaxBreakdown/Taxes | 0..1 | 	| Contains a list of Taxes.|
| Transportation/Fares/Fare/<br>AmountBreakdown/PaxBreakdowns/<br>PaxBreakdown/Taxes/Tax | 1..n | 	| Code and amount of each tax.|
| @code				| 1	| String	| Code.	|
| @amount				| 1	| Decimal	| Amount.	|
| Transportation/Fares/Fare/<br>PaxConfigurations		| 1     	|		| Contains a list of PaxConfiguration.	|
| Transportation/Fares/Fare/<br>PaxConfigurations/PaxConfiguration | 1..n |   		| Contains details of PaxConfiguration.	|
| @id                    		| 1 		| Integer	| Unique identifier of the PaxConfiguration. 		|
| @paxRef                		| 1 		| Integer	| Reference to the passenger Id from the request. 	|
| @age                   		| 0..1 		| Integer	| Age of the passenger. 				|
| @nacionality                   	| 0..1 		| String	| Nacionality of the passenger. 			|
| @paxType               		| 1 		| String	| Passenger type based on the age of the passenger: ADT (Adult), CHD (Child), INF (Infant), YOU (Young) and SEN (Senior).	|
| Transportation/Fares/Fare/<br>PaxConfigurations/PaxConfiguration/<br>AppliedBonuses | 0..1 | | Applied discounts.			|
| @resident              	| 1 		| String	| [Resident discount type.](#availability-enumerate-description)|
| @largeFamily           		| 1 		| String	| Family discount type: N(None), F1(Large family), F2 (Special large family). |
| @discountCardCode		| 0..1	| String	| Discount card code.|
| @discountCard		| 1	| String	| [Discount card type.](#availability-enumerate-description)|
| Transportation/Fares/Fare/<br>PaxConfigurations/PaxConfiguration/<br>AppliedBonuses/DiscountCards	| 0..1	|	| Contains a list of DiscountCards.|
| Transportation/Fares/Fare/<br>PaxConfigurations/PaxConfiguration/<br>AppliedBonuses/DiscountCards/<br>DiscountCard| 1..n	|	| DiscountCard details.|
| @code	| 0..1	| String | Discount card code.|
| @id	| 1	| String	| Unique identifier of discound card.|
| @type	| 1	| String	| [Discount card type.](#availability-enumerate-description)|
| Fares/Fare/PaxConfigurations<br>/PaxConfiguration/PaxConfiguration/<br>AppliedBonuses/PaxTypeCodes		| 0..1	|		| Contains a list of PaxTypeCodes.|
| Transportation/Fares/Fare/<br>PaxConfigurations/PaxConfiguration/<br>AppliedBonuses/PaxTypeCodes/<br>PaxTypeCode	| 1..n	|	| Contains the code type of the passenger.|
| @code		| 1		| String	| Code type of the passenger.|


### Availability Enumerate description

| **Element**				| **Possible Values**	| **Description**	|
| ------------------------- | --------------------- | ------------------ |
| @discountCard        					| N | None |
| 							| NINYO |  |
| 							| JOVEN | |
| 							| ESCAPADA | |
| 							| SENIOR | |
| 							| THALYS_CORPORATE | |
| 							| FORFAIT_LYS | |
| 							| ABO_FREQUENCE_1ST_AND_2ND | |
| 							| ABO_FORFAIT_1ST_AND_2ND | |
| 							| BAHN_CARD_REDUCTION | |
| 							| BAHN_CARD_25 | |
| 							| SWITZERLAND_50 | |
| 							| SWITZERLAND_100 | |
| 							| EJERCITO_AIRE | |
| 							| EJERCITO_TIERRA | |
| 							| FUERZAS_NAVALES | |
| 							| GUARDIA_CIVIL | |
| 							| FREQUENT_FLYER | |
| 							| CARTA_ARGENTO | |
| 							| CARTA_FRECCIA | |
| 							| UK_ANNUAL_GOLD | |
| 							| UK_CHILD_DISABILITY | |
| 							| UK_DISABILITY | |
| 							| UK_FAMILY_FRIENDS | |
| 							| UK_GROUPSAVE3 | |
| 							| UK_GROUPSAVE4 | |
| 							| UK_HM_ARMED_FORCES | |
| 							| UK_JOBCENTRE_PLUS | |
| 							| UK_NETWORK | |
| 							| UK_SENIOR | |
| 							| UK_TWO_TOGETHER | |
| 							| UK_YOUTH | |
| 							| UK_GROUPSAVE | |
| @resident						| N | None |
| 							| BP | Balearic Islands resident flying to mainland |
| 							| BI | Balearic Islands resident flying to another balearic island |
| 							| DC | Canarian Islands resident flying to another Canarian Island |
| 							| RC | Canarian Islands resident flying to mainland |
| 							| RM | Ceuta/Melilla resident |
| 							| STR | Italian resident  discount |
| 							| ELB | Italian resident Elba |
| 							| SDG | Italian resident Sardegna |
| 							| SLC | Italian resident Sicily |
| 							| RE | Ceuta |
| Vehicles/Vehicle/@type				| N  | None  |
| 							| Turismo  | Touring  |
| 							| Todoterreno  | All terrain  |
| 							| Monovolumen  | Minivan  |
| 							| CiclomotorMax50  | Moped max 50kg.  |
| 							| MotocicletaMin50Max250  | Motorcicle min 50kg. max 250kg.  |
| 							| MotocicletaMin250Max500  | Motorcicle min 250kg. max 500kg.  |
| 							| MotocicletaMin500  | Motorcicle min 500kg.  |
| 							| Bicicleta  | Bike  |
| 							| Furgoneta  | Van  |
| 							| VehiculoLargoMax6  | Long vehicle max 6m.  |
| 							| VehiculoEmision0  | Zero emissions vehicle  |
| 							| Caravana  | Caravan  |
| 							| Remolque  | Trailer  |
| Fares/Fare/AmountBreakdown<br>/ChargeBreakdowns/ChargeBreakdown/@type				| TASA  | Tax  |
| 							| TARJETA  | Card  |
| 							| EQUIPAJE  | Baggage  |
| 							| CHECKIN  | Checkin  |
| 							| GASTOS_CIA  | Carrier charges  |
| 							| TASA_DU  | DU Taxes  |
| 							| IMPORTE_BASE  | Base import  |
| 							| DESCUENTO  | Discount  |
| 							| VEHICULO  | Vehicle  |
| 							| GASTOS_BANCARIOS  | Bank charges  |
| 							| GASTOS_CONVERSION_DIVISA  | Currency conversion charges  |
| 							| FEE_VEHICULO  | Vehicle fee  |
| 							| FEE  | Fee  |
| 							| ASIENTO  | Seat  |
| 							| SUPLEMENTO  | Supplement  |
| 							| TRAVELCARD  | Travel card  |
| 							| MASCOTA  | Pet  |
| 							| FEE_MASCOTA  | Pet fee  |
| 							| SEGURO  | Ensurance  |
| 							| ACCESO_PREFERENTE  | Fast Track  |
| 							| EMBARQUE_PRIORITARIO  | Priority Boarding  |
| 							| BLOQUEO_TARIFA  | Fare lock |
| 							| ASISTENCIA_ESPECIAL  | Special assistance  |
| 							| PENALTY  | Penalty  |


### Detailed description


**Total amount breakdown:**

The totalAmount from AmountBreakdown can be calculated by simply adding
the prices of each amount attribute from every PaxBreakdown.

Please note, that the amount as already had in consideration the taxes,
therefore, if the total price marks a 100€, and the taxes are 10€, then
the base price is 90€, like so:

  Pax Breakdown:

 Adult     |      Amount: 100€      |   tax: 10€

Total amount: 100€ Tax: 10€ Pax amount: 100€ - 10€ = 90€



**How to calculate a breakdown:**

Lets say for example we want to calculate the breakdown of the paxes,
then the amount will be the sum of all of the paxes price multiplied by
the number paxes.

For example, if the prices for each pax type are:

Paxes breakdown:                             

| Adult       |  Amount: 100€     |    tax: 10€  |
| Child       |  Amount: 50€      |    tax: 10€  |
| Infant      |  Amount: 10€      |    tax: 10€  |

And we want to do a booking for two adults, two kids and one baby, the
configuration of the paxes will be:


Paxes configuration:                        

| Adult    |    Attribute   |   Bonus  |
| Adult    |    Attribute   |   Bonus  |
| Child    |    Attribute   |   Bonus  |
| Child    |    Attribute   |   Bonus  |
| Infant   |    Attribute   |   Bonus  |

Therefore the total price will be:


Amount breakdown:

| Total  |  Amount: (DesgloseADT \* numADT) + (DesgloseCHD \* numCHD) + (DesgloseINF \* numINF) = **310€**



### Possible Operations (Examples)

**Operation 1 - One way request:**

Search for 1 journey with 1 adult (ADT), 1 child (CHD) and 1 infant (INF).

AvailabilityRQ:

~~~xml
<AvailabilityRQ travelType="OW">
	<Journeys>
		<Journey id="0" departureDate="18/12/2018" departureTime="" action="N">
			<OriginLoc type="A" code="PMI" cityCode="false"/>
			<DestinationLoc type="A" code="MAD" cityCode="false"/>
		</Journey>
	</Journeys>
	<Passengers>
		<Passenger id="0" age="30">
			<Bonuses resident="N" largeFamily="N" discountCard="N"/>
		</Passenger>
		<Passenger id="1" age="8">
			<Bonuses resident="N" largeFamily="N" discountCard="N"/>
		</Passenger>
		<Passenger id="2" age="1">
			<Bonuses resident="N" largeFamily="N" discountCard="N"/>
		</Passenger>
	</Passengers>
	<Preferences cabinClass="N" lowCostIncluded="false" onlyNonStop="false" onlyTrain="false" allowOverNight="false" trainIncluded="false" cheapestFares="false" brandedFares="false">
		<lightAvail>false</lightAvail>
	</Preferences>
</AvailabilityRQ>
~~~

AvailabilityRS:

~~~xml
<AvailabilityRS>
	<Transportation totalFares="2">
		<Segments>
			<Segment id="0" transportationId="D86770" transportationType="A" operatingCarrier="D8" marketingCarrier="D8" arrivalTerminal="2" departureDate="2018-12-18T07:25:00" arrivalDate="2018-12-18T08:50:00" segmentDuration="0" maxCheckinDate="0001-01-01T00:00:00" planeType="73H" segmentStatus="HK" electronicTicket="true" hasTechnicalStop="false" secureFlight="false">
				<OriginLoc type="A" code="PMI" cityCode="false"/>
				<DestinationLoc type="A" code="MAD" cityCode="false"/>
			</Segment>
			<Segment id="1" transportationId="UX6072" transportationType="A" operatingCarrier="UX" marketingCarrier="UX" arrivalTerminal="1" departureDate="2018-12-18T17:05:00" arrivalDate="2018-12-18T17:55:00" segmentDuration="0" maxCheckinDate="0001-01-01T00:00:00" planeType="73H" segmentStatus="HK" electronicTicket="true" hasTechnicalStop="false" secureFlight="false">
				<OriginLoc type="A" code="PMI" cityCode="false"/>
				<DestinationLoc type="A" code="BCN" cityCode="false"/>
			</Segment>
			<Segment id="2" transportationId="UX2159" transportationType="A" operatingCarrier="UX" marketingCarrier="UX" departureTerminal="1" arrivalTerminal="2" departureDate="2018-12-18T20:40:00" arrivalDate="2018-12-18T22:05:00" segmentDuration="0" maxCheckinDate="0001-01-01T00:00:00" planeType="332" segmentStatus="HK" electronicTicket="true" hasTechnicalStop="false" secureFlight="false">
				<OriginLoc type="A" code="BCN" cityCode="false"/>
				<DestinationLoc type="A" code="MAD" cityCode="false"/>
			</Segment>
			<Segment id="3" transportationId="UX6060" transportationType="A" operatingCarrier="UX" marketingCarrier="UX" arrivalTerminal="1" departureDate="2018-12-18T13:30:00" arrivalDate="2018-12-18T14:20:00" segmentDuration="0" maxCheckinDate="0001-01-01T00:00:00" planeType="73H" segmentStatus="HK" electronicTicket="true" hasTechnicalStop="false" secureFlight="false">
				<OriginLoc type="A" code="PMI" cityCode="false"/>
				<DestinationLoc type="A" code="BCN" cityCode="false"/>
			</Segment>
		</Segments>
		<Fares>
			<Fare id="0" providerCode="AMD" fareType="OW">
				<Conditions>
					<Condition id="PEN">
						<Text>TICKETS ARE NON-REFUNDABLE</Text>
					</Condition>
					<Condition id="LTD">
						<Text>LAST TKT DTE, 11DEC18, - SEE ADV PURCHASE</Text>
					</Condition>
				</Conditions>
				<Options>
					<Option id="0" availabilityJourneyRef="0" numStopOvers="0" carrier="DY">
						<SegmentReferences>
							<SegmentReference segmentRef="0">
								<SegmentClasses>
									<SegmentClass cabinClass="Y" class="T" paxRef="0" fareBasis="TJIPPI" fareType="PUB" avail="9"/>
									<SegmentClass cabinClass="Y" class="T" paxRef="1" fareBasis="TJIPPI" fareType="PUB" avail="9"/>
									<SegmentClass cabinClass="Y" class="T" paxRef="2" fareBasis="TJIPPI" fareType="PUB" avail="9"/>
								</SegmentClasses>
								<ReservationTokens>
									<Attribute key="LtdProv" value="111218"/>
									<Attribute key="Ltd" value="11/12/2018"/>
									<Attribute key="claseCabina" value="N"/>
									<Attribute key="breakPoint" value="Y"/>
									<Attribute key="fareType" value="PUB"/>
								</ReservationTokens>
							</SegmentReference>
						</SegmentReferences>
						<Emissions/>
						<BaggageTypes>
							<BaggageType checkinType="OnLine" appliesSegments="Ref">
								<References>
									<SegmentReferences>
										<SegmentReference itineraryRef="0" journeyRef="0" segmentRef="0"/>
									</SegmentReferences>
								</References>
								<Baggage type="Bag" quantity="2" maxWeightPerUnit="0" maxTotalWeight="0" paymentInAirport="false" needToken="false"/>
							</BaggageType>
						</BaggageTypes>
					</Option>
				</Options>
				<AmountBreakdown currency="EUR" totalAmount="98.23" nonCommissionableAmount="0" commission="-1">
					<ChargeBreakdowns/>
					<PaxBreakdowns>
						<PaxBreakdown paxType="ADT" amount="45.01" taxes="10.01" fees="0" tasaDU="0"/>
						<PaxBreakdown paxType="CHD" amount="45.01" taxes="10.01" fees="0" tasaDU="0"/>
						<PaxBreakdown paxType="INF" amount="8.21" taxes="8.21" fees="0" tasaDU="0"/>
					</PaxBreakdowns>
				</AmountBreakdown>
				<PaxConfigurations>
					<PaxConfiguration id="0" paxRef="0" age="30" paxType="ADT">
						<AppliedBonuses resident="N" largeFamily="N" discountCard="N"/>
					</PaxConfiguration>
					<PaxConfiguration id="1" paxRef="1" age="8" paxType="CHD">
						<AppliedBonuses resident="N" largeFamily="N" discountCard="N"/>
					</PaxConfiguration>
					<PaxConfiguration id="2" paxRef="2" age="1" paxType="INF">
						<AppliedBonuses resident="N" largeFamily="N" discountCard="N"/>
					</PaxConfiguration>
				</PaxConfigurations>
				<HasObFees>false</HasObFees>
			</Fare>
			<Fare id="1" providerCode="AMD" fareType="OW">
				<Conditions>
					<Condition id="PEN">
						<Text>TICKETS ARE NON-REFUNDABLE</Text>
					</Condition>
					<Condition id="LTD">
						<Text>LAST TKT DTE, 12DEC18, - SEE ADV PURCHASE</Text>
					</Condition>
					<Condition id="APM">
						<Text>PRIVATE RATES USED *F*</Text>
					</Condition>
				</Conditions>
				<Options>
					<Option id="0" availabilityJourneyRef="0" numStopOvers="1" carrier="UX">
						<SegmentReferences>
							<SegmentReference segmentRef="1">
								<SegmentClasses>
									<SegmentClass cabinClass="Y" class="Z" paxRef="0" fareBasis="ZDPROW5L" fareType="PRI" avail="9"/>
									<SegmentClass cabinClass="Y" class="Z" paxRef="1" fareBasis="ZDPROW5L" fareType="PRI" avail="9"/>
									<SegmentClass cabinClass="Y" class="Z" paxRef="2" fareBasis="ZDPROW5L" fareType="PRI" avail="9"/>
								</SegmentClasses>
								<ReservationTokens>
									<Attribute key="LtdProv" value="121218"/>
									<Attribute key="Ltd" value="12/12/2018"/>
									<Attribute key="claseCabina" value="N"/>
									<Attribute key="breakPoint" value="Y"/>
									<Attribute key="fareType" value="PRI"/>
								</ReservationTokens>
							</SegmentReference>
							<SegmentReference segmentRef="2">
								<SegmentClasses>
									<SegmentClass cabinClass="Y" class="Z" paxRef="0" fareBasis="ZDOW5L" fareType="PRI" avail="9"/>
									<SegmentClass cabinClass="Y" class="Z" paxRef="1" fareBasis="ZDOW5L" fareType="PRI" avail="9"/>
									<SegmentClass cabinClass="Y" class="Z" paxRef="2" fareBasis="ZDOW5L" fareType="PRI" avail="9"/>
								</SegmentClasses>
								<ReservationTokens>
									<Attribute key="LtdProv" value="121218"/>
									<Attribute key="Ltd" value="12/12/2018"/>
									<Attribute key="claseCabina" value="N"/>
									<Attribute key="breakPoint" value="Y"/>
									<Attribute key="fareType" value="PRI"/>
								</ReservationTokens>
							</SegmentReference>
						</SegmentReferences>
						<Emissions/>
						<BaggageTypes>
							<BaggageType checkinType="OnLine" appliesSegments="Ref">
								<References>
									<SegmentReferences>
										<SegmentReference itineraryRef="0" journeyRef="0" segmentRef="1"/>
										<SegmentReference itineraryRef="0" journeyRef="0" segmentRef="2"/>
									</SegmentReferences>
								</References>
								<Baggage type="Bag" quantity="0" maxWeightPerUnit="0" maxTotalWeight="0" paymentInAirport="false" needToken="false"/>
							</BaggageType>
						</BaggageTypes>
					</Option>
					<Option id="1" availabilityJourneyRef="0" numStopOvers="1" carrier="UX">
						<SegmentReferences>
							<SegmentReference segmentRef="3">
								<SegmentClasses>
									<SegmentClass cabinClass="Y" class="Z" paxRef="0" fareBasis="ZDPROW5L" fareType="PRI" avail="9"/>
									<SegmentClass cabinClass="Y" class="Z" paxRef="1" fareBasis="ZDPROW5L" fareType="PRI" avail="9"/>
									<SegmentClass cabinClass="Y" class="Z" paxRef="2" fareBasis="ZDPROW5L" fareType="PRI" avail="9"/>
								</SegmentClasses>
								<ReservationTokens>
									<Attribute key="LtdProv" value="121218"/>
									<Attribute key="Ltd" value="12/12/2018"/>
									<Attribute key="claseCabina" value="N"/>
									<Attribute key="breakPoint" value="Y"/>
									<Attribute key="fareType" value="PRI"/>
								</ReservationTokens>
							</SegmentReference>
							<SegmentReference segmentRef="2">
								<SegmentClasses>
									<SegmentClass cabinClass="Y" class="Z" paxRef="0" fareBasis="ZDOW5L" fareType="PRI" avail="9"/>
									<SegmentClass cabinClass="Y" class="Z" paxRef="1" fareBasis="ZDOW5L" fareType="PRI" avail="9"/>
									<SegmentClass cabinClass="Y" class="Z" paxRef="2" fareBasis="ZDOW5L" fareType="PRI" avail="9"/>
								</SegmentClasses>
								<ReservationTokens>
									<Attribute key="LtdProv" value="121218"/>
									<Attribute key="Ltd" value="12/12/2018"/>
									<Attribute key="claseCabina" value="N"/>
									<Attribute key="breakPoint" value="Y"/>
									<Attribute key="fareType" value="PRI"/>
								</ReservationTokens>
							</SegmentReference>
						</SegmentReferences>
						<Emissions/>
						<BaggageTypes>
							<BaggageType checkinType="OnLine" appliesSegments="Ref">
								<References>
									<SegmentReferences>
										<SegmentReference itineraryRef="0" journeyRef="0" segmentRef="3"/>
										<SegmentReference itineraryRef="0" journeyRef="0" segmentRef="2"/>
									</SegmentReferences>
								</References>
								<Baggage type="Bag" quantity="0" maxWeightPerUnit="0" maxTotalWeight="0" paymentInAirport="false" needToken="false"/>
							</BaggageType>
						</BaggageTypes>
					</Option>
				</Options>
				<AmountBreakdown currency="EUR" totalAmount="126.66" nonCommissionableAmount="0" commission="-1">
					<ChargeBreakdowns/>
					<PaxBreakdowns>
						<PaxBreakdown paxType="ADT" amount="51.22" taxes="20.22" fees="0" tasaDU="0"/>
						<PaxBreakdown paxType="CHD" amount="51.22" taxes="20.22" fees="0" tasaDU="0"/>
						<PaxBreakdown paxType="INF" amount="24.22" taxes="20.22" fees="0" tasaDU="0"/>
					</PaxBreakdowns>
				</AmountBreakdown>
				<PaxConfigurations>
					<PaxConfiguration id="0" paxRef="0" age="30" paxType="ADT">
						<AppliedBonuses resident="N" largeFamily="N" discountCard="N"/>
					</PaxConfiguration>
					<PaxConfiguration id="1" paxRef="1" age="8" paxType="CHD">
						<AppliedBonuses resident="N" largeFamily="N" discountCard="N"/>
					</PaxConfiguration>
					<PaxConfiguration id="2" paxRef="2" age="1" paxType="INF">
						<AppliedBonuses resident="N" largeFamily="N" discountCard="N"/>
					</PaxConfiguration>
				</PaxConfigurations>
				<HasObFees>false</HasObFees>
			</Fare>
		</Fares>
	</Transportation>
</AvailabilityRS>
~~~

**Operation 2 - Round trip request:**

Search for 2 journies, outbound destination = inbound origin,  with 2 adults (ADT).

AvailabilityRQ:

~~~xml
<AvailabilityRQ travelType="RT">
  <Journeys>
    <Journey id="0" departureDate="18/12/2018" departureTime="" action="N">
      <OriginLoc type="A" code="PMI" cityCode="false"/>
      <DestinationLoc type="A" code="MAD" cityCode="false"/>
    </Journey>
    <Journey id="1" departureDate="25/12/2018" departureTime="" action="N">
      <OriginLoc type="A" code="MAD" cityCode="false"/>
      <DestinationLoc type="A" code="PMI" cityCode="false"/>
    </Journey>
  </Journeys>
  <Passengers>
    <Passenger id="0" age="30">
      <Bonuses resident="N" largeFamily="N" discountCard="N"/>
    </Passenger>
    <Passenger id="1" age="30">
      <Bonuses resident="N" largeFamily="N" discountCard="N"/>
    </Passenger>
  </Passengers>
  <Preferences cabinClass="N" lowCostIncluded="false" onlyNonStop="false" onlyTrain="false" allowOverNight="false" trainIncluded="false" cheapestFares="false" brandedFares="false">
    <lightAvail>false</lightAvail>
  </Preferences>
</AvailabilityRQ>
~~~

AvailabilityRS:

~~~xml
<AvailabilityRS>
  <Transportation totalFares="3">
    <Segments>
      <Segment id="0" transportationId="D86770" transportationType="A" operatingCarrier="D8" marketingCarrier="D8" arrivalTerminal="2" departureDate="2018-12-18T07:25:00" arrivalDate="2018-12-18T08:50:00" segmentDuration="0" maxCheckinDate="0001-01-01T00:00:00" planeType="73H" segmentStatus="HK" electronicTicket="true" hasTechnicalStop="false" secureFlight="false">
        <OriginLoc type="A" code="PMI" cityCode="false"/>
        <DestinationLoc type="A" code="MAD" cityCode="false"/>
      </Segment>
      <Segment id="1" transportationId="UX6096" transportationType="A" operatingCarrier="UX" marketingCarrier="UX" arrivalTerminal="2" departureDate="2018-12-18T21:00:00" arrivalDate="2018-12-18T22:25:00" segmentDuration="0" maxCheckinDate="0001-01-01T00:00:00" planeType="73H" segmentStatus="HK" electronicTicket="true" hasTechnicalStop="false" secureFlight="false">
        <OriginLoc type="A" code="PMI" cityCode="false"/>
        <DestinationLoc type="A" code="MAD" cityCode="false"/>
      </Segment>
      <Segment id="2" transportationId="UX6031" transportationType="A" operatingCarrier="UX" marketingCarrier="UX" departureTerminal="2" departureDate="2018-12-25T08:30:00" arrivalDate="2018-12-25T09:50:00" segmentDuration="0" maxCheckinDate="0001-01-01T00:00:00" planeType="E90" segmentStatus="HK" electronicTicket="true" hasTechnicalStop="false" secureFlight="false">
        <OriginLoc type="A" code="MAD" cityCode="false"/>
        <DestinationLoc type="A" code="PMI" cityCode="false"/>
      </Segment>
      <Segment id="3" transportationId="UX6013" transportationType="A" operatingCarrier="UX" marketingCarrier="UX" departureTerminal="2" departureDate="2018-12-25T10:15:00" arrivalDate="2018-12-25T11:35:00" segmentDuration="0" maxCheckinDate="0001-01-01T00:00:00" planeType="73H" segmentStatus="HK" electronicTicket="true" hasTechnicalStop="false" secureFlight="false">
        <OriginLoc type="A" code="MAD" cityCode="false"/>
        <DestinationLoc type="A" code="PMI" cityCode="false"/>
      </Segment>
      <Segment id="4" transportationId="UX6067" transportationType="A" operatingCarrier="UX" marketingCarrier="UX" departureTerminal="2" departureDate="2018-12-25T13:50:00" arrivalDate="2018-12-25T15:10:00" segmentDuration="0" maxCheckinDate="0001-01-01T00:00:00" planeType="73H" segmentStatus="HK" electronicTicket="true" hasTechnicalStop="false" secureFlight="false">
        <OriginLoc type="A" code="MAD" cityCode="false"/>
        <DestinationLoc type="A" code="PMI" cityCode="false"/>
      </Segment>
      <Segment id="5" transportationId="UX6049" transportationType="A" operatingCarrier="UX" marketingCarrier="UX" departureTerminal="2" departureDate="2018-12-25T21:45:00" arrivalDate="2018-12-25T23:05:00" segmentDuration="0" maxCheckinDate="0001-01-01T00:00:00" planeType="73H" segmentStatus="HK" electronicTicket="true" hasTechnicalStop="false" secureFlight="false">
        <OriginLoc type="A" code="MAD" cityCode="false"/>
        <DestinationLoc type="A" code="PMI" cityCode="false"/>
      </Segment>
    </Segments>
    <Fares>
      <Fare id="0" providerCode="AMD" fareType="OW">
        <Conditions>
          <Condition id="PEN">
            <Text>TICKETS ARE NON-REFUNDABLE</Text>
          </Condition>
          <Condition id="LTD">
            <Text>LAST TKT DTE, 11DEC18,  - SEE ADV PURCHASE</Text>
          </Condition>
        </Conditions>
        <Options>
          <Option id="0" availabilityJourneyRef="0" numStopOvers="0" carrier="DY">
            <SegmentReferences>
              <SegmentReference segmentRef="0">
                <SegmentClasses>
                  <SegmentClass cabinClass="Y" class="T" paxRef="0" fareBasis="TJIPPI" fareType="PUB" avail="9"/>
                  <SegmentClass cabinClass="Y" class="T" paxRef="1" fareBasis="TJIPPI" fareType="PUB" avail="9"/>
                </SegmentClasses>
                <ReservationTokens>
                  <Attribute key="LtdProv" value="111218"/>
                  <Attribute key="Ltd" value="11/12/2018"/>
                  <Attribute key="claseCabina" value="N"/>
                  <Attribute key="breakPoint" value="Y"/>
                  <Attribute key="fareType" value="PUB"/>
                </ReservationTokens>
              </SegmentReference>
            </SegmentReferences>
            <Emissions/>
            <BaggageTypes>
              <BaggageType checkinType="OnLine" appliesSegments="Ref">
                <References>
                  <SegmentReferences>
                    <SegmentReference itineraryRef="0" journeyRef="0" segmentRef="0"/>
                  </SegmentReferences>
                </References>
                <Baggage type="Bag" quantity="2" maxWeightPerUnit="0" maxTotalWeight="0" paymentInAirport="false" needToken="false"/>
              </BaggageType>
            </BaggageTypes>
          </Option>
        </Options>
        <AmountBreakdown currency="EUR" totalAmount="90.02" nonCommissionableAmount="0" commission="-1">
          <ChargeBreakdowns/>
          <PaxBreakdowns>
            <PaxBreakdown paxType="ADT" amount="45.01" taxes="10.01" fees="0" tasaDU="0"/>
          </PaxBreakdowns>
        </AmountBreakdown>
        <PaxConfigurations>
          <PaxConfiguration id="0" paxRef="0" age="30" paxType="ADT">
            <AppliedBonuses resident="N" largeFamily="N" discountCard="N"/>
          </PaxConfiguration>
          <PaxConfiguration id="1" paxRef="1" age="30" paxType="ADT">
            <AppliedBonuses resident="N" largeFamily="N" discountCard="N"/>
          </PaxConfiguration>
        </PaxConfigurations>
        <HasObFees>false</HasObFees>
      </Fare>
      <Fare id="3" providerCode="AMD" fareType="OW">
        <Conditions>
          <Condition id="PEN">
            <Text>TICKETS ARE NON-REFUNDABLE</Text>
          </Condition>
          <Condition id="LTD">
            <Text>LAST TKT DTE, 12DEC18,  - SEE ADV PURCHASE</Text>
          </Condition>
          <Condition id="APM">
            <Text>PRIVATE RATES USED *F*</Text>
          </Condition>
        </Conditions>
        <Options>
          <Option id="0" availabilityJourneyRef="1" numStopOvers="0" carrier="UX">
            <SegmentReferences>
              <SegmentReference segmentRef="5">
                <SegmentClasses>
                  <SegmentClass cabinClass="Y" class="U" paxRef="0" fareBasis="UDOW5L" fareType="PRI" avail="9"/>
                  <SegmentClass cabinClass="Y" class="U" paxRef="1" fareBasis="UDOW5L" fareType="PRI" avail="9"/>
                </SegmentClasses>
                <ReservationTokens>
                  <Attribute key="LtdProv" value="121218"/>
                  <Attribute key="Ltd" value="12/12/2018"/>
                  <Attribute key="claseCabina" value="N"/>
                  <Attribute key="breakPoint" value="Y"/>
                  <Attribute key="fareType" value="PRI"/>
                </ReservationTokens>
              </SegmentReference>
            </SegmentReferences>
            <Emissions/>
            <BaggageTypes>
              <BaggageType checkinType="OnLine" appliesSegments="Ref">
                <References>
                  <SegmentReferences>
                    <SegmentReference itineraryRef="0" journeyRef="1" segmentRef="64"/>
                  </SegmentReferences>
                </References>
                <Baggage type="Bag" quantity="0" maxWeightPerUnit="0" maxTotalWeight="0" paymentInAirport="false" needToken="false"/>
              </BaggageType>
            </BaggageTypes>
          </Option>
        </Options>
        <AmountBreakdown currency="EUR" totalAmount="220.64" nonCommissionableAmount="0" commission="-1">
          <ChargeBreakdowns/>
          <PaxBreakdowns>
            <PaxBreakdown paxType="ADT" amount="110.32" taxes="20.32" fees="0" tasaDU="0"/>
          </PaxBreakdowns>
        </AmountBreakdown>
        <PaxConfigurations>
          <PaxConfiguration id="0" paxRef="0" age="30" paxType="ADT">
            <AppliedBonuses resident="N" largeFamily="N" discountCard="N"/>
          </PaxConfiguration>
          <PaxConfiguration id="1" paxRef="1" age="30" paxType="ADT">
            <AppliedBonuses resident="N" largeFamily="N" discountCard="N"/>
          </PaxConfiguration>
        </PaxConfigurations>
        <HasObFees>false</HasObFees>
      </Fare>
      <Fare id="26" providerCode="AMD" fareType="RT">
        <Conditions>
          <Condition id="PEN">
            <Text>TICKETS ARE NON-REFUNDABLE</Text>
          </Condition>
          <Condition id="LTD">
            <Text>LAST TKT DTE, 12DEC18,  - SEE ADV PURCHASE</Text>
          </Condition>
          <Condition id="APM">
            <Text>PRIVATE RATES USED *F*</Text>
          </Condition>
        </Conditions>
        <Options>
          <Option id="0" availabilityJourneyRef="0" numStopOvers="0" carrier="UX">
            <SegmentReferences>
              <SegmentReference segmentRef="1">
                <SegmentClasses>
                  <SegmentClass cabinClass="Y" class="N" paxRef="0" fareBasis="NSUBRT5L" fareType="PRI" avail="9"/>
                  <SegmentClass cabinClass="Y" class="N" paxRef="1" fareBasis="NSUBRT5L" fareType="PRI" avail="9"/>
                </SegmentClasses>
                <ReservationTokens>
                  <Attribute key="LtdProv" value="121218"/>
                  <Attribute key="Ltd" value="12/12/2018"/>
                  <Attribute key="claseCabina" value="N"/>
                  <Attribute key="breakPoint" value="Y"/>
                  <Attribute key="fareType" value="PRI"/>
                </ReservationTokens>
              </SegmentReference>
            </SegmentReferences>
            <Emissions/>
            <BaggageTypes>
              <BaggageType checkinType="OnLine" appliesSegments="Ref">
                <References>
                  <SegmentReferences>
                    <SegmentReference itineraryRef="0" journeyRef="0" segmentRef="31"/>
                  </SegmentReferences>
                </References>
                <Baggage type="Bag" quantity="0" maxWeightPerUnit="0" maxTotalWeight="0" paymentInAirport="false" needToken="false"/>
              </BaggageType>
            </BaggageTypes>
          </Option>
          <Option id="1" availabilityJourneyRef="1" numStopOvers="0" carrier="UX">
            <SegmentReferences>
              <SegmentReference segmentRef="2">
                <SegmentClasses>
                  <SegmentClass cabinClass="Y" class="N" paxRef="0" fareBasis="NSUBRT5L" fareType="PRI" avail="9"/>
                  <SegmentClass cabinClass="Y" class="N" paxRef="1" fareBasis="NSUBRT5L" fareType="PRI" avail="9"/>
                </SegmentClasses>
                <ReservationTokens>
                  <Attribute key="LtdProv" value="121218"/>
                  <Attribute key="Ltd" value="12/12/2018"/>
                  <Attribute key="claseCabina" value="N"/>
                  <Attribute key="breakPoint" value="Y"/>
                  <Attribute key="fareType" value="PRI"/>
                </ReservationTokens>
              </SegmentReference>
            </SegmentReferences>
            <Emissions/>
            <BaggageTypes>
              <BaggageType checkinType="OnLine" appliesSegments="Ref">
                <References>
                  <SegmentReferences>
                    <SegmentReference itineraryRef="0" journeyRef="1" segmentRef="55"/>
                  </SegmentReferences>
                </References>
                <Baggage type="Bag" quantity="0" maxWeightPerUnit="0" maxTotalWeight="0" paymentInAirport="false" needToken="false"/>
              </BaggageType>
            </BaggageTypes>
          </Option>
          <Option id="2" availabilityJourneyRef="1" numStopOvers="0" carrier="UX">
            <SegmentReferences>
              <SegmentReference segmentRef="3">
                <SegmentClasses>
                  <SegmentClass cabinClass="Y" class="N" paxRef="0" fareBasis="NSUBRT5L" fareType="PRI" avail="9"/>
                  <SegmentClass cabinClass="Y" class="N" paxRef="1" fareBasis="NSUBRT5L" fareType="PRI" avail="9"/>
                </SegmentClasses>
                <ReservationTokens>
                  <Attribute key="LtdProv" value="121218"/>
                  <Attribute key="Ltd" value="12/12/2018"/>
                  <Attribute key="claseCabina" value="N"/>
                  <Attribute key="breakPoint" value="Y"/>
                  <Attribute key="fareType" value="PRI"/>
                </ReservationTokens>
              </SegmentReference>
            </SegmentReferences>
            <Emissions/>
            <BaggageTypes>
              <BaggageType checkinType="OnLine" appliesSegments="Ref">
                <References>
                  <SegmentReferences>
                    <SegmentReference itineraryRef="0" journeyRef="1" segmentRef="56"/>
                  </SegmentReferences>
                </References>
                <Baggage type="Bag" quantity="0" maxWeightPerUnit="0" maxTotalWeight="0" paymentInAirport="false" needToken="false"/>
              </BaggageType>
            </BaggageTypes>
          </Option>
          <Option id="3" availabilityJourneyRef="1" numStopOvers="0" carrier="UX">
            <SegmentReferences>
              <SegmentReference segmentRef="4">
                <SegmentClasses>
                  <SegmentClass cabinClass="Y" class="N" paxRef="0" fareBasis="NSUBRT5L" fareType="PRI" avail="9"/>
                  <SegmentClass cabinClass="Y" class="N" paxRef="1" fareBasis="NSUBRT5L" fareType="PRI" avail="9"/>
                </SegmentClasses>
                <ReservationTokens>
                  <Attribute key="LtdProv" value="121218"/>
                  <Attribute key="Ltd" value="12/12/2018"/>
                  <Attribute key="claseCabina" value="N"/>
                  <Attribute key="breakPoint" value="Y"/>
                  <Attribute key="fareType" value="PRI"/>
                </ReservationTokens>
              </SegmentReference>
            </SegmentReferences>
            <Emissions/>
            <BaggageTypes>
              <BaggageType checkinType="OnLine" appliesSegments="Ref">
                <References>
                  <SegmentReferences>
                    <SegmentReference itineraryRef="0" journeyRef="1" segmentRef="57"/>
                  </SegmentReferences>
                </References>
                <Baggage type="Bag" quantity="0" maxWeightPerUnit="0" maxTotalWeight="0" paymentInAirport="false" needToken="false"/>
              </BaggageType>
            </BaggageTypes>
          </Option>
        </Options>
        <AmountBreakdown currency="EUR" totalAmount="196.24" nonCommissionableAmount="0" commission="-1">
          <ChargeBreakdowns/>
          <PaxBreakdowns>
            <PaxBreakdown paxType="ADT" amount="98.12" taxes="28.12" fees="0" tasaDU="0"/>
          </PaxBreakdowns>
        </AmountBreakdown>
        <PaxConfigurations>
          <PaxConfiguration id="0" paxRef="0" age="30" paxType="ADT">
            <AppliedBonuses resident="N" largeFamily="N" discountCard="N"/>
          </PaxConfiguration>
          <PaxConfiguration id="1" paxRef="1" age="30" paxType="ADT">
            <AppliedBonuses resident="N" largeFamily="N" discountCard="N"/>
          </PaxConfiguration>
        </PaxConfigurations>
        <HasObFees>false</HasObFees>
      </Fare>
    </Fares>
  </Transportation>
  <OptionalsCharges/>
</AvailabilityRS>
~~~