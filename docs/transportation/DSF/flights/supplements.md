---
title: Supplements
keywords: transportation, data structure, flights, supplements
search: Transportation - Flights - Data Structure - Supplements
sidebar: mydoc_sidebar
permalink: /docs/transportation/DSF/flights/supplements
---



### Method Goals


This method aims to get the available supplements and their price information (before or after a reservation has been done).


### Request Format

The Supplements request can be done by two different ways: with a group of Itineraries (before a reservation) or with a booking locator (after a reservation).

### Response Format

The result returns a list of the available supplements (seats, baggage, fare rules, payment methods, etc.)

### Remarks

Not implemented by all suppliers


### SupplementsRQ Description



| **Element** 						| **Number**| **Type**	| **Description**															|
| --------------------------------- | ----------| ----------| --------------------------------------------------------------------------|
| SupplementsRQ			            | 1     	|			| Root node.|
| Preferences						| 1		    |			| Valuation preferences.|
| @paymentMethods					| 0..1		| Boolean	| If true, the Valuation will return the list of payment methods available for the Itineraries.|
| @baggageTypes						| 0..1		| Boolean	| If true, the Valuation will return the list of baggage allowance available for the Itineraries.|
| @specialSupplements				| 0..1		| Boolean	| If true, the Valuation will return the list of special suplements available for the Itineraries.|
| @extendedFareRules				| 0..1		| Boolean	| If true, the Valuation will return a list of detailed fare rules of the Itineraries.|
| @summarizedFareRules				| 0..1		| Boolean	| If true, the Valuation will return a list of summarired fare rules of the Itineraries.|
| @seating							| 0..1		| Boolean	| If true, the Valuation will return the list of seats available in the plane.|
| @installments						| 0..1		| Boolean	| If true, the Valuation will return the list of partial payment rules (installments) available for the Itineraries.|
| Itineraries                 		| 0..1     	|			| Contains a list of Itineraries.|
| Itineraries/Itinerary       		| 1..n    	|			| Details of the Itinerary.|
| @id                    			| 1 		| Integer	| Unique identifier of the Itinerary.|
| @carrier               			| 1 		| String	| Validating carrier.|
| @fareRef	               			| 0..1 		| String	| Reference identifier to the original Fare.|
| @hasObFees             			| 0..1 		| Boolean	| If true then there is an extra fee for using credit card.|
| Itineraries/Itinerary/Conditions	| 0..1		|			| Contains a list of Fare Conditions.|
| Itineraries/Itinerary/Conditions/<br>Condition			| 1..n || Contains details of the Condition that applies to the condition.|
| @carrier							| 0..1		| String	| Carrier applying the condition.|
| @code								| 0..1		| String	| Code of the condition.|
| @id								| 0..1		| String	| Unique id of the condition.|
| @language							| 0..1		| String	| Language in which the condition is written.|
| Itineraries/Itinerary/Conditions/<br>Condition/Text		| 0..1 || Description of the condition.|
| Itineraries/Itinerary/Conditions/<br>Condition/Paragraph	| 0..n || List of Sentences and titles.|
| @title							| 0..1		| String	| Title content.|
| Itineraries/Itinerary/Conditions/<br>Condition/Paragraph/Sentence	| 0..n | String	| List of Sentences contents.|
| Itineraries/Itinerary/Journeys	| 1    		|			| Contains a list of Journeys.|
| Itineraries/Itinerary/Journeys/Journey					| 1..n    	|| Contains details of the Journeys.|
| @id								| 1 		| Integer	| Unique identifier of the Journey in scope.|
| @duration							| 0..1 		| Integer	| Duration of the Journey in minutes. |
| @familyFare						| 0..1 		| String	| Family fare name of the Journey.|
| @checkinStart						| 0..1 		| Date		| Checkin start date.|
| @checkinEnd						| 0..1 		| Date		| Checkin end date.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments		| 1 || Contains a list of Segments associated to the Journey.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment | 1..n   || Contains details of the SegmentInfo.|
| @id								| 1 		| Integer	| Unique SegmentInfo identifier.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentInfo | 1 || Contains information of the Segment.|
| @id								| 1 		| Integer	| Unique identifier of the SegmentInfo.|
| @transportationId					| 1 		| String	| Unique Id of the transportation.|
| @operatingCarrier      			| 1 		| String	| Company which operates the transportation.|
| @marketingCarrier      			| 1 		| String	| Company which commercializes the transportation.|
| @departureDate         			| 1 		| Date		| Departure date.|
| @arrivalDate           			| 1 		| Date		| Arrival date.|
| @transportationType    			| 0..1 		| String	| Transport type: V ( Flight ), T ( Train ), B ( Bus ), S() & F ( Ferry ).|
| @transportationName    			| 0..1 		| String	| Name of the transportation.|
| @transportationCode				| 0..1		| String	| Code of the transportation.|
| @departureTerminal				| 0..1 		| String	| Departure terminal.|
| @arrivalTerminal       			| 0..1 		| String	| Arrival terminal.|
| @segmentDuration       			| 0..1 		| Integer	| Transport duration ( in minutes ).|
| @segmentStatus					| 0..1		| String	| Segment status: HK (Holding confirmed), TK(Confirming new flight times), UC(Unable to confirm), UN(Flight cancelled by airline), NO (No action taken), UD (Undefined).|
| @planeType						| 0..1 		| String	| Plane type. Flights parameter.|
| @maxCheckinDate					| 0..1 		| Date		| Maximum date to make the check-in.|
| @hasTechnicalStop					| 0..1		| Boolean	| If true, the segment has a technical stop.|
| @electronicTicket      			| 0..1 		| Boolean	| If true, the segment uses a electronic ticket.|
| @secureFlight          			| 0..1		| Boolean	| If true, the provider requires extra information of the passengers. Flights parameter.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/OriginLoc | 1     	|| Origin location.|
| @code                  			| 1 		| String	| Location code.|
| @type                  			| 0..1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).|
| @name								| 0..1 		| String	| Location full name.|
| @radius							| 0..1		| Integer	| Area radius from location.|
| @cityCode              			| 0..1 		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/OriginLoc/<br>AlternativeLocations	| 0..1		|| Contains a list of AlternativeLocations.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/OriginLoc/<br>AlternativeLocations/AlternativeLocation	| 1..n	|| Contains the information of the alternative location.|
| @code								| 1			| String	| Location code.|
| @cityCode        					| 0..1  	| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.|
| @name								| 0..1		| String	| Location long name.|
| @type								| 0..1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/DestinationLoc | 1   || Destination location.|
| @code                  			| 1 		| String	| Location code.|
| @type								| 0..1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).|
| @name								| 0..1 		| String	| Location full name.|
| @radius							| 0..1		| Integer	| Area radius from location.|
| @cityCode              			| 0..1 		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/<br>DestinationLoc/AlternativeLocations	| 0..1		|| Contains a list of AlternativeLocations.
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/<br>DestinationLoc/AlternativeLocations/<br>AlternativeLocation	| 1..n	|| Contains the information of the alternative location.|
| @code								| 1			| String	| Location code.|
| @cityCode        					| 0..1  	| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.|
| @name								| 0..1		| String	| Location long name.|
| @type								| 0..1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/TechnicalStops | 0..1 || Contains a list of TechnicalStops.|
| @totalTechnicalStops				| 1 		| Integer	| Total number of TechnicalStops.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/TechnicalStops/<br>TechnicalStop | 0..n || Contains the details of the TechnicalStop.|
| @location							| 1 		| String	| TechnicalStop location.|
| @stopDate							| 1 		| Date		| Approx. stop date and time.|
| @departureDate					| 1 		| Date		| Approx. departure date and time.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses | 1 | | Contains a list of SegmentClasses.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses/<br>SegmentClass | 1..n || Contains details of the SegmentClass.|
| @cabinClass            			| 1 		| String	| Cabin class of the seat: N (Not specified), Y (Tourist), C (Business), F (First), CA (Cabin, only for ferries), YP (Tourist Plus).|
| @paxRef               	 		| 1 		| Integer	| Passenger reference.|
| @fareType              			| 1 		| String	| Fare type: PUB ( Public ), PRI ( Private ), NEGO ( Negotiated ) and CORP ( Corporate ).|
| @class                 			| 0..1 		| String	| Fare class.|
| @fareBasis             			| 0..1 		| String	| Identifier of the fare.|
| @avail                 			| 0..1 		| Integer	| Available seats remaining for this class (In flights, the maximum is 9).|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses/<br>SegmentClass/Modifiable | 0..1 || Contains the information of the modifiable fare.|
| @modifiable                 		| 1 		| Boolean	| If true, the fare allows this modification.|
| @Description                 		| 0..1 		| String	| Modification description.|
| @amount                 			| 0..1 		| Decimal	| Modification amount.|
| @currency                 		| 0..1 		| String	| Modification currency.|
| @amountType                 		| 0..1 		| String	| Modification amount type: AMOUNT (Fare amount), FEE (Fee amount), TOTAL (Total fare amount), PERCENTUAL (Percentual amount).|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses/<br>SegmentClass/CancellationPolicies | 0..1 || Contains a list of CancellationPolicies.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses/<br>SegmentClass/CancellationPolicies/<br>CancellationPolicy | 1..n ||Contains details of the CancelationPolicy.	|
| @refundable                 		| 1 		| Boolean	| If true, the fare allows the refundation.|
| @fromDate                 		| 0..1 		| Date		| Date of the begining of the policy.|
| @amount                 			| 0..1 		| Decimal	| Policy amount.|
| @currency                 		| 0..1 		| String	| Policy currency.|
| @amountType                 		| 0..1 		| String	| Policy amount type: AMOUNT (Fare amount), FEE (Fee amount), TOTAL (Total fare amount), PERCENTUAL (Percentual amount).|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/ReservationTokens | 0..1 |  | Specific attribute used for each provider.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/ReservationTokens/<br>Attribute | 1..n || Type of attribute.|
| @key								| 1 		| String	| Contains the keyword/ Id to identify a parameter.|
| @value							| 1 		| String	| Contains the value of the parameter.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/CheckinInformation | 0..1 || Checkin information.|
| @openingTime						| 0..1 		| Date		| Checkin opening time.|
| @closingTime						| 0..1 		| Date		| Checkin closing time.|
| @estimatedCheckinTime				| 0..1 		| Date		| Estimated checkin time.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/CheckinInformation/<br>Status | 0..1 || Status checkin information.|
| @isAvailable						| 0..1 		| Boolean	| If true, the cheking is available.|
| @direction						| 0..1 		| String	| Direction of the journey about to checkin: OUTBOUND, INBOUND, OUTBOUND_INBOUND (Outbound and Inbound).|
| @status							| 0..1 		| String	| Status of the checkin: UNDEFINED, IN_PROGRESS, ERROR, COMPLETE, UNCONFIRMED.|
| Itineraries/Itinerary/AmountBreakdown  					| 1     	|| Breakdown of the fare amount.|
| @currency							| 1 		| String	| Currency code of the fare.|
| @totalAmount           			| 1 		| Decimal	| Total amount. with taxes and other charges included.|
| @notCommissionableAmount			| 0..1 		| Decimal	| Total amount that can not be commissioned.|
| @commission            			| 0..1 		| Decimal	| Commission.|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakdowns | 0..1   || Contains a list of breakdown amounts ( taxes, mandatory charges.. ).|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakdowns/ChargeBreakdown | 1..n || Contains details of the BreakdownAmount.|
| @amount                			| 1    	 	| Decimal	| Charge amount.|
| @type                  			| 0..1 		| String	| [Type of charge.](#reservation-enumerate-description)|
| @included							| 0..1		| Boolean	| If true, the charge is included to the total fare amount.|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakdowns/ChargeBreakdown<br>/Concept | 0..1 || Contains details of the charge.|
| @id                    			| 0..1 		| String	| Unique id of the Concept.|
| @language              			| 0..1 		| String	| Language.|
| @carrier              			| 0..1 		| String	| Carrier.|
| @code              				| 0..1 		| String	| Concept code.|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakDowns/ChargeBreakdown<br>/Concept/Text | 0..1 | String | Remarks.|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakDowns/ChargeBreakdown<br>/Concept/Paragraph | 0..n || Contains a list of Sentences and titles.|
| @title							| 0..1		| String	| Title.|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakDowns/ChargeBreakdown/<br>Concept/Paragraph/Sentence | 0..n | String | Sentence.|
| Itineraries/Itinerary/AmountBreakdown/<br>PaxBreakdown	| 1    	|| Contains a list of breakdown amounts for each passenger ( ADT amount, etc. ).|
| Itineraries/Itinerary/AmountBreakdown/<br>PaxBreakdowns/PaxBreakdown | 1..n || Contains details of breakdown amounts for each passenger.|
| @paxType               			| 1 		| String	| Passenger type: ADT ( Adult ), CHD ( Child ) & INF ( Infant ).|
| @amount                			| 1 		| Decimal	| Total amount, with taxes included, associated to the passenger.|
| @taxes                 			| 1 		| Decimal	| If they exist, taxes are applied for this passenger type.|
| @taxesDU                			| 0..1 		| Decimal	| DU taxes.|
| @fees                				| 0..1 		| Decimal	| Fees.|
| Itineraries/Itinerary/AmountBreakdown/<br>PaxBreakdowns/PaxBreakdown/<br>Taxes | 0..1 || Contains a list of Taxes.|
| Itineraries/Itinerary/AmountBreakdown/<br>PaxBreakdowns/PaxBreakdown/<br>Taxes/Tax | 1..n || Code and amount of each tax.|
| @code								| 1			| String	| Code.|
| @amount							| 1			| Decimal	| Amount.|
| Itineraries/Itinerary/PaxConfigurations					| 1     	|| Contains a list of PaxConfiguration.|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration | 1..n || Contains details of PaxConfiguration.|
| @id                    			| 1 		| Integer	| Unique identifier of the PaxConfiguration.|
| @paxRef                			| 1 		| Integer	| Reference to the passenger Id from the request.|
| @paxType               			| 1 		| String	| Passenger type based on the age of the passenger: ADT (Adult), CHD (Child), INF (Infant), YOU (Young) and SEN (Senior).|
| @age                   			| 0..1 		| Integer	| Age of the passenger.|
| @nacionality						| 0..1 		| String	| Nacionality of the passenger.|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses | 0..1 || Applied discounts.|
| @resident              			| 0..1 		| String	| [Resident discount type.](#reservation-enumerate-description)|
| @largeFamily           			| 0..1 		| String	| Family discount type: N(None), F1(Large family), F2 (Special large family).|
| @discountCardCode					| 0..1		| String	| Discount card code.|
| @discountCard						| 0..1		| String	| [Discount card type.](#reservation-enumerate-description)|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses/<br>DiscountCards	| 0..1	|| Contains a list of DiscountCards.|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses/<br>DiscountCards/DiscountCard| 1..n	|| DiscountCard details.|
| @type								| 1			| String	| [Discount card type.](#reservation-enumerate-description)|
| @code								| 0..1		| String	| Discount card code.|
| @id								| 0..1		| String	| Unique identifier of discound card.|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses/<br>PaxTypeCodes		| 0..1	|| Contains a list of PaxTypeCodes.|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses/<br>PaxTypeCodes/PaxTypeCode	| 1..n	|| Contains the code type of the passenger.|
| @code								| 1			| String	| Code type of the passenger.|
| Itineraries/Itinerary/Emissions							| 0..1	|| Contains a list of Issuances.|
| Itineraries/Itinerary/Emissions/<br>Emission				| 1..n	|| Contains the key of the Issuance.|
| @key								| 1			| String	| Key of the Issuance.|
| Locators                       	| 0..1  	|    		| Contains a list of locators.|
| Locators/Locator               	| 1..n  	|    		| Contains details of the locator.|
| Locators/Locator/Id            	| 1  		| String 	| Unique identifier of the locator.|
| Locators/Locator/Type          	| 1  		| String 	| [Locator type.](#reservation-enumerate-description)|
| Email								| 0..1     	| String	| Client's email.|


### SupplementsRS Description

| **Element** 						| **Number**| **Type**	| **Description**															|
| --------------------------------- | ----------| ----------| --------------------------------------------------------------------------|
| SupplementsRS                     | 1    		|			| Root node.|
| Locators                       	| 0..1  	|    		| Contains a list of locators.|
| Locators/Locator               	| 1..n  	|    		| Contains details of the locator.|
| Locators/Locator/Id            	| 1  		| String 	| Unique identifier of the locator.|
| Locators/Locator/Type          	| 1  		| String 	| [Locator type.](#reservation-enumerate-description)|
| Itineraries                 		| 0..1     	|			| Contains a list of Itineraries.|
| Itineraries/Itinerary       		| 1..n    	|			| Details of the Itinerary.|
| @id                    			| 1 		| Integer	| Unique identifier of the Itinerary.|
| @carrier               			| 1 		| String	| Validating carrier.|
| @fareRef	               			| 0..1 		| String	| Reference identifier to the original Fare.|
| @hasObFees             			| 0..1 		| Boolean	| If true then there is an extra fee for using credit card.|
| Itineraries/Itinerary/Conditions	| 0..1		|			| Contains a list of Fare Conditions.|
| Itineraries/Itinerary/Conditions/<br>Condition			| 1..n || Contains details of the Condition that applies to the condition.|
| @carrier							| 0..1		| String	| Carrier applying the condition.|
| @code								| 0..1		| String	| Code of the condition.|
| @id								| 0..1		| String	| Unique id of the condition.|
| @language							| 0..1		| String	| Language in which the condition is written.|
| Itineraries/Itinerary/Conditions/<br>Condition/Text		| 0..1 || Description of the condition.|
| Itineraries/Itinerary/Conditions/<br>Condition/Paragraph	| 0..n || List of Sentences and titles.|
| @title							| 0..1		| String	| Title content.|
| Itineraries/Itinerary/Conditions/<br>Condition/Paragraph/Sentence	| 0..n | String	| List of Sentences contents.|
| Itineraries/Itinerary/Journeys	| 1    		|			| Contains a list of Journeys.|
| Itineraries/Itinerary/Journeys/Journey					| 1..n    	|| Contains details of the Journeys.|
| @id								| 1 		| Integer	| Unique identifier of the Journey in scope.|
| @duration							| 0..1 		| Integer	| Duration of the Journey in minutes. |
| @familyFare						| 0..1 		| String	| Family fare name of the Journey.|
| @checkinStart						| 0..1 		| Date		| Checkin start date.|
| @checkinEnd						| 0..1 		| Date		| Checkin end date.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments		| 1 || Contains a list of Segments associated to the Journey.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment | 1..n   || Contains details of the SegmentInfo.|
| @id								| 1 		| Integer	| Unique SegmentInfo identifier.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentInfo | 1 || Contains information of the Segment.|
| @id								| 1 		| Integer	| Unique identifier of the SegmentInfo.|
| @transportationId					| 1 		| String	| Unique Id of the transportation.|
| @operatingCarrier      			| 1 		| String	| Company which operates the transportation.|
| @marketingCarrier      			| 1 		| String	| Company which commercializes the transportation.|
| @departureDate         			| 1 		| Date		| Departure date.|
| @arrivalDate           			| 1 		| Date		| Arrival date.|
| @transportationType    			| 0..1 		| String	| Transport type: V ( Flight ), T ( Train ), B ( Bus ), S() & F ( Ferry ).|
| @transportationName    			| 0..1 		| String	| Name of the transportation.|
| @transportationCode				| 0..1		| String	| Code of the transportation.|
| @departureTerminal				| 0..1 		| String	| Departure terminal.|
| @arrivalTerminal       			| 0..1 		| String	| Arrival terminal.|
| @segmentDuration       			| 0..1 		| Integer	| Transport duration ( in minutes ).|
| @segmentStatus					| 0..1		| String	| Segment status: HK (Holding confirmed), TK(Confirming new flight times), UC(Unable to confirm), UN(Flight cancelled by airline), NO (No action taken), UD (Undefined).|
| @planeType						| 0..1 		| String	| Plane type. Flights parameter.|
| @maxCheckinDate					| 0..1 		| Date		| Maximum date to make the check-in.|
| @hasTechnicalStop					| 0..1		| Boolean	| If true, the segment has a technical stop.|
| @electronicTicket      			| 0..1 		| Boolean	| If true, the segment uses a electronic ticket.|
| @secureFlight          			| 0..1		| Boolean	| If true, the provider requires extra information of the passengers. Flights parameter.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/OriginLoc | 1     	|| Origin location.|
| @code                  			| 1 		| String	| Location code.|
| @type                  			| 0..1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).|
| @name								| 0..1 		| String	| Location full name.|
| @radius							| 0..1		| Integer	| Area radius from location.|
| @cityCode              			| 0..1 		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/OriginLoc/<br>AlternativeLocations	| 0..1		|| Contains a list of AlternativeLocations.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/OriginLoc/<br>AlternativeLocations/AlternativeLocation	| 1..n	|| Contains the information of the alternative location.|
| @code								| 1			| String	| Location code.|
| @cityCode        					| 0..1  	| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.|
| @name								| 0..1		| String	| Location long name.|
| @type								| 0..1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/DestinationLoc | 1   || Destination location.|
| @code                  			| 1 		| String	| Location code.|
| @type								| 0..1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).|
| @name								| 0..1 		| String	| Location full name.|
| @radius							| 0..1		| Integer	| Area radius from location.|
| @cityCode              			| 0..1 		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/<br>DestinationLoc/AlternativeLocations	| 0..1		|| Contains a list of AlternativeLocations.
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/<br>DestinationLoc/AlternativeLocations/<br>AlternativeLocation	| 1..n	|| Contains the information of the alternative location.|
| @code								| 1			| String	| Location code.|
| @cityCode        					| 0..1  	| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.|
| @name								| 0..1		| String	| Location long name.|
| @type								| 0..1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/TechnicalStops | 0..1 || Contains a list of TechnicalStops.|
| @totalTechnicalStops				| 1 		| Integer	| Total number of TechnicalStops.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/TechnicalStops/<br>TechnicalStop | 0..n || Contains the details of the TechnicalStop.|
| @location							| 1 		| String	| TechnicalStop location.|
| @stopDate							| 1 		| Date		| Approx. stop date and time.|
| @departureDate					| 1 		| Date		| Approx. departure date and time.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses | 1 | | Contains a list of SegmentClasses.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses/<br>SegmentClass | 1..n || Contains details of the SegmentClass.|
| @cabinClass            			| 1 		| String	| Cabin class of the seat: N (Not specified), Y (Tourist), C (Business), F (First), CA (Cabin, only for ferries), YP (Tourist Plus).|
| @paxRef               	 		| 1 		| Integer	| Passenger reference.|
| @fareType              			| 1 		| String	| Fare type: PUB ( Public ), PRI ( Private ), NEGO ( Negotiated ) and CORP ( Corporate ).|
| @class                 			| 0..1 		| String	| Fare class.|
| @fareBasis             			| 0..1 		| String	| Identifier of the fare.|
| @avail                 			| 0..1 		| Integer	| Available seats remaining for this class (In flights, the maximum is 9).|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses/<br>SegmentClass/Modifiable | 0..1 || Contains the information of the modifiable fare.|
| @modifiable                 		| 1 		| Boolean	| If true, the fare allows this modification.|
| @Description                 		| 0..1 		| String	| Modification description.|
| @amount                 			| 0..1 		| Decimal	| Modification amount.|
| @currency                 		| 0..1 		| String	| Modification currency.|
| @amountType                 		| 0..1 		| String	| Modification amount type: AMOUNT (Fare amount), FEE (Fee amount), TOTAL (Total fare amount), PERCENTUAL (Percentual amount).|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses/<br>SegmentClass/CancellationPolicies | 0..1 || Contains a list of CancellationPolicies.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses/<br>SegmentClass/CancellationPolicies/<br>CancellationPolicy | 1..n ||Contains details of the CancelationPolicy.	|
| @refundable                 		| 1 		| Boolean	| If true, the fare allows the refundation.|
| @fromDate                 		| 0..1 		| Date		| Date of the begining of the policy.|
| @amount                 			| 0..1 		| Decimal	| Policy amount.|
| @currency                 		| 0..1 		| String	| Policy currency.|
| @amountType                 		| 0..1 		| String	| Policy amount type: AMOUNT (Fare amount), FEE (Fee amount), TOTAL (Total fare amount), PERCENTUAL (Percentual amount).|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/ReservationTokens | 0..1 |  | Specific attribute used for each provider.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/ReservationTokens/<br>Attribute | 1..n || Type of attribute.|
| @key								| 1 		| String	| Contains the keyword/ Id to identify a parameter.|
| @value							| 1 		| String	| Contains the value of the parameter.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/CheckinInformation | 0..1 || Checkin information.|
| @openingTime						| 0..1 		| Date		| Checkin opening time.|
| @closingTime						| 0..1 		| Date		| Checkin closing time.|
| @estimatedCheckinTime				| 0..1 		| Date		| Estimated checkin time.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/CheckinInformation/<br>Status | 0..1 || Status checkin information.|
| @isAvailable						| 0..1 		| Boolean	| If true, the cheking is available.|
| @direction						| 0..1 		| String	| Direction of the journey about to checkin: OUTBOUND, INBOUND, OUTBOUND_INBOUND (Outbound and Inbound).|
| @status							| 0..1 		| String	| Status of the checkin: UNDEFINED, IN_PROGRESS, ERROR, COMPLETE, UNCONFIRMED.|
| Itineraries/Itinerary/AmountBreakdown  					| 1     	|| Breakdown of the fare amount.|
| @currency							| 1 		| String	| Currency code of the fare.|
| @totalAmount           			| 1 		| Decimal	| Total amount. with taxes and other charges included.|
| @notCommissionableAmount			| 0..1 		| Decimal	| Total amount that can not be commissioned.|
| @commission            			| 0..1 		| Decimal	| Commission.|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakdowns | 0..1   || Contains a list of breakdown amounts ( taxes, mandatory charges.. ).|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakdowns/ChargeBreakdown | 1..n || Contains details of the BreakdownAmount.|
| @amount                			| 1    	 	| Decimal	| Charge amount.|
| @type                  			| 0..1 		| String	| [Type of charge.](#reservation-enumerate-description)|
| @included							| 0..1		| Boolean	| If true, the charge is included to the total fare amount.|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakdowns/ChargeBreakdown<br>/Concept | 0..1 || Contains details of the charge.|
| @id                    			| 0..1 		| String	| Unique id of the Concept.|
| @language              			| 0..1 		| String	| Language.|
| @carrier              			| 0..1 		| String	| Carrier.|
| @code              				| 0..1 		| String	| Concept code.|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakDowns/ChargeBreakdown<br>/Concept/Text | 0..1 | String | Remarks.|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakDowns/ChargeBreakdown<br>/Concept/Paragraph | 0..n || Contains a list of Sentences and titles.|
| @title							| 0..1		| String	| Title.|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakDowns/ChargeBreakdown/<br>Concept/Paragraph/Sentence | 0..n | String | Sentence.|
| Itineraries/Itinerary/AmountBreakdown/<br>PaxBreakdown	| 1    	|| Contains a list of breakdown amounts for each passenger ( ADT amount, etc. ).|
| Itineraries/Itinerary/AmountBreakdown/<br>PaxBreakdowns/PaxBreakdown | 1..n || Contains details of breakdown amounts for each passenger.|
| @paxType               			| 1 		| String	| Passenger type: ADT ( Adult ), CHD ( Child ) & INF ( Infant ).|
| @amount                			| 1 		| Decimal	| Total amount, with taxes included, associated to the passenger.|
| @taxes                 			| 1 		| Decimal	| If they exist, taxes are applied for this passenger type.|
| @taxesDU                			| 0..1 		| Decimal	| DU taxes.|
| @fees                				| 0..1 		| Decimal	| Fees.|
| Itineraries/Itinerary/AmountBreakdown/<br>PaxBreakdowns/PaxBreakdown/<br>Taxes | 0..1 || Contains a list of Taxes.|
| Itineraries/Itinerary/AmountBreakdown/<br>PaxBreakdowns/PaxBreakdown/<br>Taxes/Tax | 1..n || Code and amount of each tax.|
| @code								| 1			| String	| Code.|
| @amount							| 1			| Decimal	| Amount.|
| Itineraries/Itinerary/PaxConfigurations					| 1     	|| Contains a list of PaxConfiguration.|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration | 1..n || Contains details of PaxConfiguration.|
| @id                    			| 1 		| Integer	| Unique identifier of the PaxConfiguration.|
| @paxRef                			| 1 		| Integer	| Reference to the passenger Id from the request.|
| @paxType               			| 1 		| String	| Passenger type based on the age of the passenger: ADT (Adult), CHD (Child), INF (Infant), YOU (Young) and SEN (Senior).|
| @age                   			| 0..1 		| Integer	| Age of the passenger.|
| @nacionality						| 0..1 		| String	| Nacionality of the passenger.|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses | 0..1 || Applied discounts.|
| @resident              			| 0..1 		| String	| [Resident discount type.](#reservation-enumerate-description)|
| @largeFamily           			| 0..1 		| String	| Family discount type: N(None), F1(Large family), F2 (Special large family).|
| @discountCardCode					| 0..1		| String	| Discount card code.|
| @discountCard						| 0..1		| String	| [Discount card type.](#reservation-enumerate-description)|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses/<br>DiscountCards	| 0..1	|| Contains a list of DiscountCards.|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses/<br>DiscountCards/DiscountCard| 1..n	|| DiscountCard details.|
| @type								| 1			| String	| [Discount card type.](#reservation-enumerate-description)|
| @code								| 0..1		| String	| Discount card code.|
| @id								| 0..1		| String	| Unique identifier of discound card.|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses/<br>PaxTypeCodes		| 0..1	|| Contains a list of PaxTypeCodes.|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses/<br>PaxTypeCodes/PaxTypeCode	| 1..n	|| Contains the code type of the passenger.|
| @code								| 1			| String	| Code type of the passenger.|
| Itineraries/Itinerary/Emissions							| 0..1	|| Contains a list of Issuances.|
| Itineraries/Itinerary/Emissions/<br>Emission				| 1..n	|| Contains the key of the Issuance.|
| @key								| 1			| String	| Key of the Issuance.|
| Passengers						| 0..1  	|    		| Contains a list of Passengers.|
| Passengers/Passenger				| 1..n 		|			| Contains information of the Passenger.|
| @id								| 1  		| Integer	| Unique identifier of the passenger.|
| @title							| 1  		| String 	| Treatment: MR, MRS, CHD and INF.|
| @name								| 1  		| String 	| Name of the Passenger.|
| @surname        					| 1  		| String 	| Surname/s of the Passenger.|
| @bithDate							| 1  		| Date 		| Date of birth.|
| @codeDCO     						| 0..1  	| Integer 	| Consolidate document number.|
| @documentType						| 0..1  	| String 	| Document type: NATIONAL_ID, PASSPORT, RESIDENT_ID, FOREIGN_PASSPORT, BIRTH_NOTIFICATION.|
| @documentId						| 0..1  	| String 	| Unique identifier of the documentation.|
| @documentExpiration  				| 0..1		| Date 		| Expiration date of the documentation.|
| @documentExpedition  				| 0..1		| Date 		| Expedition date of the documentation.|
| @nationality						| 0..1  	| String 	| Nationality.|
| @gender							| 0..1  	| Char		| Gender.|
| @language							| 0..1  	| String 	| Language.|
| Passengers/Passenger/PaxBonusDetails 						| 0..1  || Contains details of the Passenger bonus.|
| Passengers/Passenger/PaxBonusDetails/<br>AppliedBonuses	| 0..1  || Contains details of the applied bonus.|
| @resident              			| 0..1 		| String	| [Resident discount type.](#reservation-enumerate-description)|
| @largeFamily           			| 0..1 		| String	| Family discount type: N(None), F1(Large family), F2 (Special large family). |
| @discountCardCode					| 0..1		| String	| Discount card code.|
| @discountCard						| 0..1		| String	| [Discount card type.](#reservation-enumerate-description)|
| Passengers/Passenger/PaxBonusDetails/<br>AppliedBonuses/DiscountCards	| 0..1	|| Contains a list of DiscountCards.|
| Passengers/Passenger/PaxBonusDetails/<br>AppliedBonuses/DiscountCards/<br>DiscountCard| 1..n || DiscountCard details.|
| @type								| 1			| String	| [Discount card type.](#reservation-enumerate-description)|
| @code								| 0..1		| String	| Discount card code.|
| @id								| 0..1		| String	| Unique identifier of discound card.|
| Passengers/Passenger/PaxBonusDetails/<br>AppliedBonuses/PaxTypeCodes		| 0..1	|| Contains a list of PaxTypeCodes.|
| Passengers/Passenger/PaxBonusDetails/<br>AppliedBonuses/PaxTypeCodes/<br>PaxTypeCode	| 1..n	|| Contains the code type of the passenger.|
| @code								| 1			| String	| Code type of the passenger.|
| Passengers/Passenger/PaxBonusDetails/<br>ResidentCityCode	| 0..1	| String	| If required, city code for the Spanish Resident discount (070407, PALMA DE MALLORCA).|
| Passengers/Passenger/PaxBonusDetails/<br>LargeFamilyId	| 0..1	| String	| Spanish family id.|
| Passengers/Passenger/PaxBonusDetails/<br>LargeFamilyCityCode | 0..1	| String	| City code for the Spanish Family discount (070407, Islas Baleares).|
| Passengers/Passenger/PaxBonusDetails/<br>ResidentCertificateId | 0..1	| String	| Resident certification number.|
| Passengers/Passenger/PaxBonusDetails/<br>DetailName		| 0..1	|| Passenger name expanded (more details).|
| Passengers/Passenger/PaxBonusDetails/<br>DetailName/name	| 0..1	| String | Name.|
| Passengers/Passenger/PaxBonusDetails/<br>DetailName/firstSurname | 0..1	| String | First surname.|
| Passengers/Passenger/PaxBonusDetails/<br>DetailName/secondSurname | 0..1	| String | Second surname.|
| Passengers/Passenger/PaxTickets	| 0..1		|			| Contains a list of PaxTickets.|
| Passengers/Passenger/PaxTickets/PaxTicket					| 1..n	|| Contains the details of the tickets relative to the passenger and the status of the applied bonuses.|
| @ticketNum						| 1  		| String 	| Unique id of the ticket.|
| @ticketRef						| 0..1  	| String 	| Reference to a Ticket id.|
| Passengers/Passenger/PaxTickets/<br>PaxTicket/DiscountStates | 0..1	|| Contains a list of discount information status.|
| Passengers/Passenger/PaxTickets/<br>PaxTicket/DiscountStates/DiscountState | 1..n	|| Information of the applied bonuses.|
| @type								| 1  		| String 	| Discount Type: RESIDENT, LARGE_FAMILY|
| @status							| 1  		| String 	| Discount status: N (None), CHECKED, NOT_CHECKED.|
| @numAttempts						| 0..1  	| String 	| Number of retry attempts for spanish resident validation.|
| @code								| 0..1  	| String 	| Discount/Bonus associated code provided by the supplier.|
| Passengers/Passenger/SpecialPetitions						| 0..1	|| Contains information of the bags, seats or other supplements requested by the passenger.|
| Passengers/Passenger/SpecialPetitions/<br>NumSuitcases	| 0..1	|| Number of bags requested by the passenger.|
| Passengers/Passenger/SpecialPetitions/<br>PaxBaggageInfos | 0..1	|| Contains a list of PaxBaggageInfo.|
| Passengers/Passenger/SpecialPetitions/<br>PaxBaggageInfos/PaxBaggageInfo | 1..n	|| Specifies the luggage of the passenger.|
| @type								| 1  		| String 	| Baggage type: Bag, Bike, Wheelchair, Skis, BabyTrolley, HandBaggage.|
| @id								| 1  		| String 	| Baggage id.|
| @code								| 1  		| String 	| Bag code.|
| @weight							| 0..1  	| String 	| Weight.|
| @reservationToken					| 0..1  	| String 	| Weight.|
| @quantity							| 0..1  	| Decimal 	| Quantity.|
| Passengers/Passenger/SpecialPetitions/<br>PaxBaggageInfos/PaxBaggageInfo/<br>References | 0..1	|| Segment and Passenger references.|
| Passengers/Passenger/SpecialPetitions/<br>PaxBaggageInfos/PaxBaggageInfo/<br>References/SegmentReferences		| 0..1	||	Contains a list of segment references for the Baggage Type.|
| Passengers/Passenger/SpecialPetitions/<br>PaxBaggageInfos/PaxBaggageInfo/<br>References/SegmentReferences/<br>SegmentReference		| 1..n	||	Segment reference.|
| @itineraryRef						| 1 		| Integer	| Unique identifier of the Itinerary.|
| @journeyRef						| 1 		| Integer	| Unique identifier of the Journey.|
| @segmentRef						| 1 		| Integer	| Unique identifier of the Segment.|
| Passengers/Passenger/SpecialPetitions/<br>PaxBaggageInfos/PaxBaggageInfo/<br>References/PaxReferences		| 0..1	||	Contains a list of passenger references for the Baggage Type.|
| Passengers/Passenger/SpecialPetitions/<br>PaxBaggageInfos/PaxBaggageInfo/<br>References/PaxReferences/<br>PaxReference		| 1..n	||	Passenger reference.|
| @paxRef							| 1 		| String	| Reference to the passenger.|
| Passengers/Passenger/SpecialPetitions/<br>Optionals		| 0..1	||	Contains a list of supplements (food, pets, etc. Used also for baggage).|
| Passengers/Passenger/SpecialPetitions/<br>Optionals/Optional | 1..n	||	Optional element information for the reservation.|
| @id								| 1  		| String 	| Optional id.|
| @type								| 1  		| String 	| Type: RM (Remark), SSR (Special Service Request), OSI (Other Service Information).|
| @specialSupplementType			| 1			| String 	| [Special Service type.](#reservation-enumerate-description).|
| @code								| 1  		| String 	| Code.|
| @quantity							| 0..1  	| Decimal 	| Quantity.|
| @carrier							| 0..1  	| String 	| Carrier.|
| @text								| 0..1  	| String 	| Free text.|
| @reservationToken					| 0..1  	| String 	| Reservation token.|
| @length							| 0..1  	| Decimal 	| Length.|
| @width							| 0..1  	| Decimal 	| Width.|
| @height							| 0..1  	| Decimal 	| Height.|
| @weight							| 0..1  	| Decimal 	| Weight.|
| @ownTransportation				| 0..1  	| Boolean 	| If true, the supplement includes own transportation cage.|
| Passengers/Passenger/SpecialPetitions/<br>Optionals/Optional/<br>References | 0..1	|| Segment and Passenger references.|
| Passengers/Passenger/SpecialPetitions/<br>Optionals/Optional/<br>References/SegmentReferences		| 0..1	||	Contains a list of segment references for the Optional.|
| Passengers/Passenger/SpecialPetitions/<br>Optionals/Optional/<br>References/SegmentReferences/<br>SegmentReference		| 1..n	||	Segment reference.|
| @itineraryRef						| 1 		| Integer	| Unique identifier of the Itinerary.|
| @journeyRef						| 1 		| Integer	| Unique identifier of the Journey.|
| @segmentRef						| 1 		| Integer	| Unique identifier of the Segment.|
| Passengers/Passenger/SpecialPetitions/<br>Optionals/Optional/<br>References/PaxReferences		| 0..1	||	Contains a list of passenger references for the Optional.|
| Passengers/Passenger/SpecialPetitions/<br>Optionals/Optional/<br>References/PaxReferences/<br>PaxReference		| 1..n	||	Passenger reference.|
| @paxRef							| 1 		| String	| Reference to the passenger.|
| Passengers/Passenger/SpecialPetitions/<br>Optionals/Optional/<br>Charge		| 0..1	||	Charge details of the optional.|
| @currency             			| 1 		| String	| Currency.|
| @fixAmount             			| 0..1 		| Decimal	| Total fixed amount.|
| @appliesFixAmount					| 0..1 		| String	| The fixed amount applies to: PorReserva(Reservation), PorPasajero(Passenger), PorSegmento(Segment), TarifaBase(Base Fare), Tasas(Taxes), ForAdt(Adult passengers), ForChd(Children passengers), ForInf(Infant passengers).|
| @minFixAmount             		| 0..1 		| Decimal	| Minimal fixed amount.|
| @maxFixAmount             		| 0..1 		| Decimal	| Maximal fixed amount.|
| @minAmountPercentage             	| 0..1 		| Decimal	| Minimal percentage amount.|
| @maxAmountPercentage             	| 0..1 		| Decimal	| Maximal percentage amount.|
| @percentage             			| 0..1 		| Decimal	| Total percentage amount.|
| @percentageApplied             	| 0..1 		| String	| The percentage amount applies to: PorReserva(Reservation), PorPasajero(Passenger), PorSegmento(Segment), TarifaBase(Base Fare), Tasas(Taxes), ForAdt(Adult passengers), ForChd(Children passengers), ForInf(Infant passengers).|
| Passengers/Passenger/SpecialPetitions/<br>Seating			| 0..1    	|| Seating availability.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/BlockRules    | 0..1    	|| Contains a list of Block Rules.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/BlockRules/BlockRule 		| 1..n    	|| Block Rules.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/BlockRules/BlockRule/References | 1    	|| References for the Block Rule.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/BlockRules/BlockRule/References/<br>BlockReferences		| 1	||	Contains a list of references to block elements.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/BlockRules/BlockRule/References/<br>BlockReferences/BlockReference | 1..n || Block element reference.|
| @blockTypeRef						| 1  		| String	| Block type: CABIN (The entire cabin of the plane).|
| @blockRef							| 1  		| Integer	| Block reference.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/BlockRules/BlockRule/References/<br>SegmentReferences		| 0..1	||	Contains a list of segment references for the Block Rule.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/BlockRules/BlockRule/References/<br>SegmentReferences/SegmentReference		| 1..n	||	Segment reference.|
| @itineraryRef						| 1 		| Integer	| Unique identifier of the Itinerary.|
| @journeyRef						| 1 		| Integer	| Unique identifier of the Journey.|
| @segmentRef						| 1 		| Integer	| Unique identifier of the Segment.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/BlockRules/BlockRule/References/<br>PaxReferences		| 0..1	||	Contains a list of passenger references for the Special Supplement.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/BlockRules/BlockRule/References/<br>PaxReferences/PaxReference		| 1..n	||	Passenger reference.|
| @paxRef							| 1 		| String	| Reference to the passenger.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/BlockRules/BlockRule/BlockPrice | 0..1  	|| Price element.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/BlockRules/BlockRule/BlockPrice/<br>Amount | 0..1  	|| Amount by type.|
| @currency							| 1  		| String	| Currency code of the amount.|
| @amount                 			| 1  		| Decimal	| Amount.|
| @amountType             			| 0..1  	| String	| Amount type: AMOUNT (Amount), FEE (Service Fee), TOTAL (Total), PERCENTUAL (Percentual).|
| Passengers/Passenger/SpecialPetitions/<br>Seating/Blocks  | 1    	|| Contains a list of seating blocks.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/Blocks/Block    | 1..n    	|| Seating details.|
| @type								| 1  		| String	| Block type: CABIN (The entire cabin of the plane).|
| @id								| 1  		| Integer	| Unique id.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/Blocks/Block/References/<br>SegmentReferences		| 1	||	Contains a list of segment references for the Block.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/Blocks/Block/References/<br>SegmentReferences/SegmentReference		| 1..n	||	Segment reference.|
| @itineraryRef						| 1 		| Integer	| Unique identifier of the Itinerary.|
| @journeyRef						| 1 		| Integer	| Unique identifier of the Journey.|
| @segmentRef						| 1 		| Integer	| Unique identifier of the Segment.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/Blocks/Block/Blocks | 1    	|| Contains a list of row blocks.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/Blocks/Block/Blocks/Block 	| 1..n    	|| Row block.|
| @type    							| 1  		| String	| Block type: ROW|
| @id     							| 1  		| Integer	| Unique row id.|
| @number							| 1  		| Integer	| Row number in the cabin.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/Blocks/Block/Blocks/Block/<br>Blocks | 1    	|| Contains a list of seat blocks.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/Blocks/Block/Blocks/Block/<br>Blocks/Block | 1..n  || Seat block.|
| @type								| 1  		| String	| Block type: SEAT.|
| @id								| 1  		| Integer	| Unique seat id.|
| @number    						| 1  		| String	| Seat identifier.|
| @token    						| 0..1  	| String	| Reservation seat token.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/Blocks/Block/Blocks/Block/<br>Blocks/Block/Availability | 0..1 || Availability of the seat.|
| @isAvailable						| 1  		| Boolean	| Indicates whether the seat is available.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/Blocks/Block/Blocks/Block/<br>Blocks/Block/BlockAttributes | 0..1 || Contains a list of Seat attributes.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/Blocks/Block/Blocks/Block/<br>Blocks/Block/BlockAttributes/<br>BlockAttribute | 1..n |  | Seat attribute.|
| @type                   			| 1  		| String	| [Seat type.](#reservation-enumerate-description)|
| PaymentMethods                 	| 0..1    	|			| Contains a list of paymentMethods.|
| PaymentMethods/PaymentMethod 		| 1..n    	|			| Contains paymentMethod details.|
| @paymentType						| 1  		| String	| Payment Type: CreditCard, ElectronicBanking.|
| @cardType               			| 1  		| String	| Card type with a provider format.|
| PaymentMethods/PaymentMethod/<br>PaymentCharges			| 0..1      	|| Contains a list of Payment Charges.|
| PaymentMethods/PaymentMethod/<br>PaymentCharges/PaymentCharge | 1..n      || Charge applied to the Booking when this paymed method is used.|
| @fixAmount             			| 0..1 		| Decimal	| Total fixed amount.|
| @appliesFixAmount             	| 0..1 		| String	| The fixed amount applies to: PorReserva(Reservation), PorPasajero(Passenger), PorSegmento(Segment), TarifaBase(Base Fare), Tasas(Taxes), ForAdt(Adult passengers), ForChd(Children passengers), ForInf(Infant passengers).|
| @minFixAmount             		| 0..1 		| Decimal	| Minimal fixed amount.|
| @maxFixAmount             		| 0..1 		| Decimal	| Maximal fixed amount.|
| @minAmountPercentage             	| 0..1 		| Decimal	| Minimal percentage amount.|
| @maxAmountPercentage             	| 0..1 		| Decimal	| Maximal percentage amount.|
| @currency             			| 1 		| String	| Currency.|
| @percentage             			| 0..1 		| Decimal	| Total percentage amount.|
| @percentageApplied             	| 0..1 		| String	| The percentage amount applies to: PorReserva(Reservation), PorPasajero(Passenger), PorSegmento(Segment), TarifaBase(Base Fare), Tasas(Taxes), ForAdt(Adult passengers), ForChd(Children passengers), ForInf(Infant passengers).|
| BaggageTypes                 		| 0..1    	|			| Contains a list of Baggage information.|
| BaggageTypes/BaggageType			| 1..n    	|			| Baggage information.|
| @checkInType						| 1  		| String	| Check-in type: OnLine & Airport.|
| @appliesSegments        			| 1  		| String	| Segments in which is applied: All, Departure, Return, Ref (only the segment references indicated in the node SegmentReferences).|
| BaggageTypes/BaggageType/<br>References					| 0..1		||	References for the Baggage Type.|
| BaggageTypes/BaggageType/<br>References/SegmentReferences	| 0..1		||	Contains a list of segment references for the Baggage Type.|
| BaggageTypes/BaggageType/<br>References/SegmentReferences/<br>SegmentReference		| 1..n	||	Segment reference.|
| @itineraryRef						| 1 		| Integer	| Unique identifier of the Itinerary.|
| @journeyRef						| 1 		| Integer	| Unique identifier of the Journey.|
| @segmentRef						| 1 		| Integer	| Unique identifier of the Segment.|
| BaggageTypes/BaggageType/<br>References/PaxReferences		| 0..1	||	Contains a list of passenger references for the Baggage Type.|
| BaggageTypes/BaggageType/<br>References/PaxReferences/<br>PaxReference		| 1..n	||	Passenger reference.|
| @paxRef							| 1 		| String	| Reference to the passenger.|
| BaggageTypes/BaggageType/Baggage	| 1..n		|			| Details of the baggage.|
| @id                    			| 0..1 		| String	| Unique identifier of the Baggage.|
| @type                  			| 1 		| String	| Type of baggage: Bag, Bike, Wheelchair, Skis, BabyTrolley and HandBaggage.|
| @quantity              			| 1 		| Integer	| Baggage quantity.|
| @maxWeightPerUnit					| 0..1 		| Integer	| Maximum weight of the baggage.| 
| @maxTotalWeight        			| 0..1 		| Integer	| Maximum weight of ALL the baggage.|
| @paymentInAirpot       			| 0..1 		| Boolean	| Determines whether the pay is in station.|
| @code								| 0..1 		| String	| Code of the Baggage.|
| @carrier               			| 0..1 		| String	| Carrier.|
| @needToken						| 0..1 		| Boolean	| Reserve token mandatory.|
| @reservationToken             	| 0..1 		| String	| Reserve token.|
| @description             			| 0..1 		| String	| Baggage description.|
| BaggageTypes/BaggageType/Baggage/<br>BaggageCharge		| 0..1 || Details of the baggage charge.|
| @fixAmount             			| 0..1 		| Decimal	| Total fixed amount.|
| @appliesFixAmount             	| 0..1 		| String	| The fixed amount applies to: PorReserva(Reservation), PorPasajero(Passenger), PorSegmento(Segment), TarifaBase(Base Fare), Tasas(Taxes), ForAdt(Adult passengers), ForChd(Children passengers), ForInf(Infant passengers).|
| @minFixAmount             		| 0..1 		| Decimal	| Minimal fixed amount.|
| @maxFixAmount             		| 0..1 		| Decimal	| Maximal fixed amount.|
| @minAmountPercentage             	| 0..1 		| Decimal	| Minimal percentage amount.|
| @maxAmountPercentage             	| 0..1 		| Decimal	| Maximal percentage amount.|
| @currency             			| 1 		| String	| Currency.|
| @percentage             			| 0..1 		| Decimal	| Total percentage amount.|
| @percentageApplied             	| 0..1 		| String	| The percentage amount applies to: PorReserva(Reservation), PorPasajero(Passenger), PorSegmento(Segment), TarifaBase(Base Fare), Tasas(Taxes), ForAdt(Adult passengers), ForChd(Children passengers), ForInf(Infant passengers).|
| SpecialSupplements				| 0..1		|			| Contains a list of SpecialSupplements.|
| SpecialSupplements/SpecialSupplement						| 1..n	||	Contains information about the Special Supplement.|
| @id								| 0..1		| String	| Unique identifier of the supplement.|
| @code								| 0..1		| String	| Supplement code.|
| @height							| 0..1		| Integer	| Dimension of the supplement: height.|
| @width							| 0..1		| Integer	| Dimension of the supplement: width.|
| @length							| 0..1		| Integer	| Dimension of the supplement: length.|
| @weight							| 0..1		| Integer	| Dimension of the supplement: weight.|
| @quantity							| 0..1		| Integer	| Quantity of supplements.|
| @description						| 0..1		| String	| Description of the supplement|
| @carrier							| 0..1		| String	| Carrier selling the supplement.|
| @status							| 0..1		| String	| Status of the supplement: N(None), INC(Included in the price), CHA(Avalilable with charges), NOF(Not offered).|
| @needToken						| 0..1		| Boolean	| If true, the field @reservationToken should be filled.|
| @type								| 1			| String	| Type of supplement: Miscelaneous, Seat, Meal, Pet, Lounge, Baggage, Canoe, PreferentialBoarding, Bike, Trailer, Seguro, Embarque_Prioritario, Acceso_Preferente, Bloqueo_Tarifa, Special_Assistance.|
| @reservationToken					| 0..1		| String	| Reservation Token of the supplement.|
| @ownTransportation				| 0..1		| Boolean	| If true, the supplement includes own transportation cage.|
| SpecialSupplements/SpecialSupplement/<br>References		| 0..1	||	References for the Special Supplement.|
| SpecialSupplements/SpecialSupplement/<br>References/SegmentReferences		| 0..1	||	Contains a list of segment references for the Special Supplement.|
| SpecialSupplements/SpecialSupplement/<br>References/SegmentReferences/<br>SegmentReference		| 1..n	||	Segment reference.|
| @itineraryRef						| 1 		| Integer	| Unique identifier of the Itinerary.|
| @journeyRef						| 1 		| Integer	| Unique identifier of the Journey.|
| @segmentRef						| 1 		| Integer	| Unique identifier of the Segment.|
| SpecialSupplements/SpecialSupplement/<br>References/PaxReferences		| 0..1	||	Contains a list of passenger references for the Special Supplement.|
| SpecialSupplements/SpecialSupplement/<br>References/PaxReferences/PaxReference		| 1..n	||	Passenger reference.|
| @paxRef							| 1 		| String	| Reference to the passenger.|
| SpecialSupplements/SpecialSupplement/<br>SupplementCharge	| 0..1	||	Details of the special supplement charge.|
| @fixAmount             			| 0..1 		| Decimal	| Total fixed amount.|
| @appliesFixAmount					| 0..1 		| String	| The fixed amount applies to: PorReserva(Reservation), PorPasajero(Passenger), PorSegmento(Segment), TarifaBase(Base Fare), Tasas(Taxes), ForAdt(Adult passengers), ForChd(Children passengers), ForInf(Infant passengers).|
| @minFixAmount             		| 0..1 		| Decimal	| Minimal fixed amount.|
| @maxFixAmount             		| 0..1 		| Decimal	| Maximal fixed amount.|
| @minAmountPercentage             	| 0..1 		| Decimal	| Minimal percentage amount.|
| @maxAmountPercentage             	| 0..1 		| Decimal	| Maximal percentage amount.|
| @currency             			| 1 		| String	| Currency.|
| @percentage             			| 0..1 		| Decimal	| Total percentage amount.|
| @percentageApplied             	| 0..1 		| String	| The percentage amount applies to: PorReserva(Reservation), PorPasajero(Passenger), PorSegmento(Segment), TarifaBase(Base Fare), Tasas(Taxes), ForAdt(Adult passengers), ForChd(Children passengers), ForInf(Infant passengers).|
| Seating							| 0..1    	|			| Seating availability.|
| Seating/BlockRules				| 1    		|			| Contains a list of Block Rules.|
| Seating/BlockRules/BlockRule 		| 1..n    	|			| Block Rules.|
| Seating/BlockRules/BlockRule/References					| 1    		|| References for the Block Rule.|
| Seating/BlockRules/BlockRule/References/<br>BlockReferences		| 1	||	Contains a list of references to block elements.|
| Seating/BlockRules/BlockRule/References/<br>BlockReferences/BlockReference | 1..n || Block element reference.|
| @blockTypeRef						| 1  		| String	| Block type: CABIN (The entire cabin of the plane).|
| @blockRef							| 1  		| Integer	| Block reference.|
| Seating/BlockRules/BlockRule/References/<br>SegmentReferences		| 0..1	||	Contains a list of segment references for the Block Rule.|
| Seating/BlockRules/BlockRule/References/<br>SegmentReferences/SegmentReference		| 1..n	||	Segment reference.|
| @itineraryRef						| 1 		| Integer	| Unique identifier of the Itinerary.|
| @journeyRef						| 1 		| Integer	| Unique identifier of the Journey.|
| @segmentRef						| 1 		| Integer	| Unique identifier of the Segment.|
| Seating/BlockRules/BlockRule/References/<br>PaxReferences	| 0..1	||	Contains a list of passenger references for the Special Supplement.|
| Seating/BlockRules/BlockRule/References/<br>PaxReferences/PaxReference		| 1..n	||	Passenger reference.|
| @paxRef							| 1 		| String	| Reference to the passenger.|
| Seating/BlockRules/BlockRule/BlockPrice					| 0..1  	|| Price element.|
| Seating/BlockRules/BlockRule/BlockPrice/<br>Amount		| 0..1  	|| Amount by type.|
| @currency							| 1  		| String	| Currency code of the amount.|
| @amount                 			| 1  		| Decimal	| Amount.|
| @amountType             			| 0..1  	| String	| Amount type: AMOUNT (Amount), FEE (Service Fee), TOTAL (Total), PERCENTUAL (Percentual).|
| Seating/Blocks					| 1    		|			| Contains a list of seating blocks.|
| Seating/Blocks/Block				| 1..n    	|			| Seating details.|
| @type								| 1  		| String	| Block type: CABIN (The entire cabin of the plane).|
| @id								| 1  		| Integer	| Unique id.|
| Seating/Blocks/Block/References/<br>SegmentReferences		| 1	||	Contains a list of segment references for the Block.|
| Seating/Blocks/Block/References/<br>SegmentReferences/SegmentReference		| 1..n	||	Segment reference.|
| @itineraryRef						| 1 		| Integer	| Unique identifier of the Itinerary.|
| @journeyRef						| 1 		| Integer	| Unique identifier of the Journey.|
| @segmentRef						| 1 		| Integer	| Unique identifier of the Segment.|
| Seating/Blocks/Block/Blocks		| 1    		|			| Contains a list of row blocks.|
| Seating/Blocks/Block/Blocks/Block | 1..n    	|			| Row block.|
| @type    							| 1  		| String	| Block type: ROW.|
| @id     							| 1  		| Integer	| Unique row id.|
| @number							| 1  		| Integer	| Row number in the cabin.|
| Seating/Blocks/Block/Blocks/Block/<br>Blocks				| 1    	|| Contains a list of seat blocks.|
| Seating/Blocks/Block/Blocks/Block/<br>Blocks/Block		| 1..n  || Seat block.|
| @type								| 1  		| String	| Block type: SEAT.|
| @id								| 1  		| Integer	| Unique seat id.|
| @number    						| 1  		| String	| Seat identifier.|
| @token    						| 0..1  	| String	| Reservation seat token.|
| Seating/Blocks/Block/Blocks/Block/<br>Blocks/Block/Availability | 0..1 || Availability of the seat.|
| @isAvailable						| 1  		| Boolean	| Indicates whether the seat is available.|
| Seating/Blocks/Block/Blocks/Block/<br>Blocks/Block/BlockAttributes | 0..1 || Contains a list of Seat attributes.|
| Seating/Blocks/Block/Blocks/Block/<br>Blocks/Block/BlockAttributes/<br>BlockAttribute | 1..n || Seat attribute.|
| @type                   			| 1  		| String	| [Seat type.](#valuation-enumerate-description)|
| Conditions						| 0..1		|			| Contains a list of applied fare conditions.|
| Conditions/Condition				| 1..n		|			| Details of the condition.|
| @carrier							| 0..1		| String	| Carrier applying the condition.|
| @code								| 0..1		| String	| Code of the condition.|
| @id								| 0..1		| String	| Unique id of the condition.|
| @language							| 0..1		| String	| Language in which the condition is written.|
| @Text								| 0..1		| String	| Description of the condition.|
| Conditions/Condition/Paragraph	| 0..n		|			| List of Sentences and titles.|
| @title							| 0..1		| String	| Title content.|
| Conditions/Condition/Paragraph/Sentence					| 0..n | String	| List of Sentences contents.|
| SummarizedConditions				| 0..1		|			| Summarized applied fare conditions.|
| SummarizedConditions/FareRuleTypes| 0..1		|			| Contains a list of fare rules.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType		| 1..n || Fare rule details.|
| @id								| 1			| String	| Unique id of the fare rule.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/TicketingRules | 0..1 || Ticketing rules details.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/TicketingRules/<br>DatesTypes | 0..n || Contains a list of Date type elements.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/TicketingRules/<br>DatesTypes/DatesType | 1..n || Date details.|
| @type								| 0..1		| String	| Date type.|
| @date								| 1			| Date		| Ticketing date.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/MinimumStayRules | 0..1 || Minimum stay rules details.|
| @location							| 1			| String	| Location concerning the minimum stay.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/MinimumStayRules/<br>DatesTypes | 0..n || Contains a list of Date type elements.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/MinimumStayRules/<br>DatesTypes/DatesType | 1..n || Date details.|
| @type								| 0..1		| String	| Date type.|
| @date								| 1			| Date		| Date.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/MaximumStayRules | 0..1 || Maximum stay rules details.|
| @location							| 1			| String	| Location concerning the maximum stay.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/MaximumStayRules/<br>DatesTypes | 0..n || Contains a list of Date type elements.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/MaximumStayRules/<br>DatesTypes/DatesType | 1..n || Date details.|
| @type								| 0..1		| String	| Date type.|
| @date								| 1			| Date		| Date.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/Penalty | 0..1 || Penaly rules details.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/Penalty/<br>DatesTypes | 0..n || Contains a list of Date type elements.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/Penalty/<br>DatesTypes/DatesType | 1..n || Date details.|
| @type								| 0..1		| String	| Date type.|
| @date								| 1			| Date		| Date.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/Penalty/AmountTypes | 0..n || Contains a list of amount types.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/Penalty/AmountTypes/<br>AmountType | 1..n || Amount details.|
| @type								| 0..1		| String	| Date type.|
| @date								| 0..1		| Date		| Date.|
| @currency							| 0..1		| String	| Currency.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/Penalty/RestrictionTypes | 0..n || Contains a list of restriction types.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/Penalty/RestrictionTypes/<br>RestrictionType | 1..n || Restriction details.|
| @type								| 0..1		| String	| Restriction type.|
| @application						| 1			| Boolean	| If true, the restriction applies to the fare.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/ReissueRules | 0..1 || Reissue rules details.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/ReissueRules/<br>DatesTypes | 0..n || Contains a list of Date type elements.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/ReissueRules/<br>DatesTypes/DatesType | 1..n || Date details.|
| @type								| 0..1		| String	| Date type.|
| @date								| 1			| Date		| Date.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/ReissueRules/AmountTypes | 0..n || Contains a list of amount types.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/ReissueRules/AmountTypes/<br>AmountType | 1..n || Amount details.|
| @type								| 0..1		| String	| Date type.|
| @date								| 0..1		| Date		| Date.|
| @currency							| 0..1		| String	| Currency.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/ReissueRules/RestrictionTypes | 0..n || Contains a list of restriction types.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/ReissueRules/RestrictionTypes/<br>RestrictionType | 1..n || Restriction details.|
| @type								| 0..1		| String	| Restriction type.|
| @application						| 1			| Boolean	| If true, the restriction applies to the fare.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/RefundRules| 0..1 || Refund rules details.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/RefundRules/<br>DatesTypes | 0..n || Contains a list of Date type elements.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/RefundRules/<br>DatesTypes/DatesType | 1..n || Date details.|
| @type								| 0..1		| String	| Date type.|
| @date								| 1			| Date		| Date.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/RefundRules/AmountTypes | 0..n || Contains a list of amount types.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/RefundRules/AmountTypes/<br>AmountType | 1..n || Amount details.|
| @type								| 0..1		| String	| Date type.|
| @date								| 0..1		| Date		| Date.|
| @currency							| 0..1		| String	| Currency.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/RefundRules/RestrictionTypes | 0..n || Contains a list of restriction types.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/RefundRules/RestrictionTypes/<br>RestrictionType | 1..n || Restriction details.|
| @type								| 0..1		| String	| Restriction type.|
| @application						| 1			| Boolean	| If true, the restriction applies to the fare.|
| SummarizedConditions/FareRuleApplicabilities				| 0..1 || Contains a list of fare rules aplicability.|
| SummarizedConditions/FareRuleApplicabilities/<br>FareRulesApplicability | 1..n || Contains a list of fare rules aplicability.|
| SummarizedConditions/FareRuleApplicabilities/<br>FareRulesApplicability/OriginDestinationIds | 0..1 |	| Contains a list of Origin Destination identificators.|
| SummarizedConditions/FareRuleApplicabilities/<br>FareRulesApplicability/OriginDestinationIds/<br>OriginDestinationId | 1..n || List of Origin and Destinations pairs involved in the fare rule.|
| @origin							| 1			| String	| Origin.|
| @destination						| 1			| String	| Destination.|
| SummarizedConditions/FareRuleApplicabilities/<br>FareRulesApplicability/PaxReferences | 0..1 || Contains a list of pasengers involved in the fare rules.|
| SummarizedConditions/FareRuleApplicabilities/<br>FareRulesApplicability/PaxReferences/<br>PaxReference| 1..n || List of references to pasengers related to the fare rule.|
| @paxRef							| 1			| String	| Reference to a specific pasenger.|
| SummarizedConditions/FareRuleApplicabilities/<br>FareRulesApplicability/FareRulesReferences | 0..1 || Contains a list of fare rules.|
| SummarizedConditions/FareRuleApplicabilities/<br>FareRulesApplicability/FareRulesReferences/<br>FareRulesReference| 1..n || List of references to fare rules.|
| @FareRulesRefType					| 1			| String	| Reference to a fare rule.|
| Installments						| 0..1		|			| Contains a list of Installments.|
| Installments/Installment			| 1..n		|			| Installment details.|
| @number							| 1			| Integer	| Number of installments.|
| @currency							| 0..1		| String	| Currency.|
| Installments/Installment/PaymentCharge					| 0..1 || First installment amount.|
| Installments/Installment/InterestRate						| 0..1 || Interest rate.|
| Installments/Installment/<br>RemainingInstallmentAmount	| 0..1 || Remaining installment amount.|
| Installments/Installment/<br>RemainingInstallmentTotalAmount | 0..1 || Remaining installment total amount.|
