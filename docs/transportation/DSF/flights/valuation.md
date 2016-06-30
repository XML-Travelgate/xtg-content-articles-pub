---
title: Valuation
keywords: transportation, data structure, flights, valuation
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
selected Option at Availability may not be available for this stage. In
this case the integration returns an error code 301 ( link missing ).



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
| ValuationRQ                 		| 1     	|		| Root node. 								|
| Itineraries                 		| 1     	|		| List of Itineraries.							|
| Itineraries/Itinerary       		| 1..n    	|		| Details of the Itinerary.  						|
| @id                    		| 1 		| Integer	| Unique identifier of the Itinerary.					|
| @fareRef	               		| 1 		| Integer	| Reference identifier to the original Fare. Flights parameter.  	|
| @HasObFees             		| 1 		| Boolean	| If true then there is an extra fee for using credit card.  		|
| @carrier               		| 1 		| String	| Validating carrier. Flights parameter.				|
| Itineraries/Itinerary /Conditions	| 0..1    	|		| Contains a list of Conditions.  					|
| Itineraries/Itinerary /Conditions/Condition | 0..n    |		| Contains details of the Condition.					|
| @id                    		| 1 		| String	| Indicates if the conditions are of one way ( with a 0 ) or round trip ( with a 1 ). Ferries parameter.	|
| @language              		| 1 		| String	| Language.								|
| Itineraries/Itinerary /Conditions/Condition /Text | 1 | String	| Remarks.								|
| Itineraries/Itinerary /Journeys	| 0..1    	|		| Contains a list of Journeys.   					|
| Itineraries/Itinerary /Journeys/Journey | 0..n    	|		| Contains details of the Journeys.					|
| @id                    		| 1 		| Integer	| Unique identifier of the Journey in scope.  				|
| @duration              		| 1 		| Integer	| Duration of the Journey in minutes.  					|
| Itineraries/Itinerary /Journeys/Journey/Segments | 0..1 |   		| Contains a list of Segments associated to the Journey.		|
| Itineraries/Itinerary /Journeys/Journey/Segments /Segment | 0..n   |	| Contains details of the SegmentInfo.					|
| @id                    		| 1 		| Integer	| Unique SegmentInfo identifier.					|
| Itineraries/Itinerary /Journeys/Journey/Segments /Segment/SegmentInfo | 0..n | | Contains information of the SegmentInfo.			|
| @id                    		| 1 		| Integer	| Unique identifier of the SegmentInfo. 				|
| @transportationId      		| 1 		| String	| Unique Id of the transportation.					|
| @transportationType    		| 1 		| String	| Transport type: F ( Flight ), T ( Train ), B ( Bus ) & F ( Ferry ).	|
| @operatinCarrier       		| 1 		| String	| Company which operates the transportation.				|
| @marketingCarrier      		| 1 		| String	| Company which commercializes the transportation.			|
| @departureTerminal     		| 1 		| String	| Departure terminal.							|
| @arrivalTerminal       		| 1  		| String	| Arrival terminal.							|
| @departureDate         		| 1 		| Date		| Departure date. 							|
| @arrivalDate           		| 1 		| Date		| Arrival date.								|
| @segmentDuration       		| 1 		| Integer	| Transport duration ( in minutes ). 					|
| @planeType             		| 1 		| String	| Plane type. Flights parameter.					|
| @maxCheckinDate        		| 1 		| String	| Maximum date to make the check-in.					|
| @segmentStatus         		| 1 		| String	| SegmentInfo status: HK (OK), TK (Change of programming), UC (Unconfirmed), UN( Unable), NO (No action taken) & UD (Undefined).  |
| @hasTechnicalStop      		| 1 		| Boolean	| If true, the SegmentInfo has a technical stop.			|
| @electronicTicket      		| 1 		| Boolean	| If true, the SegmentInfo uses a electronic ticket.			|
| @secureFlight          		| 0..1		| Boolean	| If true, the provider requires extra information of the passengers. Flights parameter.	|
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /SegmentInfo/OriginLoc | 1 |  | Origin location.					|
| @type                  		| 1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).	|
| @code                  		| 1 		| String	| Location code.							|
| @cityCode	              		| 1 		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.	|
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /SegmentInfo/DestinationLoc | 1 |  | Destination location.				|
| @type                  		| 1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).	|
| @code                  		| 1 		| String	| Location code.							|
| @cityCode              		| 1 		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.	|
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /SegmentClasses | 0..1 |  | Contains a list of SegmentClasses.			|
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /SegmentClasses/SegmentClass | 0..n 1  | Contains details of the SegmentClass.	|
| @cabinClass            		| 1 		| String	| Cabin class of the seat: N (Not specified), Y (Tourist), C (Business), F (First), CA (Cabin, only for ferries), YP (Tourist Plus).	|
| @class                 		| 1 		| String	| Fare class.								|
| @paxRef                		| 1 		| Integer 	| Reference for the passenger which is using this fare in the transport.  |
| @fareBasis             		| 1 		| String	| Fare basis.								|
| @fareType              		| 1 		| String	| Fare type: PUB ( Public ), PRI ( Private ), NEGO ( Negotiated ) & CORP ( Corporate ).	|
| @avail                 		| 1 		| Integer	| Available seats remaining for this class (In flights, the maximum is 9).  |
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /ReservationToken | 0..1 |  | Contains specific attributes of each provider.		|
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /ReservationToken/Attribute | 0..n |  | Contains details of the attribute.		|
| @key                   		| 1 		| String	| Keyword or id to identify a parameter.				|
| @value                 		| 1 		| String	| Value of the parameter.						|
| Itineraries/Itinerary/AmountBreakdown	| 1     	|		| Contains details of the AmountBreakdown.				|
| @currency              		| 1 		| String	| Currency code of the fare.						|
| @totalAmount           		| 1 		| Decimal	| Total amount. with taxes and other charges included.			|
| @notCommissionableAmount		| 1 		| Decimal	| Total amount that can not be commissioned.				|
| @commission            		| 1 		| Decimal	| Commission.  								|
| Itineraries/Itinerary /AmountBreakdown/ChargeBreakdowns | 0..1  |  	|  Contains a list of ChargeBreakdowns.					|
| Itineraries/Itinerary /AmountBreakdown/PaxBreakdowns | 0..1 |  | Contains a list of breakdown amounts for each passenger ( ADT amount, etc. ). |
| Itineraries/Itinerary /AmountBreakdown/PaxBreakdowns /PaxBreakdown | 0..n |   | Contains details of breakdown amounts for each passenger.	|
| @paxType               		| 1 		| String	| Passenger type: ADT ( Adult ), CHD ( Child ) & INF ( Infant ).	|
| @amount                		| 1 		| Decimal	| Total amount, with taxes included, associated to the passenger.	|
| @taxes                 		| 1 		| Integer	| If they exist, taxes are applied for this passenger type. 		|
| @tasaDU                		| 1 		| Integer	| Deprecated.								|
| Itineraries/Itinerary/PaxConfigurations | 1     	|		| Contains a list of PaxConfigurations.					|
| Itineraries/Itinerary /PaxConfigurations/PaxConfiguration | 1 |  	| Contains details of the PaxConfiguration.				|
| @id                    		| 1 		| Integer	| Unique identifier of the PaxConfiguration.  				|
| @paxRef                		| 1 		| Integer	| Reference to the passenger Id from the request. 			|
| @age                   		| 1 		| Integer	| Age of the passenger.							|
| @paxType               		| 1 		| String	| Passenger type based on the age of the passenger: ADT (Adult), CHD (Child), INF (Infant), YOU (Young) and SEN (Senior).	|
| Fares/Fare/PaxConfigurations /PaxConfiguration/AppliedBonuses | 0..1 | | Applied discounts.							|
| @resident              		| 1 		| String	| Resident discount type: N(None), BP(Balearic Islands resident flying to mainland), BI(Balearic Islands resident flying to another balearic island), DC(Canarian Islands resident flying to another Canarian Island), RC(Canarian Islands resident flying to mainland),RM(Ceuta/Melilla resident), STR(Italian resident discount), ELB(Italian resident Elba), SDG(Italian resident Sardegna), SCL(Italian resident Sicily).	|
| @largeFamily           		| 1 		| String	| Family discount type: N(None), F1(Large family), F2 (Special large family). 1
| @discountCard          		| 1 		| String	| Discount card type (for more details, see information below).		|
| Fares/Fare/PaxConfigurations /PaxConfiguration/AppliedBonuses /PaxTypeCodes | 0..1 |  | Contains a list of PaxTypeCodes.			|
| Fares/Fare/PaxConfigurations /PaxConfiguration/AppliedBonuses /PaxTypeCodes/PaxTypeCode | 0..n |   | Contains details of the PTC.		|
| @code                  		| 1 		| String	| String with the PTC code.						|



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
| ValuationRS                 		| 1     	|		| Root node.								|
| Itineraries                 		| 1     	|		| List of Itineraries.							|
| Itineraries/Itinerary       		| 1..n    	|		| Details of the Itinerary.    						|
| @id                    		| 1 		| Integer	| Unique identifier of the Itinerary.					|
| @fareRef               		| 1 		| Integer	| Reference identifier to the original Fare. Flights parameter.  	|
| @HasObFees             		| 1 		| Boolean 	| If true then there is an extra fee for using credit card.  		|
| @carrier               		| 1 		| String	| Validating carrier. Flights parameter.				|
| Itineraries/Itinerary/Conditions	| 0..1    	|		| Contains a list of Conditions.					|
| Itineraries/Itinerary/Journeys	| 0..1    	|		| Contains a list of Journeys.  					|
| Itineraries/Itinerary /Journeys/Journey | 0..n    	|		| Contains details of the Journeys.					|
| @id                    		| 1 		| Integer	| Unique identifier of the Journey in scope.				|
| @duration              		| 1 		| Integer	| Duration of the Journey in minutes.					|
| Itineraries/Itinerary/Journeys /Journey/Segments | 0..1 |   		| Contains a list of Segments associated to the Journey.		|
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment | 0..n |   	| Contains details of the SegmentInfo.					|
| @id                    		| 1 		| Integer	| Unique SegmentInfo identifier.					|
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /SegmentInfo | 0..n |  | Contains information of the SegmentInfo.			|
| @id                    		| 1 		| Integer	| Unique identifier of the SegmentInfo.					|
| @transportationId      		| 1 		| String	| Unique Id of the transportation.					|
| @transportationType    		| 1 		| String	| Transport type: F ( Flight ), T ( Train ), B ( Bus ) & F ( Ferry ).	|
| @operatinCarrier       		| 1 		| String	| Company which operates the transportation.				|
| @marketingCarrier      		| 1 		| String	| Company which commercializes the transportation.			|
| @departureTerminal     		| 1 		| String	| Departure terminal.							|
| @arrivalTerminal       		| 1 		| String	| Arrival terminal.							|
| @departureDate         		| 1 		| Date		| Departure date.							|
| @arrivalDate           		| 1 		| Date		| Arrival date.								|
| @segmentDuration       		| 1  		| Integer	| Transport duration ( in minutes ).					|
| @planeType             		| 1 		| String	| Plane type. Flights parameter.					|
| @maxCheckinDate        		| 1 		| String	| Maximum date to make the check-in.					|
| @segmentStatus         		| 1 		| String 	| SegmentInfo status: HK (OK), TK (Change of programming), UC (Unconfirmed), UN( Unable), NO (No action taken) & UD (Undefined). |
| @hasTechnicalStop      		| 1 		| Boolean	| If true, the SegmentInfo has a technical stop.			|
| @electronicTicket      		| 1 		| Boolean	| If true, the SegmentInfo uses a electronic ticket.			|
| @secureFlight          		| 0..1		| Boolean	| If true, the provider requires extra information of the passengers. Flights parameter.	|
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /SegmentInfo/OriginLoc | 1 |   | Origin location.					|
| @type                 		| 1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).		|
| @code                  		| 1 		| String	| Location code.							|
| @cityCode              		| 1 		| Boolean 	| If true, the field code indicates a city code, if false, it will indicate an airport code.	|
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /SegmentInfo/DestinationLoc | 1  |   | Destination location.				|
| @type                  		| 1 		| String 	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).	|
| @code                  		| 1 		| String	| Location code.							|
| @cityCode              		| 1 		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.	|
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /SegmentClasses | 0..1 |   | Contains a list of SegmentClasses.			|
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /SegmentClasses/SegmentClass | 0..n |   | Contains details of the SegmentClass.	|
| @cabinClass            		| 1 		| String	| Cabin class of the seat: N (Not specified), Y (Tourist), C (Business), F (First), CA (Cabin, only for ferries), YP (Tourist Plus).	|
| @class                 		| 1 		| String	| Fare class.								|
| @paxRef                		| 1 		| Integer	| Reference for the passenger which is using this fare in the transport.  |
| @fareBasis             		| 1 		| String	| Fare basis.								|
| @fareType              		| 1 		| String	| Fare type: PUB ( Public ), PRI ( Private ), NEGO ( Negotiated ) & CORP ( Corporate ).	|
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /ReservationToken | 0..1 |   | Contains specific attributes of each provider.	|
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /ReservationToken/Attribute | 0..n |   | Contains details of the attribute.		|
| @key                   		| 1 		| String	| Keyword or id to identify a parameter.		|
| @value                 		| 1 		| String	| Value of the parameter.				|
| Itineraries/Itinerary /AmountBreakdown | 1     	|		| Contains details of the AmountBreakdown.		|
| @currency              		| 1 		| String	| Currency code of the fare.				|
| @totalAmount           		| 1 		| Decimal	| Total amount. with taxes and other charges included.	|
| @notCommissionableAmount		| 1 		| Decimal	| Total amount that can not be commissioned.		|
| @commission            		| 1 		| Decimal	| Commission.						|
| Itineraries/Itinerary /AmountBreakdown/ChargeBreakdowns | 0..1 |  	| Contains a list of ChargeBreakdowns.			|
| Itineraries/Itinerary /AmountBreakdown/ChargeBreakdowns /ChargeBreakdown | 1..n |   | Contains details of the ChargeBreakdown.	|
| @type                  		| 1 		| String	| ChargeBreakdown type.					|
| @amount                		| 1 		| Decimal	|Total amount, with taxes included, associated to the passenger.  |
| Itineraries/Itinerary /AmountBreakdown/ChargeBreakdowns /ChargeBreakdown/Concept | 1  |   | Charge concept.			|
| @id                    		| 1 		| String	| Indicates if the conditions are of one way ( with a 0 ) or round trip ( with a 1 ). Ferries parameter.	|
| @language              		| 1 		| String	| Language.						|
| Itineraries/Itinerary /AmountBreakdown/ChargeBreakdowns /ChargeBreakdown/Concept/Text | 1 | String | Remarks.			|
| Itineraries/Itinerary /AmountBreakdown/PaxBreakdowns | 0..1  |  	| Contains a list of breakdown amounts for each passenger ( ADT amount, etc. ).	|
| Itineraries/Itinerary /AmountBreakdown/PaxBreakdowns /PaxBreakdown | 0..n |  | Contains details of breakdown amounts for each passenger. |
| @paxType               		| 1 		| String	| Passenger type: ADT ( Adult ), CHD ( Child ) & INF ( Infant ).   |
| @amount                		| 1 		| Decimal	| Total amount, with taxes included, associated to the passenger.  |
| @taxes                 		| 1 		| Integer	| If they exist, taxes are applied for this passenger type.	|
| @tasaDU                		| 1 		| Integer	| Deprecated.						|
| Itineraries/Itinerary /PaxConfigurations | 1     	|		| Contains a list of PaxConfigurations.			|
| Itineraries/Itinerary /PaxConfigurations/PaxConfiguration | 1  |   	| Contains details of the PaxConfiguration.		|
| @id                    		| 1 		| Integer	| Unique identifier of the PaxConfiguration.		|
| @paxRef                		| 1 		| Integer	| Reference to the passenger Id from the request.	|
| @age                   		| 1 		| Integer	| Age of the passenger.					|
| @paxType               		| 1 		| String	| Passenger type based on the age of the passenger: ADT (Adult), CHD (Child), INF (Infant), YOU (Young) and SEN (Senior).|
| Itineraries/Itinerary /PaxConfigurations/PaxConfiguration /AppliedBonuses | 0..1 |   | Applied discounts.			|
| @resident              		| 1 		| String	| Resident discount type: N(None), BP(Balearic Islands resident flying  to mainland), BI(Balearic Islands resident flying to another balearic  island), DC(Canarian Islands resident flying to another Canarian Island), RC(Canarian Islands resident flying  to mainland),RM(Ceuta/Melilla resident), STR(Italian resident discount), ELB(Italian resident  Elba), SDG(Italian resident Sardegna), SCL(Italian resident Sicily).	|
| @largeFamily           		| 1 		| String	| Family discount type: N(None), F1(Large family), F2 (Special large family).	|
| @discountCard          		| 1 		| String	| Discount card type (for more details, see information below).  |
| Itineraries/Itinerary /PaxConfigurations/PaxConfiguration /AppliedBonuses/PaxTypeCodes | 0..1 |   | Contains a list of PaxTypeCodes.	|
| Itineraries/Itinerary /PaxConfigurations/PaxConfiguration /AppliebBonuses/PaxTypeCodes /PaxTypeCode | 0..n |   | Contains details of the PTC.|
| @code                  		| 1 		| String	| String with the PTC code.				|



### ValuationSupplements


  

This option is only shown when requested in Preferences node. The
functionality is the same has SupplementsRQ.



| **Element**				| **Number**	| **Type**	| **Description**					|
| ------------------------------------- | ------------- | ------------- | ----------------------------------------------------- |
| Supplements                  		| 1      	|		| Supplements node in ValuationRS.			|
| PaymentMethods                 	| 0..1    	|		| Contains a list of paymentMethods.   			|
| PaymentMethods/PaymentMethod 		| 1..n    	|		| Contains paymentMethod details.			|
| @paymentType            		| 1  		| String	| Payment Type (CreditCard, ElectronicBanking).		|
| @cardType               		| 1  		| String	| Card type with a provider format.			|
| PaymentMethods/PaymentMehotd /PaymentCharge | 1      	|		| Charge of this payment.				|
| @currency               		| 1  		| String	| Currency code of the supplement.			|
| @fixAmount              		| 1 	 	| Decimal	| Fix amount.						|
| @minFixAmount           		| 1  		| Decimal	| Minimum fix amount to be applied.  			|
| @appliesFixAmount       		| 1  		| String	| Fix amount applies: ByPassenger, BySegment, BaseAmount, Taxes, ForAdt (by adult), ForChd (by child) and ForInf (by infant).	|
| @percentage             		| 1  		| Decimal	| Percentage.						|
| @minAmountPercentage    		| 1  		| Decimal	| Minimum percentage charge.				|
| @percentageApplied      		| 1  		| String	| Percentage applied: ByPassenger, BySegment, BaseAmount, Taxes, ForAdt (by adult), ForChd (by child) and ForInf (by infant).	|
| BaggageTypes                 		| 0..1    	|		| List of Baggage information.     			|
| BaggageTypes/BaggageType     		| 1..n    	|		| Baggage information.     				|
| @checkInType            		| 1  		| String	| Check-in type (OnLine, Airport).			|
| @appliesSegments        		| 1  		| String	| Segments in which is applied: All, Departure, Return, Ref.  |
| BaggageTypes/BaggageType /Baggage	| 1..n    	|		| Baggage description and charge.   			|
| @id                     		| 1  		| String	| Unique identifier of the Baggage.			|
| @type                   		| 1  		| String	| Type of baggage: Bag, Bike, Wheelchair, Skis and BabyTrolley.  |
| @quantity               		| 1  		| Integer	| Baggage quantity.					| 
| @maxWeightPerUnit       		| 1  		| Integer	| Maximum weight of the baggage.			|
| @maxTotalWeight         		| 1  		| Integer	| Maximum weight of ALL the baggage.			|
| @paymentInAirpot        		| 1  		| Boolean 	| Determines whether the pay is in station. 		|
| @code                   		| 1  		| String	| Code of the Baggage.					|
| @carrier                		| 1  		| String	| Carrier.						|
| @needToken              		| 1  		| Boolean	| Reserve token mandatory.				|
| BaggaesInfos/BaggageType /Baggage/BaggageCharge | 1  	|    		| Charge of this payment.				|
| @currency               		| 1  		| String	| Currency code of the supplement.			|
| @fixAmount              		| 1  		| Decimal	| Fix amount.						|
| @minFixAmount           		| 1  		| Decimal	| Minimum fix amount to be applied.   			|
| @appliesFixamount       		| 1  		| String	| Fix amount applies: ByPassenger, BySegment, BaseAmount, Taxes, ForAdt (by adult), ForChd (by child) and ForInf (by infant).	|
| @percentage             		| 1  		| Decimal	| Percentage.						|
| @minamountPercentage    		| 1  		| Decimal	| Minimum percentage charge.				|
| @percentageApplied      		| 1  		| String	| Percentage applied: ByPassenger, BySegment, BaseAmount, Taxes, ForAdt (by adult), ForChd (by child) and ForInf (by infant).	|
| BaggageTypes/BaggageType /References	| 0..1    	|		| Contains a list References.				|
| BaggageTypes/BaggageType /References/SegmentReferences | 0..1 |   	| List of SegmentInfo References.			|
| BaggageTypes/BaggageType /References/SegmentReferences /SegmentReference | 0..n |   | SegmentInfo Reference.			|
| @itineraryRef           		| 1  		| Integer	| Itinerary Reference.   				|
| @journeyRef             		| 1  		| Integer	|Journey Reference.					|
| @segmentRef             		| 1  		| Integer	| SegmentInfo Reference.				|
| BaggageTypes/BaggageType /References/PaxReferences | 0..1 |   	| List of references to passengers related to the baggage information.|
| BaggageTypes/BaggageType /References/PaxReferences /PaxReference | 0..n |   | Contains PaxReference details.  		|
| @paxRef                 		| 1  		| Integer	| Unique identifier of the PaxReference. 		|
| Seating                      		| 0..1    	|		| Seating availability.     				|
| Seating/BlockRules           		| 0..n    	|		| Blocks of references.    				|
| Seating/BlockRules/BlockRule 		| 0..n    	|		| Block of references.     				|
| Seating/BlockRules/BlockRule/References | 0..1    	|		| List of references to Blocks (seating details), Segments and Passengers.	|
| Seating/BlockRules/BlockRule /References/BlockReferences | 0..1 |   	| References to block elements. 			|
| Seating/BlockRules/BlockRule /References/BlockReferences /BlockReference | 0..n |   | List of references.			|
| @blockTypeRef           		| 1  		| String	| Referenced block type: UNASSIGNED(Unassigned), AIRLINE (Airline). |
| @blockRef               		| 1  		| Integer	| Reference to block id.  				|
| Seating/BlockRules/BlockRule /References/PaxReferences | 0..1 |   	| References to Passenger.				|
| Seating/BlockRules/BlockRule /References/PaxReferences /PaxReference | 0..n |   | Reference to a Passenger.			|
| @paxRef                 		| 1  		| Integer	| The id number of the passenger referenced. 		|
| Seating/BlockRules/BlockRule /BlockPrice | 0..1  	|  		| Price element.					|
| Seating/BlockRules/BlockRule /BlockPrice/Amount | 1  	|    		| Amount by type.					|
| @currency               		| 1  		| String	| Currency code of the amount.				|
| @amount                 		| 1  		| Decimal	| Amount.						|
| @amountType             		| 1  		| String	| Amount type: AMOUNT (Amount), FEE (Service Fee), TOTAL (Total), PERCENTUAL (Percentual).	|
| Seating/Blocks                  	| 0..1    	|		| Seating details.   					|
| Seating/Blocks/Block         		| 0..n    	|		| Cabin block.						|
| @type                   		| 1  		| String	| Type (CABIN).						|
| @id                     		| 1  		| Integer	| Unique id.						|
| Seating/Blocks/Block /Blocks/Block 	| 0..n    	|		| Row block.  						|
| @type                   		| 1  		| String	| Type (ROW).						|
| @id                     		| 1  		| Integer	| Unique id.						|
| @number                 		| 1  		| Integer	| Row number.						|
| Seating/Blocks/Block/Blocks /Block/Blocks/Block | 0..n  |   		| Seat block.						|
| @type                   		| 1  		| String	| Type (SEAT).						|
| @id                     		| 1  		| Integer	| Unique id. 						|
| @number                 		| 1  		| String	| Seat identifier.					|
| @token                  		| 1  		| String	| Reserve token.					|
| Seating/Blocks/Block/Blocks /Block/Blocks/Block /Availability | 0..1 |  | Availability of the seat.				|
| @isAvailable            		| 1  		| String	| Indicates whether the seat is available.		|
| Seating/Blocks/Block/Blocks /Block/Blocks/Block /BlockAttributes | 0..1 |   | Seat attributes.   				|
| Seating/Blocks/Block/Blocks /Block/Blocks/Block /BlockAttributes/BlockAttribute | 0..n |  | Seat attribute.                   |
| @type                   		| 1  		| String	| Seat type (OVER_WING, MIDDLE, AISLE, WINDOW, COMPARTMENT, LAVATORY, LUGGAGE).	|
| SpecialSupplements           		| 0..1    	|		| Ancillaries.      					|
| SpecialSupplements/SpecialSupplement	| 0..n    	|		| List of ancillaries.					|
| @id                     		| 1  		| String	| Identifier.						|
| @type                   		| 1  		| String	| Ancillary type (Miscellaneous, Seat, Meal, Pet, Lounge, Baggage). |
| @quantity               		| 1  		| Integer	| Quantity.						|
| @code                   		| 1  		| String	| Code from the provider.				|
| @needToken              		| 1  		| Boolean	| Reserve token mandatory.  				|
| @description            		| 1  		| String	| Description.						|
| Conditions                   		| 0..1    	|		| List of applied fare conditions. 			|
| Conditions/Condition            	| 1..n    	|		| Fare condition.   					|
| @id                     		| 1  		| String	| Typified id for the fare rule.			|
| Conditions/Condition/Paragraph	| 0..n    	|		| Group of sentences.					|
| @title                  		| 1  		| String	| Title.						|
| Conditions/Condition/Paragraph /Sentence | 0..n	| String	| Sentences of the fare rule.				|

