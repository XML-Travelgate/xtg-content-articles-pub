---
title: Avail
keywords: transportation, data structure, flights, avail
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
indication of the trip type: one way trip or a round trip.



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

The maximum time that our systems permits before closing the connexion
is of **25000** milliseconds.



### AvailabilityRQ Example


~~~xml
    <AvailabilityRQ travelType = "RT">
        <timeoutMilliseconds>999900</timeoutMilliseconds>
        <source>
            <agencyCode>logitravel</agencyCode>
            <languageCode>es</languageCode>
        </source>
        <filterAuditData/>
        <Configuration>
            <Credentials user="XXX"/>
            <Attributes>
                <Attribute key="test" value="true"/>
                <Attribute key="AgencyName" value="XXX"/>
            </Attributes>
        </Configuration>
        <ClientConfiguration currencyCode="EUR"/>
        <Journeys>
            <Journey id = "0" departureDate = "23/03/2014" departureTime = "">
                <OriginLoc code = "XXX" cityCode = "false"/>
                <DestinationLoc code = "YYY" cityCode = "false"/>
            </Journey>
            <Journey id = "1" departureDate = "25/03/2014" departureTime = "">
                <OriginLoc code = "XXX" cityCode = "false"/>
                <DestinationLoc code = "YYY" cityCode = "false"/>
            </Journey>
        </Journeys>
        <Passengers>
            <Passenger id = "0" age = "30">
                <Bonuses resident = "N" largeFamily = "N"/>
            </Passenger>
        </Passengers>        
        <Preferences cabinClass="N">
            <ConnexionCompanies>
                <ConnexionCompany carrier="IB" mode="INCLUDED" />
            </ConnexionCompanies>
        </Preferences>
    </AvailabilityRQ> 
~~~


### AvailabilityRQ Description


| **Element**				| **Number**	| **Type**	| **Description**						|
| ------------------------------------- | ------------- | ------------- | ------------------------------------------------------------- |
| AvailabilityRQ        		| 1      	|		| Root node.							|
| @travelType      			| 1  		| String	| Indicates the travel type: one way (OW), round trip (RT), open jaw (OJ) and circle trip.	|
| Journeys              		| 1      	|		| Contains a list of Journeys.					|
| Journeys/Journey      		| 1..n    	|		| Contains the information about the requested Journey in the availability. |
| @id              			| 1  		| Integer	| Unique identifier of the Journey.				|
| @departureDate   			| 1  		| String	| Departure date.						|
| @departureTime   			| 1  		| String	| Departure time. 						|
| Journeys/Journey/OriginLoc		| 1      	|		| Origin location.						|
| @code            			| 1  		| String	| Location code.						|
| @cityCode        			| 1  		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.	|
| Journeys/Journey/DestinationLoc	| 1      	|		| Destination location.						|
| @code            			| 1  		| String	| Location code.						|
| @cityCode        			| 1  		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.	|
| Passengers            		| 1      	|		| Contains a list of Passengers.				|
| Passengers/Passenger  		| 1..n    	|		| Contains information of the Passenger. 			|
| @id              			| 1  		| Integer	| Unique identifier of the Passenger.				|
| @age             			| 1  		| Integer	| Age of the Passenger.						|
| Passengers/Passenger/Bonuses		| 0..1    	|		| Possible discount or bonuses.					|
| @resident        			| 1  		| String	| Resident discount.						|
| @largeFamily     			| 1  		| String	| Family discount.						|
| Preferences           		| 1      	|		| Availability Preferences.					|
| @cabinClass      			| 1  		| String	| Preferred cabin class. N don't aply (default), F first, C Business, Y Economy. 	|
| ConnexionCompanies    		| 1      	|		| List of preferred companies.					|
| ConnexionCompany      		| 1      	|		| Preferred company.						|
| @carrier         			| 1  		| String	| Airline code.							|
| @mode            			| 1  		| String	| Mode. INCLUDED include preferred company and exclude all the others. EXCLUDED exclude only preferred company.	|



### AvailabilityRS Example


~~~xml
    <AvailabilityRS>
        <Transportation>
            <Segments>
                <Segment  id = "0" transportationId = "0B104" transportationType = "A" operatingCarrier = "0B" marketingCarrier = "0B" departureTerminal = "T1" arrivalTerminal = "T2" departureDate = "2014-03-23T10:20:00" arrivalDate = "2014-03-23T15:15:00" segmentDuration = "0" planeType = "734" segmentStatus = "HK" hasTechnicalStop = "false">
                    <OriginLoc type = "A" code = "MAD" cityCode = "false"/>
                    <DestinationLoc type = "A" code = "OTP" cityCode = "false"/>
                    <TechnicalStops totalTechnicalStops="1">
                        <TechnicalStop location="BCN" stopDate="2014-10-21T08:20:00" departureDate="2014-10-21T08:30:00"/>
                    </TechnicalStops>
                </Segment>
                <Segment id = "1" transportationId = "0B103" transportationType = "A" operatingCarrier = "0B" marketingCarrier = "0B" departureTerminal = "T1" arrivalTerminal = "T2" departureDate = "2014-03-25T15:30:00" arrivalDate = "2014-03-25T18:35:00" segmentDuration = "0" planeType = "734" segmentStatus = "HK" hasTechnicalStop = "false">
                    <OriginLoc type = "A" code = "OTP" cityCode = "false"/>
                    <DestinationLoc type = "A" code = "MAD" cityCode = "false"/>
                </Segment>
            </Segments>            
            <Fares>
                <Fare id = "0" providerCode = "BLU" fareType = "OW" familyFare="FAMILY1">
                    <Options>
                        <Option id ="0" availJourneyRef = "0" numStopOver = "0" carrier = "UX">
                            <SegmentReferences>
                                <SegmentReference segmentRef = "0">
                                    <SegmentClasses>
                                        <SegmentClass cabinClass = "Y" class = "K" paxRef = "0" fareBasis = "WEB14" fareType = "PUB" avail="9" />
                                    </SegmentClasses>
                                    <ReservationTokens>
                                        <Attribute key = "FareSequence" value = "88"/>
                                        <Attribute key = "RuleNumber" value = "0001"/>
                                    </ReservationTokens>
                                </SegmentReference>
                            </SegmentReferences>
                        </Option>
                    </Options>
                    <AmountBreakdown currency = "EUR" totalAmount = "109.9000" notCommissionableAmount = "0" commission = "-1">
                        <ChargeBreakdowns/>
                        <PaxBreakdowns>
                            <PaxBreakdown paxType = "ADT" amount = "109.9000" taxes = "0" tasaDU = "0"/>
                        </PaxBreakdowns>
                    </AmountBreakdown>
                    <PaxConfigurations>
                        <PaxConfiguration id = "0" paxRef = "0" age = "30" paxType = "ADT">
                            <AppliedBonuses resident = "N" largeFamily = "N" discountCard = "N"/>
                        </PaxConfiguration>
                    </PaxConfigurations>
                    <HasObFees>false</HasObFees>
                </Fare>
            </Fares>     
        </Transportation>
    </AvailabilityRS>
~~~


### AvailabilityRS Description


| **Element**				| **Number**	| **Type**	| **Description**						|
| ------------------------------------- | ------------- | ------------- | ------------------------------------------------------------- |
| AvailabilityRS              		| 1     	|		| Root node.							|
| Transportation              		| 1     	|		| Contains all of the Segments and Fares.			|
| @totalFares            		| 1 		| Integer	| Total number of Fares. 					|
| Transportation/Segments     		| 1     	|		| Contains a list of the Segments.				|
| Transportation/Segments /Segment	| 1..n    	|		| Contains the information of the segment.			|
| @id                    		| 1 		| Integer	| Unique identifier of the segment. 				|
| @transportationId      		| 1 		| String	| Unique Id of the transportation. 				|
| @transportationType    		| 1 		| String	| Transport type: A ( Flight ), T ( Train ), B ( Bus ) & F ( Ferry ).	|
| @operatingCarrier      		| 1 		| String	| Company which operates the transportation.			|
| @marketingCarrier      		| 1 		| String	| Company which commercializes the transportation.		|
| @departureTerminal     		| 1 		| String	| Departure terminal. 						|
| @arrivalTerminal       		| 1 		| String	| Arrival terminal.						|
| @departureDate         		| 1 		| Date		| Departure date.						|
| @arrivalDate           		| 1 		| Date		| Arrival date. 						|
| @segmentDuration       		| 1 		| Integer	| Transport duration ( in minutes ). 				|
| @planeType             		| 1 		| String	| Plane type. Flights parameter.				|
| @maxCheckinDate        		| 1 		| String	| Maximum date to make the check-in. 				|
| @segmentStatus         		| 1 		| String	| Segment status: HK (OK), TK (Change of programming), UC (Unconfirmed), UN( Unable), NO (No action taken) & UD (Undefined).|
| @hasTechnicalStop      		| 1 		| Boolean	| If true, the segment has a technical stop. 			|
| @electronicTicket      		| 1 		| Boolean	| If true, the segment uses a electronic ticket. 		| 
| @secureFlight          		| 0..1		| Boolean	| If true, the provider requires extra information of the passengers. Flights parameter.	|
| Transportation/Segments /Segment/OriginLoc | 1     	|		| Origin location.						|
| @type                  		| 1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).	|
| @code                  		| 1 		| String	| Location code.						|
| @cityCode              		| 1 		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.	|
| Transportation/Segments /Segment/DestinationLoc | 1   |  		| Destination location.						|
| @type                  		| 1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).	|
| @code                  		| 1 		| String	| Location code. 						|
| @cityCode              		| 1 		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.	|
| Transportation/Segments /Segment/TechnicalStops | 0..1 |   		| Contains a list of TechnicalStops.				|
| @totalTechnicalStops   		| 1 		| Integer	| Total number of TechnicalStops. 				|
| Transportation/Segments /Segment/TechnicalStops /TechnicalStop | 1..n | | Contains the details of the TechnicalStop.			|
| @location              		| 1 		| String	| TechnicalStop location.					|
| @stopDate              		| 1 		| Date		| Approx. stop date and time. 					|
| @departureDate         		| 1 		| Date		| Approx. departure date and time.  				|
| Fares                       		| 1     	|		| Contains a list of Fares.					|
| Fares/Fare                  		| 1..n    	|		| Contains details of Fare.					|
| @id                    		| 1 		| Integer	| Unique identifier of the Fare.  				|
| @providerCode          		| 1 		| String	| Provider code.						|
| @fareType              		| 1 		| String	| Fare type: OW ( one way ), RT ( round trip ), OJ ( Open jaw ) & CT ( Circle trip ).	|
| @familyFare            		| 0..1 		| String	| Optional family fare ( the same name of the petition ). Flights parameter. |	
| Fares/Fare/Options          		| 1     	|		| Contains a list of Fare Options.				|
| Fares/Fare/Options/Option   		| 1..n    	|		| Contains details of the Fare Options. 			|
| @id                    		| 1 		| Integer	| Deprecated attribute. 					|
| @availJourneyRef       		| 1  		| Integer	| Reference number of the availability Journey. 		|
| @numStopOver           		| 1 		| Integer	| Number of StopOvers. If -1, then we cannot know how many StopOvers via XML. |
| @carrier               		| 1 		| String	| Validating carrier.						|
| Fares/Fare/Options /Option/SegmentReferences | 1  	|    		| Contains a list of SegmentReferences.				|
| Fares/Fare/Options /Option/SegmentReferences /SegmentReference | 1..n | | Contains details of the SegmentReference of each option.	|
| @segmentRef            		| 1 		| Integer	| Reference of the Segment. 					|
| Fares/Fare/Options /Option/SegmentReferences /SegmentReference/SegmentClasses | 1 | | Contains a list of SegmentClasses.		|
| Fares/Fare/Options /Option/SegmentReferences /SegmentReference/SegmentClasses /SegmentClass | 1..n | | Contains details of the SegmentClass.   |
| @cabinClass            		| 1 		| String	| Cabin class of the seat: N (Not specified), Y (Tourist), C (Business), F (First), CA (Cabin, only for ferries), YP (Tourist Plus).	|
| @class                 		| 1 		| String	| Fare class.							|
| @paxRef               	 	| 1 		| Integer	| Passenger reference. 						|
| @fareBasis             		| 1 		| String	| Identifier of the fare.					|
| @fareType              		| 1 		| String	| Fare type: PUB ( Public ), PRI ( Private ), NEGO ( Negotiated ) and CORP ( Corporate ).	|
| @avail                 		| 1 		| Integer	| Available seats remaining for this class (In flights, the maximum is 9).  |
| Fares/Fare/Options /Option/SegmentReferences /SegmentReference/ReservationTokens | 0..1 |  | Specific attribute used for each provider.	|
| Fares/Fare/Options /Option/SegmentReferences /SegmentReference/ReservationTokens /Attribute | 0..n |  | Type of attribute.		|
| @key                   		| 1 		| String	| Contains the keyword/ Id to identify a parameter.		|
| @value                 		| 1 		| String	| Contains the value of the parameter.				|
| Fares/Fare/Options /Option/BaggageTypes | 0..1    	|		| Contains a list of BaggageTypes.				|
| Fares/Fare/Options /Option/BaggageTypes /BaggageType	| 1..n |  	| Contains details of BaggageType.				|
| Fares/Fare/Options /Option/BaggageTypes /BaggageType/Baggage | 1 |    | Specific attribute used for each provider. 			|
| @checkingType          		| 1 		| String	| Specifies the checkin type: OnLine and Airport.		|
| @appliesSegments       		| 1 		| String	| Type applied to the segment: Departure and Return.		|
| @id                    		| 1 		| String	| Unique identifier of the Baggage.				|
| @type                  		| 1 		| String	| Type of baggage: Bag, Bike, Wheelchair, Skis and BabyTrolley.		|
| @quantity              		| 1 		| Integer	| Baggage quantity.  						|
| @maxWeightPerUnit      		| 1 		| Integer	| Maximum weight of the baggage.  				| 
| @maxTotalWeight        		| 1 		| Integer	| Maximum weight of ALL the baggage.				|
| @paymentInAirpot       		| 1 		| Boolean	| Determines whether the pay is in station. 			|
| @code                  		| 1 		| String	| Code of the Baggage.						|
| @carrier               		| 1 		| String	| Carrier.							|
| @needToken             		| 1 		| Boolean	| Reserve token mandatory.					|
| Fares/Fare/AmountBreakdown  		| 1     	|		| Breakdown of the fare amount.					|
| @currency              		| 1 		| String	| Currency code of the fare.					|
| @totalAmount           		| 1 		| Decimal	| Total amount. with taxes and other charges included.		|
| @notCommissionableAmount		| 1 		| Decimal	| Total amount that can not be commissioned.  			|
| @commission            		| 1 		| Decimal	| Commission. 							|
| Fares/Fare/AmountBreakdown /ChargeBreakdowns | 0..1   |		| Contains a list of breakdown amounts ( taxes, mandatory charges.. ).	|
| Fares/Fare/AmountBreakdown /ChargeBreakdowns/ChargeBreakdown | 1..n |	| Contains details of the BreakdownAmount.			|
| @type                  		| 1 		| String	| Charge type.							|
| @amount                		| 1    	 	|		| Charge amount.						|
| Fares/Fare/AmountBreakdown /ChargeBreakdowns/ChargeBreakdown /Concept | 0..1 | | Contains a list of breakdown amounts ( taxes, mandatory charges.. ).|
| @id                    		| 1 		| String	| Indicates if the conditions are of one way ( with a 0 ) or round trip ( with a 1 ). Ferries parameter.	|
| @language              		| 1 		| String	| Language.							|
| Fares/Fare/AmountBreakdown /ChargeBreakDowns/ChargeBreakdown /Concept/Text | 1 | String | Remarks.					|
| Fares/Fare/AmountBreakdown /PaxBreakdown | 0..1    	|		| Contains a list of breakdown amounts for each passenger ( ADT amount, etc. ).|
| Fares/Fare/AmountBreakdown /PaxBreakdowns/PaxBreakdown | 0..n | 	| Contains details of breakdown amounts for each passenger.	|
| @paxType               		| 1 		| String	| Passenger type: ADT ( Adult ), CHD ( Child ) & INF ( Infant ).	|
| @amount                		| 1 		| Decimal	| Total amount, with taxes included, associated to the passenger.	|
| @taxes                 		| 1 		| Integer	| If they exist, taxes are applied for this passenger type. 	|
| @tasaDU                		| 1 		| Integer	| Deprecated. 							|
| Fares/Fare/PaxConfigurations		| 1     	|		| Contains a list of PaxConfiguration.				|
| Fares/Fare/PaxConfigurations /PaxConfiguration | 1..n |   		| Contains details of PaxConfiguration.				|
| @id                    		| 1 		| Integer	| Unique identifier of the PaxConfiguration. 			|
| @paxRef                		| 1 		| Integer	| Reference to the passenger Id from the request. 		|
| @age                   		| 1 		| Integer	| Age of the passenger. 					|
| @paxType               		| 1 		| String	| Passenger type based on the age of the passenger: ADT (Adult), CHD (Child), INF (Infant), YOU (Young) and SEN (Senior).	|
| Fares/Fare/PaxConfigurations /PaxConfiguration/AppliedBonuses | 0..1 | | Applied discounts.						|
| @resident              		| 1 		| String	| Resident discount type: N(None), BP(Balearic Islands resident flying to mainland), BI(Balearic Islands resident flying to another balearic island), DC(Canarian Islands resident flying to another Canarian Island), RC(Canarian Islands resident flying to mainland),RM(Ceuta/Melilla resident), STR(Italian resident  discount), ELB(Italian resident Elba), SDG(Italian resident Sardegna), SCL(Italian resident Sicily).	|
| @largeFamily           		| 1 		| String	| Family discount type: N(None), F1(Large family), F2 (Special large family). |
| @discountCard          		| 1 		| String	| Discount card type (for more details, see information below).		|
| Fares/Fare/PaxConfigurations /PaxConfiguration/AppliedBonuses /PaxTypeCodes | 0..1 |  | Contains a list of PaxTypeCodes.		|
| Fares/Fare/PaxConfigurations /PaxConfiguration/AppliedBonuses /PaxTypeCodes/PaxTypeCode | 0..n |  | Contains details of the PTC.	|
| @code                  		| 1 		| String	| String with the PTC code.					|
| Fares/Fare/HasObFees        		| 1 		| Boolean	| If true then there is an extra fee for using credit card.   	|


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
