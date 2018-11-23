---
title: Valuation
keywords: transportation, data structure, flights, valuation
search: Transportation - Flights - Data Structure - Valuation
sidebar: mydoc_sidebar
permalink: /docs/transportation/DSF/flights/valuation
---



### Method Goals


This method aims to return the total price of the selected Option. This
Option **must** be selected in the previous step ( Availability ).


### Request Format


The Valuation request can be done by two different ways: with a single
Itinerary or multiple Itineraries.

-   Multiple Itineraries :

In this method, the request will have as many Itineraries as there are
Journeys . Mainly used for **one-way** tickets. There's a total price
for each selected SegmentInfo.

-   Single Itinerary with one or more Journeys :

This case is used for **round trip** tickets. There's only one
**totalAmount** (fare, tax and discount) for all the selected Journey .

The decision of which strategy to take is done beforehand, depending on
the business rules.



### Response Format


The returned XML is very similar to the result in the Availability call.
The main difference is that there is only one node Option returned. The
totalAmount is definitive. Sometimes this method will fail since the
selected Option at Availability may not be available for this stage.



### Remarks


Some suppliers do not provide this method. If this is the case then all
of the information **must** be returned in the Availability, therefore
the Valuation call will do the Availability process again filtered by
the selected Option.




### ValoracionRQ Example


~~~xml
    <ValuationRQ>
        <ClientConfiguration currencyCode = "EUR"/>
        <Itineraries>
            <Itinerary id="0" carrier = "UX">
                 <Conditions>
                     <Condition id="1" language="en"/>
                 </Conditions>
                <Journeys>
                    <Journey id="0">
                        <Segments>
                            <Segment id="0">
                                <SegmentInfo transportationId = "0B104" transportationType = "V" operatingCarrier = "0B" marketingCarrier = "0B" departureDate = "2014-03-23T10:20:00" arrivalDate = "2014-03-23T15:15:00" planeType = "734" segmentStatus = "HK" electronicTicket = "true" hasTechnicalStop = "false">
                                    <OriginLoc type = "A" code = "MAD" cityCode = "false"/>
                                    <DestinationLoc type = "A" code = "OTP" cityCode = "false"/>
                                </SegmentInfo>
                                <SegmentClasses>
                                    <SegmentClass cabinClass = "Y" class = "K" paxRef = "0" fareBasis = "WEB14" fareType = "PUB"/>
                                </SegmentClasses>
                                <ReservationTokens>
                                    <Attribute key = "FareSequence" value = "88"/>
                                    <Attribute key = "RuleNumber" value = "0001"/>
                                </ReservationTokens>
                            </Segment>
                        </Segments>
                    </Journey>
                </Journeys>
                <ChargeBreakdown currency = "EUR" totalAmount = "109.9000">
                    <ChargeBreakdowns/>
                    <PaxBreakdowns>
                        <PaxBreakdown paxType = "ADT" amount = "109.9000"/>
                    </PaxBreakdowns>
                </ChargeBreakdown>
                <PaxConfigurations>
                    <PaxConfiguration id = "0" paxRef = "0" age = "30" paxType = "ADT">
                        <AppliedBonuses resident = "N" largeFamily = "N" discountCard = "N"/>
                    </PaxConfiguration>
                </PaxConfigurations>
                <ConfigurationesVehiculos/>
                <Emisiones/>
            </Itinerary>
            <Itinerary id="1" carrier = "UX">
                <Journeys>
                    <Journey id="0">
                        <Segments>
                            <Segment id="0">
                                <SegmentInfo transportationId = "UX103" transportationType = "V" operatingCarrier = "0B" marketingCarrier = "0B" departureDate = "2014-03-25T15:30:00" arrivalDate = "2014-03-25T18:35:00" maxCheckinDate = "0001-01-01T00:00:00" planeType = "734" segmentStatus = "HK" electronicTicket = "true" hasTechnicalStop = "false">
                                    <OriginLoc type = "A" code = "OTP" cityCode = "false"/>
                                    <DestinationLoc type = "A" code = "MAD" cityCode = "false"/>
                                </SegmentInfo>
                                <SegmentClasses>
                                    <SegmentClass cabinClass = "Y" class = "L" paxRef = "0" fareBasis = "WEB13" fareType = "PUB"/>
                                </SegmentClasses>
                                <ReservationTokens>
                                    <Attribute key = "FareSequence" value = "88"/>
                                    <Attribute key = "RuleNumber" value = "0001"/>
                                </ReservationTokens>
                            </Segment>
                        </Segments>
                    </Journey>
                </Journeys>
                <ChargeBreakdown currency = "EUR" totalAmount = "99.9000">
                    <ChargeBreakdowns/>
                    <PaxBreakdowns>
                        <PaxBreakdown paxType = "ADT" amount = "99.9000" taxes = "0" tasaDU = "0"/>
                    </PaxBreakdowns>
                </ChargeBreakdown>
                <PaxConfigurations>
                    <PaxConfiguration id = "0" paxRef = "0" age = "30" paxType = "ADT">
                        <AppliedBonuses resident = "N" largeFamily = "N" discountCard = "N"/>
                    </PaxConfiguration>
                </PaxConfigurations>
            </Itinerary>
        </Itineraries>
    </ValuationRQ>
~~~


### ValoracionRQ Description



| **Element**				| **Number**	| **Type**	| **Description**							|
| ------------------------------------- | ------------- | ------------- | --------------------------------------------------------------------- |
| ValuationRQ                 		| 1     	|		| Root node.|
| Itineraries                 		| 1     	|		| Contains a list of Itineraries.|
| Itineraries/Itinerary       		| 1..n    	|		| Details of the Itinerary.|
| @id                    		| 1 		| Integer	| Unique identifier of the Itinerary.|
| @fareRef	               		| 1 		| String	| Reference identifier to the original Fare.|
| @hasObFees             		| 1 		| Boolean	| If true then there is an extra fee for using credit card.|
| @carrier               		| 1 		| String	| Validating carrier.|
| Itineraries/Itinerary/Conditions	| 1 |	| Contains a list of Fare Conditions. |
| Itineraries/Itinerary/Conditions/Condition	| 1 |	| Contains details of the Condition that applies to the condition. |
| @cia	| 1	| String	| Carrier applying the condition.	|
| @code	| 1	| String	| Code of the condition.	|
| @id	| 1	| String	| Unique id of the condition.	|
| @language	| 1	| String	| Language in which the condition is written.	|
| @Text | 1	| String	| Description of the condition.	|
| Transportation/Fares/Fare/Conditions/<br>Condition/Paragraph	| 1 | | List of Sentences and titles. |
| @title | 1	| String	| Title content.	|
| Transportation/Fares/Fare/Conditions/<br>Condition/Paragraph/Sentence	| 1 | String	| List of Sentences contents. |
| Itineraries/Itinerary/Journeys	| 0..1    	|		| Contains a list of Journeys.|
| Itineraries/Itinerary/Journeys/Journey | 0..n    	|		| Contains details of the Journeys.|
| @id     | 1 		| Integer	| Unique identifier of the Journey in scope.|
| @duration   | 0..1 		| Integer	| Duration of the Journey in minutes. |
| @familyFare | 0..1 		| String	| Family fare name of the Journey.|
| @checkinStart   | 0..1 		| Date	| Checkin start date. |
| @checkinEnd   | 0..1 		| Date	| Checkin end date. |
| Itineraries/Itinerary/Journeys/Journey/<br>Segments | 1 |   		| Contains a list of Segments associated to the Journey.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment | 1..n   |	| Contains details of the SegmentInfo.|
| @id      | 1 		| Integer	| Unique SegmentInfo identifier.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentInfo | 1 | | Contains information of the Segment.|
| @id     | 1 		| Integer	| Unique identifier of the SegmentInfo.|
| @transportationId     | 1 		| String	| Unique Id of the transportation.|
| @transportationType    		| 1 		| String	| Transport type: V ( Flight ), T ( Train ), B ( Bus ), S() & F ( Ferry ).	|
| @transportationName    		| 1 		| String	| Name of the transportation.	|
| @transportationCode	| 1	| String	| Code of the transportation. |
| @operatingCarrier      		| 1 		| String	| Company which operates the transportation.		|
| @marketingCarrier      		| 1 		| String	| Company which commercializes the transportation.	|
| @departureTerminal     | 1 		| String	| Departure terminal.|
| @arrivalTerminal       		| 1 		| String	| Arrival terminal.|
| @departureDate         		| 1 		| Date		| Departure date.|
| @arrivalDate           		| 1 		| Date		| Arrival date. |
| @segmentDuration       		| 1 		| Integer	| Transport duration ( in minutes ).|
| @segmentStatus	| 1	| String	| Segment status: HK (Holding confirmed), TK(Confirming new flight times), UC(Unable to confirm), UN(Flight cancelled by airline), NO (No action taken), UD (Undefined). |
| @planeType | 1 		| String	| Plane type. Flights parameter.|
| @maxCheckinDate     | 1 		| String	| Maximum date to make the check-in.|
| @hasTechnicalStop   | 1 | Boolean	| If true, the segment has a technical stop. 		|
| @electronicTicket      		| 1 		| Boolean	| If true, the segment uses a electronic ticket. 	| 
| @secureFlight          		| 0..1		| Boolean	| If true, the provider requires extra information of the passengers. Flights parameter.	|
| Transportation/Segments/Segment/OriginLoc | 1     	|		| Origin location.					|
| @type                  		| 1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).	|
| @code                  		| 1 		| String	| Location code.					|
| @name	| 1 		| String	| Location full name.	|
| @radius					| 0..1			| Integer	| Area radius from location.|
| @cityCode              		| 1 		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.	|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/OriginLoc/<br>AlternativeLocations	| 0..1		|	| Contains a list of AlternativeLocations.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/OriginLoc/<br>AlternativeLocations/AlternativeLocation	| 0..n	|	| Contains the information of the alternative location.|
| @code						| 1			| String	| Location code.|
| @cityCode        			| 1  		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.|
| @name						| 0..1			| String	| Location long name.|
| @type						| 0..1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/DestinationLoc | 1   |  		| Destination location.					|
| @type  | 1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).	|
| @code                  		| 1 		| String	| Location code. 					|
| @name	| 1 		| String	| Location full name.	|
| @radius					| 0..1			| Integer	| Area radius from location.|
| @cityCode              		| 1 		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.	||
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/<br>DestinationLoc/AlternativeLocations	| 0..1		|	| Contains a list of AlternativeLocations.
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/<br>DestinationLoc/AlternativeLocations/<br>AlternativeLocation	| 0..n	|	| Contains the information of the alternative location.|
| @code						| 1			| String	| Location code.|
| @cityCode        			| 1  		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.|
| @name						| 0..1			| String	| Location long name.|
| @type						| 0..1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/TechnicalStops | 0..1 |   		| Contains a list of TechnicalStops.		|
| @totalTechnicalStops   | 1 		| Integer	| Total number of TechnicalStops.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/TechnicalStops/<br>TechnicalStop | 1..n | | Contains the details of the TechnicalStop.|
| @location          | 1 		| String	| TechnicalStop location.|
| @stopDate       | 1 		| Date		| Approx. stop date and time.|
| @departureDate    | 1 		| Date		| Approx. departure date and time.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses | 0..1 |  | Contains a list of SegmentClasses.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses | 1 | | Contains a list of SegmentClasses.	|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses/<br>SegmentClass | 1..n | | Contains details of the SegmentClass.   |
| @cabinClass            		| 1 		| String	| Cabin class of the seat: N (Not specified), Y (Tourist), C (Business), F (First), CA (Cabin, only for ferries), YP (Tourist Plus).	|
| @class                 		| 1 		| String	| Fare class. |
| @paxRef               	 	| 1 		| Integer	| Passenger reference. 					|
| @fareBasis             		| 1 		| String	| Identifier of the fare.				|
| @fareType              		| 1 		| String	| Fare type: PUB ( Public ), PRI ( Private ), NEGO ( Negotiated ) and CORP ( Corporate ).	|
| @avail                 		| 1 		| Integer	| Available seats remaining for this class (In flights, the maximum is 9).  |
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses/<br>SegmentClass/Modifiable | 0..1 |  | Contains the information of the modifiable fare.	|
| @Description                 		| 1 		| String	| Modification description. |
| @amount                 			| 1 		| Decimal	| Modification amount. |
| @modifiable                 		| 1 		| Boolean	| If true, the fare allows this modification. |
| @currency                 		| 1 		| String	| Modification currency. |
| @amountType                 		| 1 		| String	| Modification amount type: AMOUNT (Fare amount), FEE (Fee amount), TOTAL (Total fare amount), PERCENTUAL (Percentual amount). |
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses/<br>SegmentClass/CancellationPolicies | 0..1 |  | Contains a list of CancellationPolicies.	|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses/<br>SegmentClass/CancellationPolicies/<br>CancellationPolicy | 1..n |  |Contains details of the CancelationPolicy.	|
| @fromDate                 		| 1 		| Date	| Date of the begining of the policy. |
| @amount                 			| 1 		| Decimal	| Policy amount. |
| @refundable                 		| 1 		| Boolean	| If true, the fare allows the refundation. |
| @currency                 		| 1 		| String	| Policy currency. |
| @amountType                 		| 1 		| String	| Policy amount type: AMOUNT (Fare amount), FEE (Fee amount), TOTAL (Total fare amount), PERCENTUAL (Percentual amount).|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/ReservationTokens | 0..1 |  | Specific attribute used for each provider.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/ReservationTokens/<br>Attribute | 0..n |  | Type of attribute.|
| @key   | 1 		| String	| Contains the keyword/ Id to identify a parameter.	|
| @value     | 1 		| String	| Contains the value of the parameter.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/CheckinInformation | 0..1 |  | Checkin information.|
| @openingTime | 1 		| Date	| Checkin opening time.|
| @closingTime | 1 		| Date	| Checkin closing time.|
| @estimatedCheckinTime | 1 		| Date	| Estimated checkin time.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/CheckinInformation/<br>Status | 1 |  | Status checkin information.|
| @isAvailable | 1 		| Boolean	| If true, the cheking is available.|
| @direction | 1 		| String	| Direction of the journey about to checkin: DEPARTURE (Outbound), RETURN (Inbound), IDA_VUELTA (Outbound and Inbound).|
| @status | 1 		| String	| Status of the checkin: UNDEFINED, IN_PROGRESS, ERROR, COMPLETE, UNCONFIRMED.|
| Itineraries/Itinerary/AmountBreakdown  		| 1     	|		| Breakdown of the fare amount.|
| @currency  | 1 		| String	| Currency code of the fare.|
| @totalAmount           		| 1 		| Decimal	| Total amount. with taxes and other charges included.|
| @notCommissionableAmount		| 1 		| Decimal	| Total amount that can not be commissioned.  		|
| @commission            		| 1 		| Decimal	| Commission. 						|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakdowns | 0..1   |		| Contains a list of breakdown amounts ( taxes, mandatory charges.. ).	|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakdowns/ChargeBreakdown | 1..n |	| Contains details of the BreakdownAmount.	|
| @type                  		| 1 		| String	| [Type of charge.](#valuation-enumerate-description) |
| @amount                		| 1    	 	| Decimal	| Charge amount.				|
| @included				| 1		| Boolean	| If true, the charge is included to the total fare amount |
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakdowns/ChargeBreakdown<br>/Concept | 0..1 | | Contains details of the charge.|
| @id                    		| 1 		| String	| Unique id of the Concept	|
| @language              		| 1 		| String	| Language.			|
| @cia              		| 1 		| String	| Carrier.			|
| @code              		| 1 		| String	| Concept code.			|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakDowns/ChargeBreakdown<br>/Concept/Text | 1 | String | Remarks.	|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakDowns/ChargeBreakdown<br>/Concept/Paragraph | 1 |  | Contains a list of Sentences and titles.	|
| @title	| 1	| String	| Title.	|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakDowns/ChargeBreakdown/<br>Concept/Paragraph/Sentence | 1 | String | Sentence|
| Itineraries/Itinerary/AmountBreakdown/<br>PaxBreakdown | 0..1    	|		| Contains a list of breakdown amounts for each passenger ( ADT amount, etc. ).|
| Itineraries/Itinerary/AmountBreakdown/<br>PaxBreakdowns/PaxBreakdown | 0..n | 	| Contains details of breakdown amounts for each passenger.|
| @paxType               		| 1 		| String	| Passenger type: ADT ( Adult ), CHD ( Child ) & INF ( Infant ).|
| @amount                		| 1 		| Decimal	| Total amount, with taxes included, associated to the passenger.	|
| @taxes                 		| 1 		| Decimal	| If they exist, taxes are applied for this passenger type. |
| @tasaDU                		| 1 		| Decimal	| DU taxes. 						|
| @fees                			| 1 		| Decimal	| Fees. 						|
| Itineraries/Itinerary/AmountBreakdown/<br>PaxBreakdowns/PaxBreakdown/<br>Taxes | 0..1 | 	| Contains a list of Taxes.|
| Itineraries/Itinerary/AmountBreakdown/<br>PaxBreakdowns/PaxBreakdown/<br>Taxes/Tax | 0..n | 	| Code and amount of each tax.|
| @code				| 1	| String	| Code.	|
| @amount				| 1	| Decimal	| Amount.	|
| Itineraries/Itinerary/PaxConfigurations		| 1     	|		| Contains a list of PaxConfiguration.	|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration | 1..n |   		| Contains details of PaxConfiguration.	|
| @id                    		| 1 		| Integer	| Unique identifier of the PaxConfiguration. 		|
| @paxRef                		| 1 		| Integer	| Reference to the passenger Id from the request. 	|
| @age                   		| 1 		| Integer	| Age of the passenger. 				|
| @nacionality                   	| 1 		| String	| Nacionality of the passenger. 			|
| @paxType               		| 1 		| String	| Passenger type based on the age of the passenger: ADT (Adult), CHD (Child), INF (Infant), YOU (Young) and SEN (Senior).	|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses | 0..1 | | Applied discounts.			|
| @resident              	| 1 		| String	| [Resident discount type.](#valuation-enumerate-description)|
| @largeFamily           		| 1 		| String	| Family discount type: N(None), F1(Large family), F2 (Special large family). |
| @discountCardCode		| 0..1	| String	| Discount card code.|
| @discountCard		| 0..1	| String	| [Discount card type.](#valuation-enumerate-description)|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses/<br>DiscountCards	| 0..1	|	| Contains a list of DiscountCards.|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses/<br>DiscountCards/DiscountCard| 1..n	|	| DiscountCard details.|
| @code	| 1	| String | Discount card code.|
| @id	| 1	| String	| Unique identifier of discound card.|
| @type	| 1	| String	| [Discount card type.](#valuation-enumerate-description)|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses/<br>PaxTypeCodes		| 0..1	|		| Contains a list of PaxTypeCodes.|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses/<br>PaxTypeCodes/PaxTypeCode	| 0..n	|	| Contains the code type of the passenger.|
| @code		| 1		| String	| Code type of the passenger.|
| Itineraries/Itinerary/Emissions	| 0..1	|	| Contains a list of Issuances.|
| Itineraries/Itinerary/Emissions/<br>Emission	| 0..n	|	| Contains the key of the Issuance.|
| @key		| 1		| String	| Key of the Issuance.|
| Preferences	| 0..1	|	| Valuation preferences.|
| @paymentMethods		| 1		| Boolean	| If true, the Valuation will return the list of payment methods available for the Itineraries.|
| @baggageTypes		| 1		| Boolean	| If true, the Valuation will return the list of baggage allowance available for the Itineraries.|
| @specialSupplements		| 1		| Boolean	| If true, the Valuation will return the list of special suplements available for the Itineraries.|
| @extendedFareRules		| 1		| Boolean	| If true, the Valuation will return a list of detailed fare rules of the Itineraries.|
| @summarizedFareRules		| 1		| Boolean	| If true, the Valuation will return a list of summarired fare rules of the Itineraries.|
| @seating		| 1		| Boolean	| If true, the Valuation will return the list of seats available in the plane.|
| @pagoPlazos		| 1		| Boolean	| If true, the Valuation will return the list of partial payment rules (installments) available for the Itineraries.|
| SpecialSupplements	| 0..1	|	|	Contains a list of SpecialSupplements.
| SpecialSupplements/SpecialSupplement		| 0..n	|	|	Contains information about the Special Supplement	|
| @id	| 1	| String	| Unique identifier of the supplement.|
| @code	| 1	| String	| Supplement code.|
| @height	| 0..1	| Integer	| Dimension of the supplement: height.|
| @width	| 0..1	| Integer	| Dimension of the supplement: width.|
| @length	| 0..1	| Integer	| Dimension of the supplement: length.|
| @weight	| 0..1	| Integer	| Dimension of the supplement: weight.|
| @quantity	| 0..1	| Integer	| Quantity of supplements.|
| @description	| 0..1	| String	| Description of the supplement|
| @carrier	| 1	| String	| Carrier selling the supplement.|
| @estado	| 0..1	| String	| Status of the supplement: N(None), INC(Included in the price), CHA(Avalilable with charges), NOF(Not offered).|
| @needToken	| 1	| Boolean	| If true, the field @reservationToken should be filled|
| @type	| 1	| String	| Type of supplement: Miscelaneous, Seat, Meal, Pet, Lounge, Baggage, Canoe, PreferentialBoarding, Bike, Trailer, Seguro, Embarque_Prioritario, Acceso_Preferente, Bloqueo_Tarifa, Special_Assistance.|
| @reservationToken	| 0..1	| String	| Reservation Token of the supplement.|
| @ownTransportation	| 0..1	| Boolean	| If true, the supplement includes own transportation cage.|



### ValuationRS Example


~~~xml
    <ValuationRS>
        <Itineraries>
            <Itinerary id="0" HasObFees="false" carrier="SK">
                <Conditions>
                    <Condition id="PEN">
                        <Text>TICKETS ARE NON-REFUNDABLE</Text>
                    </Condition>
                    <Condition id="LTD">
                        <Text>LAST TKT DTE, 09JAN15, - SEE ADV PURCHASE</Text>
                    </Condition>
                </Conditions>
                <Journeys>
                    <Journey id="0" Duracion="0">
                        <Segments>
                            <Segment id="0">
                                <SegmentInfo id="0" transportationId="SK550" transportationType="V"
                                    operatingCarrier="SK" marketingCarrier="SK" arrivalTerminal="3"
                                    departureDate="2015-03-27T07:00:00" arrivalDate="2015-03-27T08:20:00"
                                    segmentDuration="0" maxCheckinDate="2015-01-09T00:00:00"
                                    planeType="320" segmentStatus="HK" electronicTicket="true"
                                    hasTechnicalStop="false" secureFlight="false">
                                    <OriginLoc type="A" code="AMS" cityCode="false"/>
                                    <DestinationLoc type="A" code="CPH" cityCode="false"/>
                                </SegmentInfo>
                                <SegmentClasses>
                                    <SegmentClass cabinClass="Y" class="O" paxRef="0"
                                        fareBasis="ONLOWM3" fareType="PUB"/>
                                    <SegmentClass cabinClass="Y" class="O" paxRef="1"
                                        fareBasis="ONLOWM3" fareType="PUB"/>
                                    <SegmentClass cabinClass="Y" class="O" paxRef="2"
                                        fareBasis="ONLOWM3" fareType="PUB"/>
                                    <SegmentClass cabinClass="Y" class="O" paxRef="3"
                                        fareBasis="ONLOWM3" fareType="PUB"/>
                                </SegmentClasses>
                                <ReservationTokens>
                                    <Attribute key="LtdProv" value="260215"/>
                                    <Attribute key="Ltd" value="26/02/2015"/>
                                    <Attribute key="cabinClass" value="N"/>
                                    <Attribute key="validatingCarrier" value="SK"/>
                                    <Attribute key="horaVal" value="2015-02-26T10:33:06.282"/>
                                </ReservationTokens>
                            </Segment>
                            <Segment id="1">
                                <SegmentInfo id="1" transportationId="SK2240" transportationType="V"
                                    operatingCarrier="SK" marketingCarrier="SK" departureTerminal="3"
                                    arrivalTerminal="3" departureDate="2015-03-27T10:25:00"
                                    arrivalDate="2015-03-27T14:15:00" segmentDuration="0"
                                    maxCheckinDate="2015-01-09T00:00:00" planeType="320"
                                    segmentStatus="HK" electronicTicket="true"
                                    hasTechnicalStop="false" secureFlight="false">
                                    <OriginLoc type="A" code="CPH" cityCode="false"/>
                                    <DestinationLoc type="A" code="AGP" cityCode="false"/>
                                </SegmentInfo>
                                <SegmentClasses>
                                    <SegmentClass cabinClass="Y" class="O" paxRef="0"
                                        fareBasis="ONLOWM3" fareType="PUB"/>
                                    <SegmentClass cabinClass="Y" class="O" paxRef="1"
                                        fareBasis="ONLOWM3" fareType="PUB"/>
                                    <SegmentClass cabinClass="Y" class="O" paxRef="2"
                                        fareBasis="ONLOWM3" fareType="PUB"/>
                                    <SegmentClass cabinClass="Y" class="O" paxRef="3"
                                        fareBasis="ONLOWM3" fareType="PUB"/>
                                </SegmentClasses>
                                <ReservationTokens>
                                    <Attribute key="LtdProv" value="260215"/>
                                    <Attribute key="Ltd" value="26/02/2015"/>
                                    <Attribute key="cabinClass" value="N"/>
                                    <Attribute key="validatingCarrier" value="SK"/>
                                    <Attribute key="horaVal" value="2015-02-26T10:33:06.282"/>
                                </ReservationTokens>
                            </Segment>
                        </Segments>
                    </Journey>
                </Journeys>
                <ChargeBreakdown currency="EUR" totalAmount="312.41" notCommissionableAmount="0"
                    commission="-1">
                    <ChargeBreakdowns/>
                    <PaxBreakdowns>
                        <PaxBreakdown paxType="ADT" amount="105.47" taxes="75.47" tasaDU="0"/>
                        <PaxBreakdown paxType="CHD" amount="98.47" taxes="75.47" tasaDU="0"/>
                        <PaxBreakdown paxType="INF" amount="3.00" taxes="0.00" tasaDU="0"/>
                    </PaxBreakdowns>
                </ChargeBreakdown>
                <PaxConfigurations>
                    <PaxConfiguration id="0" paxRef="0" age="30" paxType="ADT">
                        <AppliedBonuses resident="N" largeFamily="N" discountCard="N"/>
                        <PaxTypeCodes>
                            <PaxTypeCode code="IT"/>
                        </PaxTypeCodes>
                    </PaxConfiguration>
                    <PaxConfiguration id="1" paxRef="1" age="8" paxType="CHD">
                        <AppliedBonuses resident="N" largeFamily="N" discountCard="N"
                        />
                    </PaxConfiguration>
                    <PaxConfiguration id="2" paxRef="2" age="1" paxType="INF">
                        <AppliedBonuses resident="N" largeFamily="N" discountCard="N"
                        />
                    </PaxConfiguration>
                    <PaxConfiguration id="3" paxRef="3" age="70" paxType="ADT">
                        <AppliedBonuses resident="N" largeFamily="N" discountCard="N"
                        />
                    </PaxConfiguration>
                </PaxConfigurations>
            </Itinerary>
        </Itineraries>
        <Supplements>
            <PaymentMethods>
                <PaymentMethod paymentType="CreditCard" cardType="AX">
                    <PaymentCharge currency="EUR" fixAmount="9.00" minFixAmount="0"
                        appliesFixAmount="BySegment" percentage="0" minAmountPercentage="0"
                        percentageApplied="BySegment"/>
                </PaymentMethod>
                <PaymentMethod paymentType="CreditCard" cardType="VI">
                    <PaymentCharge currency="EUR" fixAmount="9.00" minFixAmount="0"
                        appliesFixAmount="BySegment" percentage="0" minAmountPercentage="0"
                        percentageApplied="BySegment"/>
                </PaymentMethod>
            </paymentMethod>
            <BaggageType>
                <BaggageType checkInType="OnLine" appliesSegments="Ida">
                    <Baggage type="bag" quantity="1" maxWeightPerUnit="0" maxTotalWeight="0"
                        paymentInAirpot="false" needToken="false">
                        <BaggageCharge currency="EUR" fixAmount="0" minFixAmount="0"
                            appliesFixAmount="ByPassenger" percentage="0" minAmountPercentage="0"
                            percentageApplied="BySegment"/>
                    </Baggage>
                </BaggageType>
                <BaggageType checkInType="OnLine" appliesSegments="Vuelta">
                    <Baggage type="bag" quantity="1" maxWeightPerUnit="0" maxTotalWeight="0"
                        paymentInAirpot="false" needToken="false">
                        <BaggageCharge currency="EUR" fixAmount="0" minFixAmount="0"
                            appliesFixAmount="ByPassenger" percentage="0" minAmountPercentage="0"
                            percentageApplied="BySegment"/>
                    </Baggage>
                </BaggageType>
                <BaggageType checkInType="OnLine" appliesSegments="Ref">
                    <References>
                        <SegmentReferences>
                            <SegmentReference itineraryRef="1" journeyRef="0" segmentRef="0"/>
                            <SegmentReference itineraryRef="1" journeyRef="0" segmentRef="1"/>
                        </SegmentReferences>
                        <PaxReferences>
                            <PaxReference paxRef="0"/>
                        </PaxReferences>
                    </References>
                    <Baggage id="D#0GO" type="bag" quantity="1" maxWeightPerUnit="0"
                        maxTotalWeight="0" paymentInAirpot="false" code="XBAG" needToken="true"
                        token="[\sA-Z0-9]{1,50}" description="23 KG BAGGAGE">
                        <BaggageCharge currency="EUR" fixAmount="50.00" minFixAmount="0"
                            appliesFixAmount="ByPassenger" percentage="0" minAmountPercentage="0"
                            percentageApplied="BySegment"/>
                    </Baggage>
                </BaggageType>
            </BaggageType>
            <Seating>
                <BlockRules>
                    <BlockRule>
                        <References>
                            <BlockReferences>
                                <BlockReference blockTypeRef="CABIN" blockRef="0"/>
                            </BlockReferences>
                            <PaxReferences>
                                <PaxReference paxRef="0"/>
                                <PaxReference paxRef="1"/>
                                <PaxReference paxRef="2"/>
                                <PaxReference paxRef="3"/>
                            </PaxReferences>
                        </References>
                        <BlockPrice>
                            <Amount currency="EUR" amount="0" amountType="FEE"/>
                        </BlockPrice>
                    </BlockRule>
                    <BlockRule>
                        <References>
                            <BlockReferences>
                                <BlockReference blockTypeRef="CABIN" blockRef="1"/>
                            </BlockReferences>
                            <PaxReferences>
                                <PaxReference paxRef="0"/>
                                <PaxReference paxRef="1"/>
                                <PaxReference paxRef="2"/>
                                <PaxReference paxRef="3"/>
                            </PaxReferences>
                        </References>
                        <BlockPrice>
                            <Amount currency="EUR" amount="0" amountType="FEE"/>
                        </BlockPrice>
                    </BlockRule>
                </BlockRules>
                <Blocks>
                    <Block type="CABIN" id="0">
                        <References>
                            <SegmentReferences>
                                <SegmentReferences itineraryRef="0" journeyRef="0"
                                    segmentRef="0"/>
                            </SegmentReferences>
                        </References>
                        <Blocks>
                            <Block type="ROW" number="1" id="0">
                                <Blocks>
                                    <Block type="SEAT" number="1A" id="0" token="1A">
                                        <Availability isAvailable="true"/>
                                        <BlockAttributes>
                                            <BlockAttribute type="WINDOW"/>
                                        </BlockAttributes>
                                    </Block>
                                    <Block type="SEAT" number="1B" id="1" token="1B">
                                        <Availability isAvailable="true"/>
                                        <BlockAttributes>
                                            <BlockAttribute type="MIDDLE"/>
                                        </BlockAttributes>
                                    </Block>
                                </Blocks>
                            </Block>
                            <Block type="ROW" number="2" id="1">
                                <Blocks>
                                    <Block type="SEAT" number="2A" id="0" token="2A">
                                        <Availability isAvailable="true"/>
                                        <BlockAttributes>
                                            <BlockAttribute type="WINDOW"/>
                                        </BlockAttributes>
                                    </Block>
                                    <Block type="SEAT" number="2B" id="1" token="2B">
                                        <Availability isAvailable="true"/>
                                        <BlockAttributes>
                                            <BlockAttribute type="MIDDLE"/>
                                        </BlockAttributes>
                                    </Block>
                                </Blocks>
                            </Block>
                        </Blocks>
                    </Block>
                </Blocks>
            </Seating>
            <specialSupplments>
                <SpecialSupplement id="A#0B5" type="Seat" quantity="1" code="SEAT" needToken="false"
                    description="PRE RESERVED SEAT ASSIGNMENT">
                    <References>
                        <SegmentReferences>
                            <SegmentReferences itineraryRef="0" journeyRef="0" segmentRef="0"/>
                            <SegmentReferences itineraryRef="0" journeyRef="0" segmentRef="1"
                            />
                        </SegmentReferences>
                        <PaxReferences>
                            <PaxReference paxRef="0"/>
                        </PaxReferences>
                    </References>
                    <CargoSuplemento currency="EUR" fixAmount="26.00" minFixAmount="0"
                        appliesFixAmount="ByPassenger" percentage="0" minAmountPercentage="0"
                        percentageApplied="BySegment"/>
                </SpecialSupplement>
            </specialSupplments>
            <Conditions>
                <Condition id="AMS-AGP-ONLOWM3-1-(5)">
                    <Paragraph title="AP.ADVANCE RES/TKT">
                        <!-- 0..n Sentences of the fare rule -->
                        <Sentence> </Sentence>
                        <Sentence> RESERVATIONS ARE REQUIRED FOR ALL SECTORS.</Sentence>
                        <Sentence> WAITLIST NOT PERMITTED.</Sentence>
                        <Sentence> TICKETING MUST BE COMPLETED WITHIN 1 DAY AFTER</Sentence>
                        <Sentence> RESERVATIONS ARE MADE OR AT LEAST 2 DAYS BEFORE DEPARTURE</Sentence>
                        <Sentence> WHICHEVER IS EARLIER.</Sentence>
                        <Sentence> OR - RESERVATIONS FOR ALL SECTORS AND TICKETING MUST BE</Sentence>
                        <Sentence> COMPLETED AT THE SAME TIME.</Sentence>
                        <Sentence> WAITLIST NOT PERMITTED.</Sentence>
                        <Sentence> NOTE -</Sentence>
                        <Sentence> WARNING-</Sentence>
                        <Sentence> ALL RESERVATIONS MADE WITHOUT TICKET NUMBER WILL</Sentence>
                        <Sentence> BE CANCELLED AUTOMATICALLY AFTER TICKETING</Sentence>
                        <Sentence> DEADLINE.</Sentence>
                    </Paragraph>
                </Condition>
                <Condition id="AGP-AMS-SHTOWMP1-1-(5)">
                    <Paragraph title="AP.ADVANCE RES/TKT">
                        <Sentence> </Sentence>
                        <Sentence> RESERVATIONS ARE REQUIRED FOR ALL SECTORS.</Sentence>
                        <Sentence> WHEN RESERVATIONS ARE MADE AT LEAST 7 DAYS BEFORE</Sentence>
                        <Sentence> DEPARTURE TICKETING MUST BE COMPLETED AT LEAST 7 DAYS</Sentence>
                        <Sentence> BEFORE DEPARTURE.</Sentence>
                        <Sentence> NOTE -</Sentence>
                        <Sentence> DIFFERENCE COULD EXIST BETWEEN THE CRS</Sentence>
                        <Sentence> LAST TICKETING DATE AND TTL ROBOT REMARK.</Sentence>
                        <Sentence> THE MOST RESTRICTIVE DATE PREVAILS.</Sentence>
                        <Sentence> OR - RESERVATIONS ARE REQUIRED FOR ALL SECTORS.</Sentence>
                        <Sentence> TICKETING MUST BE COMPLETED WITHIN 24 HOURS AFTER</Sentence>
                        <Sentence> RESERVATIONS ARE MADE.</Sentence>
                        <Sentence> NOTE -</Sentence>
                        <Sentence> DIFFERENCE COULD EXIST BETWEEN THE CRS</Sentence>
                        <Sentence> LAST TICKETING DATE AND TTL ROBOT REMARK.</Sentence>
                        <Sentence> THE MOST RESTRICTIVE DATE PREVAILS.</Sentence>
                        <Sentence> *** GENERAL RULE FOLLOWS ***</Sentence>
                        <Sentence> </Sentence>
                        <Sentence> NOTE -</Sentence>
                        <Sentence> DIFFERENCE COULD EXIST BETWEEN THE CRS</Sentence>
                        <Sentence> LAST TICKETING DATE AND TTL ROBOT REMARK.</Sentence>
                        <Sentence> THE MOST RESTRICTIVE DATE PREVAILS.</Sentence>
                    </Paragraph>
                </Condition>
            </Conditions>
        </Supplements>
    </ValuationRS> 
~~~


### ValuationRS Description



| **Element**				| **Number**	| **Type**	| **Description**							|
| ------------------------------------- | ------------- | ------------- | --------------------------------------------------------------------- |
| ValuationRS                 		| 1     	|		| Root node.|
| Itineraries                 		| 1     	|		| Contains a list of Itineraries.|
| Itineraries/Itinerary       		| 1..n    	|		| Details of the Itinerary.|
| @id                    		| 1 		| Integer	| Unique identifier of the Itinerary.|
| @fareRef	               		| 1 		| String	| Reference identifier to the original Fare.|
| @hasObFees             		| 1 		| Boolean	| If true then there is an extra fee for using credit card.|
| @carrier               		| 1 		| String	| Validating carrier.|
| Itineraries/Itinerary/Conditions	| 1 |	| Contains a list of Fare Conditions. |
| Itineraries/Itinerary/Conditions/Condition	| 1 |	| Contains details of the Condition that applies to the condition. |
| @cia	| 1	| String	| Carrier applying the condition.	|
| @code	| 1	| String	| Code of the condition.	|
| @id	| 1	| String	| Unique id of the condition.	|
| @language	| 1	| String	| Language in which the condition is written.	|
| @Text | 1	| String	| Description of the condition.	|
| Itineraries/Itinerary/Conditions/Condition/<br>Paragraph	| 1 | | List of Sentences and titles. |
| @title | 1	| String	| Title content.	|
| Itineraries/Itinerary/Conditions/Condition/<br>Paragraph/Sentence	| 1 | String	| List of Sentences contents. |
| Itineraries/Itinerary/Journeys	| 0..1    	|		| Contains a list of Journeys.|
| Itineraries/Itinerary/Journeys/Journey | 0..n    	|		| Contains details of the Journeys.|
| @id     | 1 		| Integer	| Unique identifier of the Journey in scope.|
| @duration   | 0..1 		| Integer	| Duration of the Journey in minutes. |
| @familyFare | 0..1 		| String	| Family fare name of the Journey.|
| @checkinStart   | 0..1 		| Date	| Checkin start date. |
| @checkinEnd   | 0..1 		| Date	| Checkin end date. |
| Itineraries/Itinerary/Journeys/Journey/<br>Segments | 1 |   		| Contains a list of Segments associated to the Journey.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment | 1..n   |	| Contains details of the SegmentInfo.|
| @id      | 1 		| Integer	| Unique SegmentInfo identifier.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentInfo | 1 | | Contains information of the Segment.|
| @id     | 1 		| Integer	| Unique identifier of the SegmentInfo.|
| @transportationId     | 1 		| String	| Unique Id of the transportation.|
| @transportationType    		| 1 		| String	| Transport type: V ( Flight ), T ( Train ), B ( Bus ), S() & F ( Ferry ).	|
| @transportationName    		| 1 		| String	| Name of the transportation.	|
| @transportationCode	| 1	| String	| Code of the transportation. |
| @operatingCarrier      		| 1 		| String	| Company which operates the transportation.		|
| @marketingCarrier      		| 1 		| String	| Company which commercializes the transportation.	|
| @departureTerminal     | 1 		| String	| Departure terminal.|
| @arrivalTerminal       		| 1 		| String	| Arrival terminal.|
| @departureDate         		| 1 		| Date		| Departure date.|
| @arrivalDate           		| 1 		| Date		| Arrival date. |
| @segmentDuration       		| 1 		| Integer	| Transport duration ( in minutes ).|
| @segmentStatus	| 1	| String	| Segment status: HK (Holding confirmed), TK(Confirming new flight times), UC(Unable to confirm), UN(Flight cancelled by airline), NO (No action taken), UD (Undefined). |
| @planeType | 1 		| String	| Plane type. Flights parameter.|
| @maxCheckinDate     | 1 		| String	| Maximum date to make the check-in.|
| @hasTechnicalStop   | 1 | Boolean	| If true, the segment has a technical stop. 		|
| @electronicTicket      		| 1 		| Boolean	| If true, the segment uses a electronic ticket. 	| 
| @secureFlight          		| 0..1		| Boolean	| If true, the provider requires extra information of the passengers. Flights parameter.	|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/OriginLoc | 1     	|		| Origin location.					|
| @type                  		| 1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).	|
| @code                  		| 1 		| String	| Location code.					|
| @name	| 1 		| String	| Location full name.	|
| @radius					| 0..1			| Integer	| Area radius from location.|
| @cityCode              		| 1 		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.	|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/OriginLoc/<br>AlternativeLocations	| 0..1		|	| Contains a list of AlternativeLocations.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/OriginLoc/<br>AlternativeLocations/AlternativeLocation	| 0..n	|	| Contains the information of the alternative location.|
| @code						| 1			| String	| Location code.|
| @cityCode        			| 1  		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.|
| @name						| 0..1			| String	| Location long name.|
| @type						| 0..1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/DestinationLoc | 1   |  		| Destination location.					|
| @type  | 1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).	|
| @code                  		| 1 		| String	| Location code. 					|
| @name	| 1 		| String	| Location full name.	|
| @radius					| 0..1			| Integer	| Area radius from location.|
| @cityCode              		| 1 		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.	||
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/DestinationLoc/<br>AlternativeLocations	| 0..1		|	| Contains a list of AlternativeLocations.
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/DestinationLoc/<br>AlternativeLocations/AlternativeLocation	| 0..n	|	| Contains the information of the alternative location.|
| @code						| 1			| String	| Location code.|
| @cityCode        			| 1  		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.|
| @name						| 0..1			| String	| Location long name.|
| @type						| 0..1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/TechnicalStops | 0..1 |   		| Contains a list of TechnicalStops.		|
| @totalTechnicalStops   | 1 		| Integer	| Total number of TechnicalStops.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/TechnicalStops/<br>TechnicalStop | 1..n | | Contains the details of the TechnicalStop.|
| @location          | 1 		| String	| TechnicalStop location.|
| @stopDate       | 1 		| Date		| Approx. stop date and time.|
| @departureDate    | 1 		| Date		| Approx. departure date and time.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses | 0..1 |  | Contains a list of SegmentClasses.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses | 1 | | Contains a list of SegmentClasses.	|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses/<br>SegmentClass | 1..n | | Contains details of the SegmentClass.   |
| @cabinClass            		| 1 		| String	| Cabin class of the seat: N (Not specified), Y (Tourist), C (Business), F (First), CA (Cabin, only for ferries), YP (Tourist Plus).	|
| @class                 		| 1 		| String	| Fare class. |
| @paxRef               	 	| 1 		| Integer	| Passenger reference. 					|
| @fareBasis             		| 1 		| String	| Identifier of the fare.				|
| @fareType              		| 1 		| String	| Fare type: PUB ( Public ), PRI ( Private ), NEGO ( Negotiated ) and CORP ( Corporate ).	|
| @avail                 		| 1 		| Integer	| Available seats remaining for this class (In flights, the maximum is 9).  |
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses/<br>SegmentClass/Modifiable | 0..1 |  | Contains the information of the modifiable fare.	|
| @Description                 		| 1 		| String	| Modification description. |
| @amount                 			| 1 		| Decimal	| Modification amount. |
| @modifiable                 		| 1 		| Boolean	| If true, the fare allows this modification. |
| @currency                 		| 1 		| String	| Modification currency. |
| @amountType                 		| 1 		| String	| Modification amount type: AMOUNT (Fare amount), FEE (Fee amount), TOTAL (Total fare amount), PERCENTUAL (Percentual amount). |
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses/<br>SegmentClass/CancellationPolicies | 0..1 |  | Contains a list of CancellationPolicies.	|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses/<br>SegmentClass/CancellationPolicies/<br>CancellationPolicy | 1..n |  |Contains details of the CancelationPolicy.	|
| @fromDate                 		| 1 		| Date	| Date of the begining of the policy. |
| @amount                 			| 1 		| Decimal	| Policy amount. |
| @refundable                 		| 1 		| Boolean	| If true, the fare allows the refundation. |
| @currency                 		| 1 		| String	| Policy currency. |
| @amountType                 		| 1 		| String	| Policy amount type: AMOUNT (Fare amount), FEE (Fee amount), TOTAL (Total fare amount), PERCENTUAL (Percentual amount).|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/ReservationTokens | 0..1 |  | Specific attribute used for each provider.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/ReservationTokens/<br>Attribute | 0..n |  | Type of attribute.|
| @key   | 1 		| String	| Contains the keyword/ Id to identify a parameter.	|
| @value     | 1 		| String	| Contains the value of the parameter.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/CheckinInformation | 0..1 |  | Checkin information.|
| @openingTime | 1 		| Date	| Checkin opening time.|
| @closingTime | 1 		| Date	| Checkin closing time.|
| @estimatedCheckinTime | 1 		| Date	| Estimated checkin time.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/CheckinInformation/<br>Status | 1 |  | Status checkin information.|
| @isAvailable | 1 		| Boolean	| If true, the cheking is available.|
| @direction | 1 		| String	| Direction of the journey about to checkin: DEPARTURE (Outbound), RETURN (Inbound), IDA_VUELTA (Outbound and Inbound).|
| @status | 1 		| String	| Status of the checkin: UNDEFINED, IN_PROGRESS, ERROR, COMPLETE, UNCONFIRMED.|
| Itineraries/Itinerary/AmountBreakdown  		| 1     	|		| Breakdown of the fare amount.|
| @currency  | 1 		| String	| Currency code of the fare.|
| @totalAmount           		| 1 		| Decimal	| Total amount. with taxes and other charges included.|
| @notCommissionableAmount		| 1 		| Decimal	| Total amount that can not be commissioned.  		|
| @commission            		| 1 		| Decimal	| Commission. 						|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakdowns | 0..1   |		| Contains a list of breakdown amounts ( taxes, mandatory charges.. ).	|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakdowns/ChargeBreakdown | 1..n |	| Contains details of the BreakdownAmount.	|
| @type                  		| 1 		| String	| [Type of charge.](#valuation-enumerate-description) |
| @amount                		| 1    	 	| Decimal	| Charge amount.				|
| @included				| 1		| Boolean	| If true, the charge is included to the total fare amount |
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakdowns/ChargeBreakdown<br>/Concept | 0..1 | | Contains details of the charge.|
| @id                    		| 1 		| String	| Unique id of the Concept	|
| @language              		| 1 		| String	| Language.			|
| @cia              		| 1 		| String	| Carrier.			|
| @code              		| 1 		| String	| Concept code.			|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakDowns/ChargeBreakdown<br>/Concept/Text | 1 | String | Remarks.	|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakDowns/ChargeBreakdown<br>/Concept/Paragraph | 1 |  | Contains a list of Sentences and titles.	|
| @title	| 1	| String	| Title.	|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakDowns/ChargeBreakdown/<br>Concept/Paragraph/Sentence | 1 | String | Sentence|
| Itineraries/Itinerary/AmountBreakdown/<br>PaxBreakdown | 0..1    	|		| Contains a list of breakdown amounts for each passenger ( ADT amount, etc. ).|
| Itineraries/Itinerary/AmountBreakdown/<br>PaxBreakdowns/PaxBreakdown | 0..n | 	| Contains details of breakdown amounts for each passenger.|
| @paxType               		| 1 		| String	| Passenger type: ADT ( Adult ), CHD ( Child ) & INF ( Infant ).|
| @amount                		| 1 		| Decimal	| Total amount, with taxes included, associated to the passenger.	|
| @taxes                 		| 1 		| Decimal	| If they exist, taxes are applied for this passenger type. |
| @tasaDU                		| 1 		| Decimal	| DU taxes. 						|
| @fees                			| 1 		| Decimal	| Fees. 						|
| Itineraries/Itinerary/AmountBreakdown/<br>PaxBreakdowns/PaxBreakdown/<br>Taxes | 0..1 | 	| Contains a list of Taxes.|
| Itineraries/Itinerary/AmountBreakdown/<br>PaxBreakdowns/PaxBreakdown/<br>Taxes/Tax | 0..n | 	| Code and amount of each tax.|
| @code				| 1	| String	| Code.	|
| @amount				| 1	| Decimal	| Amount.	|
| Itineraries/Itinerary/PaxConfigurations		| 1     	|		| Contains a list of PaxConfiguration.	|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration | 1..n |   		| Contains details of PaxConfiguration.	|
| @id                    		| 1 		| Integer	| Unique identifier of the PaxConfiguration. 		|
| @paxRef                		| 1 		| Integer	| Reference to the passenger Id from the request. 	|
| @age                   		| 1 		| Integer	| Age of the passenger. 				|
| @nacionality                   	| 1 		| String	| Nacionality of the passenger. 			|
| @paxType               		| 1 		| String	| Passenger type based on the age of the passenger: ADT (Adult), CHD (Child), INF (Infant), YOU (Young) and SEN (Senior).	|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses | 0..1 | | Applied discounts.			|
| @resident              	| 1 		| String	| [Resident discount type.](#valuation-enumerate-description)|
| @largeFamily           		| 1 		| String	| Family discount type: N(None), F1(Large family), F2 (Special large family). |
| @discountCardCode		| 0..1	| String	| Discount card code.|
| @discountCard		| 0..1	| String	| [Discount card type.](#valuation-enumerate-description)|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses/<br>DiscountCards	| 0..1	|	| Contains a list of DiscountCards.|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses/<br>DiscountCards/DiscountCard|
| @code	| 1	| String | Discount card code.|
| @id	| 1	| String	| Unique identifier of discound card.|
| @type	| 1	| String	| [Discount card type.](#valuation-enumerate-description)|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses/<br>PaxTypeCodes		| 0..1	|		| Contains a list of PaxTypeCodes.|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses/<br>PaxTypeCodes/PaxTypeCode	| 0..n	|	| Contains the code type of the passenger.|
| @code		| 1		| String	| Code type of the passenger.|
| Itineraries/Itinerary/Emissions	| 0..1	|	| Contains a list of Issuances.|
| Itineraries/Itinerary/Emissions/<br>Emission	| 0..n	|	| Contains the key of the Issuance.|
| @key		| 1		| String	| Key of the Issuance.|
| OptionalCharges	| 0..1	|	| Deprecated.|
| BaggageCharges | 0..1	|	| Deprecated.|


### ValuationSupplements

This option is only shown when requested in Preferences node. The
functionality is the same has SupplementsRQ.



| **Element**				| **Number**	| **Type**	| **Description**					|
| ------------------------------------- | ------------- | ------------- | ----------------------------------------------------- |
| Supplements        | 1      	|		| Supplements node in ValuationRS.|
| PaymentMethods                 	| 0..1    	|		| Contains a list of paymentMethods.   			|
| PaymentMethods/PaymentMethod 		| 1..n    	|	| Contains paymentMethod details.|
| @paymentType            		| 1  		| String	| Payment Type: CreditCard, ElectronicBanking.|
| @cardType               		| 1  		| String	| Card type with a provider format.|
| PaymentMethods/PaymentMethod/<br>PaymentCharges | 0..1      	|		| Contains a list of Payment Charges.|
| PaymentMethods/PaymentMethod/<br>PaymentCharges/PaymentCharge | 1..n      	|		| Charge applied to the Booking when this paymed method is used.|
| @fixAmount             		| 1 		| Decimal| Total fixed amount.|
| @appliesFixAmount             		| 1 		| String| The fixed amount applies to: PorReserva(Reservation), PorPasajero(Passenger), PorSegmento(Segment), TarifaBase(Base Fare), Tasas(Taxes), ForAdt(Adult passengers), ForChd(Children passengers), ForInf(Infant passengers).|
| @minFixAmount             		| 1 		| Decimal| Minimal fixed amount.|
| @maxFixAmount             		| 1 		| Decimal| Maximal fixed amount.|
| @minAmountPercentage             		| 1 		| Decimal| Minimal percentage amount.|
| @maxAmountPercentage             		| 1 		| Decimal| Maximal percentage amount.|
| @currency             		| 1 		| String| Currency.|
| @percentage             		| 1 		| Decimal| Total percentage amount.|
| @percentageApplied             		| 1 		| String| The percentage amount applies to: PorReserva(Reservation), PorPasajero(Passenger), PorSegmento(Segment), TarifaBase(Base Fare), Tasas(Taxes), ForAdt(Adult passengers), ForChd(Children passengers), ForInf(Infant passengers).|
| BaggageTypes                 		| 0..1    	|		| Contains a list of Baggage information.|
| BaggageTypes/BaggageType     | 1..n    	|		| Baggage information.|
| @checkInType        | 1  		| String	| Check-in type: OnLine & Airport.|
| @appliesSegments        		| 1  		| String	| Segments in which is applied: All, Departure, Return, Ref (only the segment references indicated in the node SegmentReferences).|
| BaggageTypes/BaggageType/<br>References		| 0..1	|	|	References for the Baggage Type.|
| BaggageTypes/BaggageType/<br>References/SegmentReferences		| 0..1	|	|	Contains a list of segment references for the Baggage Type.|
| BaggageTypes/BaggageType/<br>References/SegmentReferences/<br>SegmentReference		| 1..n	|	|	Segment reference.|
| @itineraryRef | 1 		| Integer| Unique identifier of the Itinerary.|
| @journeyRef | 1 		| Integer| Unique identifier of the Journey.|
| @segmentRef | 1 		| Integer| Unique identifier of the Segment.|
| BaggageTypes/BaggageType/<br>References/PaxReferences		| 0..1	|	|	Contains a list of passenger references for the Baggage Type.|
| BaggageTypes/BaggageType/<br>References/PaxReferences/<br>PaxReference		| 1..n	|	|	Passenger reference.|
| @paxRef | 1 		| String| Reference to the passenger.|
| BaggageTypes/BaggageType/Baggage | 1..n |    | Details of the baggage. 		|
| @id                    		| 1 		| String	| Unique identifier of the Baggage.			|
| @type                  		| 1 		| String	| Type of baggage: Bag, Bike, Wheelchair, Skis, BabyTrolley and HandBaggage.|
| @quantity              		| 1 		| Integer	| Baggage quantity.|
| @maxWeightPerUnit      | 1 		| Integer	| Maximum weight of the baggage.| 
| @maxTotalWeight        		| 1 		| Integer	| Maximum weight of ALL the baggage.|
| @paymentInAirpot       		| 1 		| Boolean	| Determines whether the pay is in station.|
| @code     | 1 		| String	| Code of the Baggage.|
| @carrier               		| 1 		| String	| Carrier.|
| @needToken     | 1 		| Boolean	| Reserve token mandatory.|
| @reservationToken             		| 1 		| String| Reserve token.|
| @description             		| 1 		| String| Baggage description.|
| BaggageTypes/BaggageType/Baggage/<br>BaggageCharge | 1 |    | Details of the baggage charge.|
| @fixAmount             		| 1 		| Decimal| Total fixed amount.|
| @appliesFixAmount             		| 1 		| String| The fixed amount applies to: PorReserva(Reservation), PorPasajero(Passenger), PorSegmento(Segment), TarifaBase(Base Fare), Tasas(Taxes), ForAdt(Adult passengers), ForChd(Children passengers), ForInf(Infant passengers).|
| @minFixAmount             		| 1 		| Decimal| Minimal fixed amount.|
| @maxFixAmount             		| 1 		| Decimal| Maximal fixed amount.|
| @minAmountPercentage             		| 1 		| Decimal| Minimal percentage amount.|
| @maxAmountPercentage             		| 1 		| Decimal| Maximal percentage amount.|
| @currency             		| 1 		| String| Currency.|
| @percentage             		| 1 		| Decimal| Total percentage amount.|
| @percentageApplied             		| 1 		| String| The percentage amount applies to: PorReserva(Reservation), PorPasajero(Passenger), PorSegmento(Segment), TarifaBase(Base Fare), Tasas(Taxes), ForAdt(Adult passengers), ForChd(Children passengers), ForInf(Infant passengers).|
| SpecialSupplements	| 0..1	|	|	Contains a list of SpecialSupplements.
| SpecialSupplements/SpecialSupplement		| 0..n	|	|	Contains information about the Special Supplement	|
| @id	| 1	| String	| Unique identifier of the supplement.|
| @code	| 1	| String	| Supplement code.|
| @height	| 0..1	| Integer	| Dimension of the supplement: height.|
| @width	| 0..1	| Integer	| Dimension of the supplement: width.|
| @length	| 0..1	| Integer	| Dimension of the supplement: length.|
| @weight	| 0..1	| Integer	| Dimension of the supplement: weight.|
| @quantity	| 0..1	| Integer	| Quantity of supplements.|
| @description	| 0..1	| String	| Description of the supplement|
| @carrier	| 1	| String	| Carrier selling the supplement.|
| @estado	| 0..1	| String	| Status of the supplement: N(None), INC(Included in the price), CHA(Avalilable with charges), NOF(Not offered).|
| @needToken	| 1	| Boolean	| If true, the field @reservationToken should be filled|
| @type	| 1	| String	| Type of supplement: Miscelaneous, Seat, Meal, Pet, Lounge, Baggage, Canoe, PreferentialBoarding, Bike, Trailer, Seguro, Embarque_Prioritario, Acceso_Preferente, Bloqueo_Tarifa, Special_Assistance.|
| @reservationToken	| 0..1	| String	| Reservation Token of the supplement.|
| @ownTransportation	| 0..1	| Boolean	| If true, the supplement includes own transportation cage.|
| SpecialSupplements/SpecialSupplement/<br>References		| 0..1	|	|	References for the Special Supplement.|
| SpecialSupplements/SpecialSupplement/<br>References/SegmentReferences		| 0..1	|	|	Contains a list of segment references for the Special Supplement.|
| SpecialSupplements/SpecialSupplement/<br>References/SegmentReferences/<br>SegmentReference		| 1..n	|	|	Segment reference.|
| @itineraryRef | 1 		| Integer| Unique identifier of the Itinerary.|
| @journeyRef | 1 		| Integer| Unique identifier of the Journey.|
| @segmentRef | 1 		| Integer| Unique identifier of the Segment.|
| SpecialSupplements/SpecialSupplement/<br>References/PaxReferences		| 0..1	|	|	Contains a list of passenger references for the Special Supplement.|
| SpecialSupplements/SpecialSupplement/<br>References/PaxReferences/PaxReference		| 1..n	|	|	Passenger reference.|
| @paxRef | 1 		| String| Reference to the passenger.|
| SpecialSupplements/SpecialSupplement/<br>SupplementCharge		| 0..1	|	|	Details of the special supplement charge.|
| @fixAmount             		| 1 		| Decimal| Total fixed amount.|
| @appliesFixAmount             | 1 		| String| The fixed amount applies to: PorReserva(Reservation), PorPasajero(Passenger), PorSegmento(Segment), TarifaBase(Base Fare), Tasas(Taxes), ForAdt(Adult passengers), ForChd(Children passengers), ForInf(Infant passengers).|
| @minFixAmount             		| 1 		| Decimal| Minimal fixed amount.|
| @maxFixAmount             		| 1 		| Decimal| Maximal fixed amount.|
| @minAmountPercentage             		| 1 		| Decimal| Minimal percentage amount.|
| @maxAmountPercentage             		| 1 		| Decimal| Maximal percentage amount.|
| @currency             		| 1 		| String| Currency.|
| @percentage             		| 1 		| Decimal| Total percentage amount.|
| @percentageApplied             		| 1 		| String| The percentage amount applies to: PorReserva(Reservation), PorPasajero(Passenger), PorSegmento(Segment), TarifaBase(Base Fare), Tasas(Taxes), ForAdt(Adult passengers), ForChd(Children passengers), ForInf(Infant passengers).|
| Seating        | 0..1    	|		| Seating availability.|
| Seating/BlockRules    | 0..1    	|		| Contains a list of Block Rules.|
| Seating/BlockRules/BlockRule 		| 0..n    	|		| Block Rules.|
| Seating/BlockRules/BlockRule/References | 0..1    	|		| References for the Block Rule.|
| Seating/BlockRules/BlockRule/References/<br>BlockReferences		| 0..1	|	|	Contains a list of references to block elements.|
| Seating/BlockRules/BlockRule/References/<br>BlockReferences/BlockReference | 0..n |   | Block element reference.			|
| @blockTypeRef     | 1  		| String	| Block type: CABIN (The entire cabin of the plane).|
| @blockRef      | 1  		| Integer	| Block reference.|
| Seating/BlockRules/BlockRule/References/<br>SegmentReferences		| 0..1	|	|	Contains a list of segment references for the Block Rule.|
| Seating/BlockRules/BlockRule/References/<br>SegmentReferences/SegmentReference		| 1..n	|	|	Segment reference.|
| @itineraryRef | 1 		| Integer| Unique identifier of the Itinerary.|
| @journeyRef | 1 		| Integer| Unique identifier of the Journey.|
| @segmentRef | 1 		| Integer| Unique identifier of the Segment.|
| Seating/BlockRules/BlockRule/References/<br>PaxReferences		| 0..1	|	|	Contains a list of passenger references for the Special Supplement.|
| Seating/BlockRules/BlockRule/References/<br>PaxReferences/PaxReference		| 1..n	|	|	Passenger reference.|
| @paxRef | 1 		| String| Reference to the passenger.|
| Seating/BlockRules/BlockRule/BlockPrice | 0..1  	|  		| Price element.|
| Seating/BlockRules/BlockRule/BlockPrice/<br>Amount | 1  	|    | Amount by type.|
| @currency    | 1  		| String	| Currency code of the amount.				|
| @amount                 		| 1  		| Decimal	| Amount.						|
| @amountType             		| 1  		| String	| Amount type: AMOUNT (Amount), FEE (Service Fee), TOTAL (Total), PERCENTUAL (Percentual).|
| Seating/Blocks     | 0..1    	|		| Contains a list of seating blocks.|
| Seating/Blocks/Block    | 0..n    	|		| Seating details.|
| @type   | 1  		| String	| Block type: CABIN (The entire cabin of the plane).|
| @id     | 1  		| Integer	| Unique id.|
| Seating/Blocks/Block/References/<br>SegmentReferences		| 0..1	|	|	Contains a list of segment references for the Block.|
| Seating/Blocks/Block/References/<br>SegmentReferences/SegmentReference		| 1..n	|	|	Segment reference.|
| @itineraryRef | 1 		| Integer| Unique identifier of the Itinerary.|
| @journeyRef | 1 		| Integer| Unique identifier of the Journey.|
| @segmentRef | 1 		| Integer| Unique identifier of the Segment.|
| Seating/Blocks/Block/Blocks | 1    	|		| Contains a list of row blocks.|
| Seating/Blocks/Block/Blocks/Block 	| 0..n    	|		| Row block.|
| @type    	| 1  		| String	| Block type: ROW|
| @id     	| 1  		| Integer	| Unique row id.|
| @number   | 1  		| Integer	| Row number in the cabin.|
| Seating/Blocks/Block/Blocks/Block/<br>Blocks | 1    	|		| Contains a list of seat blocks.|
| Seating/Blocks/Block/Blocks/Block/<br>Blocks/Block | 0..n  |   	| Seat block.|
| @type      | 1  		| String	| Block type: SEAT.						|
| @id       | 1  		| Integer	| Unique seat id. 						|
| @number    	| 1  		| String	| Seat identifier.					|
| @token    	| 1  		| String	| Reservation seat token.					|
| Seating/Blocks/Block/Blocks/Block/<br>Blocks/Block/Availability | 0..1 |  | Availability of the seat.|
| @isAvailable  | 1  		| String	| Indicates whether the seat is available.|
| Seating/Blocks/Block/Blocks/Block/<br>Blocks/Block/BlockAttributes | 0..1 |   | Contains a list of Seat attributes.|
| Seating/Blocks/Block/Blocks/Block/<br>Blocks/Block/BlockAttributes/<br>BlockAttribute | 0..n |  | Seat attribute.|
| @type                   		| 1  		| String	| [Seat type.](#valuation-enumerate-description)|
| Conditions	| 0..1 |	| Contains a list of applied fare conditions.|
| Conditions/Condition	| 1 |	| Details of the condition. |
| @cia	| 1	| String	| Carrier applying the condition.	|
| @code	| 1	| String	| Code of the condition.	|
| @id	| 1	| String	| Unique id of the condition.	|
| @language	| 1	| String	| Language in which the condition is written.	|
| @Text | 1	| String	| Description of the condition.	|
| Conditions/Condition/Paragraph	| 1 | | List of Sentences and titles. |
| @title | 1	| String	| Title content.	|
| Conditions/Condition/Paragraph/Sentence	| 1 | String	| List of Sentences contents. |
| SummarizedConditions | 0..1 |	| Summarized applied fare conditions.|
| SummarizedConditions/FareRuleTypes | 0..1 |	| Contains a list of fare rules.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType | 1..n |	| Fare rule details.|
| @id	| 1	| String	| Unique id of the fare rule.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/TicketingRules | 0..1 |	| Ticketing rules details.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/TicketingRules/<br>DatesTypes | 0..n |	| Contains a list of Date type elements.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/TicketingRules/<br>DatesTypes/DatesType | 0..n |	| Date details.|
| @type	| 1	| String	| Date type.|
| @date	| 1	| Date	| Ticketing date.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/MinimumStayRules | 0..1 |	| Minimum stay rules details.|
| @location | 1	| String	| Location concerning the minimum stay.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/MinimumStayRules/<br>DatesTypes | 0..n |	| Contains a list of Date type elements.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/MinimumStayRules/<br>DatesTypes/DatesType | 0..n |	| Date details.|
| @type	| 1	| String	| Date type.|
| @date	| 1	| Date	| Date.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/MaximumStayRules | 0..1 |	| Maximum stay rules details.|
| @location | 1	| String	| Location concerning the maximum stay.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/MaximumStayRules/<br>DatesTypes | 0..n |	| Contains a list of Date type elements.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/MaximumStayRules/<br>DatesTypes/DatesType | 0..n |	| Date details.|
| @type	| 1	| String	| Date type.|
| @date	| 1	| Date	| Date.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/Penalty | 0..1 |	| Penaly rules details.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/Penalty/<br>DatesTypes | 0..n |	| Contains a list of Date type elements.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/Penalty/<br>DatesTypes/DatesType | 0..n |	| Date details.|
| @type	| 1	| String	| Date type.|
| @date	| 1	| Date	| Date.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/Penalty/AmountTypes | 0..n |	| Contains a list of amount types.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/Penalty/AmountTypes/<br>AmountType | 0..n |	| Amount details.|
| @type	| 1	| String	| Date type.|
| @date	| 1	| Date	| Date.|
| @currency | 1	| String	| Date type.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/Penalty/RestrictionTypes | 0..n |	| Contains a list of restriction types.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/Penalty/RestrictionTypes/<br>RestrictionType | 0..n |	| Restriction details.|
| @type	| 1	| String	| Restriction type.|
| @application | 1	| Boolean | If true, the restriction applies to the fare.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/ReissueRules | 0..1 |	| Reissue rules details.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/ReissueRules/<br>DatesTypes | 0..n |	| Contains a list of Date type elements.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/ReissueRules/<br>DatesTypes/DatesType | 0..n |	| Date details.|
| @type	| 1	| String	| Date type.|
| @date	| 1	| Date	| Date.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/ReissueRules/AmountTypes | 0..n |	| Contains a list of amount types.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/ReissueRules/AmountTypes/<br>AmountType | 0..n |	| Amount details.|
| @type	| 1	| String	| Date type.|
| @date	| 1	| Date	| Date.|
| @currency | 1	| String	| Date type.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/ReissueRules/RestrictionTypes | 0..n |	| Contains a list of restriction types.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/ReissueRules/RestrictionTypes/<br>RestrictionType | 0..n |	| Restriction details.|
| @type	| 1	| String	| Restriction type.|
| @application | 1	| Boolean | If true, the restriction applies to the fare.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/RefundRules| 0..1 |	| Refund rules details.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/RefundRules/<br>DatesTypes | 0..n |	| Contains a list of Date type elements.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/RefundRules/<br>DatesTypes/DatesType | 0..n |	| Date details.|
| @type	| 1	| String	| Date type.|
| @date	| 1	| Date	| Date.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/RefundRules/AmountTypes | 0..n |	| Contains a list of amount types.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/RefundRules/AmountTypes/<br>AmountType | 0..n |	| Amount details.|
| @type	| 1	| String	| Date type.|
| @date	| 1	| Date	| Date.|
| @currency | 1	| String	| Date type.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/RefundRules/RestrictionTypes | 0..n |	| Contains a list of restriction types.|
| SummarizedConditions/FareRuleTypes/<br>FareRuleType/RefundRules/RestrictionTypes/<br>RestrictionType | 0..n |	| Restriction details.|
| @type	| 1	| String	| Restriction type.|
| @application | 1	| Boolean | If true, the restriction applies to the fare.|
| SummarizedConditions/FareRuleApplicabilities | 0..1 |	| Contains a list of fare rules aplicability.|
| SummarizedConditions/FareRuleApplicabilities/<br>FareRulesApplicability | 1..n |	| Contains a list of fare rules aplicability.|
| SummarizedConditions/FareRuleApplicabilities/<br>FareRulesApplicability/OriginDestinationIds | 0..1 |	| Contains a list of Origin Destination identificators.|
| SummarizedConditions/FareRuleApplicabilities/<br>FareRulesApplicability/OriginDestinationIds/<br>OriginDestinationId | 1..n |	| List of Origin and Destinations pairs involved in the fare rule.|
| @origin| 1	| String	| Origin.|
| @destination	| 1	| String	| Destination.|
| SummarizedConditions/FareRuleApplicabilities/<br>FareRulesApplicability/PaxReferences | 0..1 |	| Contains a list of pasengers involved in the fare rules.|
| SummarizedConditions/FareRuleApplicabilities/<br>FareRulesApplicability/PaxReferences/<br>PaxReference| 1..n |	| List of references to pasengers related to the fare rule.|
| @paxRef| 1	| String	| Reference to a specific pasenger.|
| SummarizedConditions/FareRuleApplicabilities/<br>FareRulesApplicability/FareRulesReferences | 0..1 |	| Contains a list of fare rules. |
| SummarizedConditions/FareRuleApplicabilities/<br>FareRulesApplicability/FareRulesReferences/<br>FareRulesReference| 1..n |	| List of references to fare rules.|
| @FareRulesRefType | 1	| String	| Reference to a fare rule.|
| Installments | 0..1 |	| Contains a list of Installments. |
| Installments/Installment | 1..n |	| Installment details. |
| @number | 1	| Integer | Number of installments.|
| @currency | 1	| String	| Currency.|
| Installments/Installment/PaymentCharge | 0..1 |	| First installment amount. |
| Installments/Installment/InterestRate | 0..1 |	| Interest rate. |
| Installments/Installment/<br>RemainingInstallmentAmount | 0..1 |	| Remaining installment amount. |
| Installments/Installment/<br>RemainingInstallmentTotalAmount | 0..1 |	| Remaining installment total amount. |


### Valuation Enumerate description

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
| Fares/Fare/AmountBreakdown<br>/ChargeBreakdowns/ChargeBreakdown/<br>@type				| TASA  | Tax  |
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
| BlockAttribute/@type		| OVER_WING | Over wing seat|
| 							| MIDDLE  | Middle seat |
| 							| AISLE  | Aisle seat  |
| 							| WINDOW  | Window seat  |
| 							| COMPARTMENT  | Compartment |
| 							| LAVATORY | Lavatory |
| 							| LUGGAGE | Luggage seat |
| 							| PHONE | Phone seat |
| 							| POWER | Power |
| 							| TABLE | Table |
| 							| EXITROW | Emergency exit |
| 							| FEETBLOCKED | Feet blocked seat |
| 							| NO_CHILD | No childs allowed seat |
| 							| NO_INFANT | No infants allowed seat |
| 							| XL_SEAT | XL seat |
| 							| RESTRICTED | Seat with some kind of restriction |
| 							| HANDICAP | Special seat for handicap people |
| 							| QUIET | Quiet seat |
| 							| GROUPS | Groups seat |
| 							| NO_PET | No pets allowed seat |
| 							| BULKHEAD | Bulk head seat |
| 							| BLOCKED | Blocked seat |
| 							| UNKNOWN | Unknown characterstic |
| 							| LAST_OFF | Last off |