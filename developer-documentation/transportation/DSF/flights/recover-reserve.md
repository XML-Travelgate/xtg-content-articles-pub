---
title: RetrieveReservation
keywords: transportation, data structure, flights, recover reserve, retrieve, reservation
sidebar: mydoc_sidebar
permalink: /developer-documentation/transportation/DSF/flights/recover-reserve
---



Method Goals
============

This method aims to retrieve a booking with its full details.



RetrieveReservationRQ Example
=============================



    <RetrieveReservationRQ xmlns:xsd = "http://www.w3.org/2001/XMLSchema" xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance">
        <Configuration/>
        <ClientConfiguration/>
        <Locator>A3U4NS</Locator>
    </RetrieveReservationRQ>



RetrieveReservationRQ Description
=================================

| **Element**				| **Number**	| **Type**	| **Description**					|
| ------------------------------------- | ------------- | ------------- | ----------------------------------------------------- |
| RetrieveReservationRQ         	| 1    		|		| Root node.						|
| Locator                       	| 1 		| String	| Locator.						|




RetrieveReservationRS Example
=============================



    <RetrieveReservationRS xmlns:xsd = "http://www.w3.org/2001/XMLSchema" xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance">
        <auditData>
            <timeStamp>2014-03-11T09:02:21.1120439+01:00</timeStamp>
            <processTimeMilliseconds>0</processTimeMilliseconds>
        </auditData>
        <operationImplemented>true</operationImplemented>
        <ResponseStatus tripType = "IDA" petitionType = "OW" status = "ok"/>
        <Passengers>
            <Passenger
                passengerType = "MR"
                name = "TestNom"
                surname = "TestApe"
                birthDate = "1984-03-10T23:00:00"
                codeDCO = "0"
                documentType = "NATIONAL_ID"
                documentExpiration = "0001-01-01T00:00:00"
                nationality = ""
                gender = "72"/>
        </Passengers>
        <Segments>
            <Segment
                id = "0"
                transportationId = "IB3857"
                transportationType = "V"
                operatinCarrier = "IB"
                marketingCarrier = "IB"
                departureTerminal = "1"
                departureDate = "2015-09-06T11:25:00"
                arrivalDate = "2015-09-06T15:00:00"
                segmentDuration = "0"
                maxCheckinDate = "2015-08-25T00:00:00"
                planeType = "32S"
                segmentStatus = "HK"
                electronicTicket = "true"
                hasTechnicalStop = "false">
                <OriginLoc type = "A" code = "ACE" citycode = "false"/>
                <DestinationLoc type = "A" code = "MAD" citycode = "false"/>
            </Segment>
        </Segments>
        <Tickets>
            <Ticket id = "1" ticketNum = "030-5035415825" paxName = "" cancelled = "0" joined = "0" seatType = "UNKNOWN" type = "eTicket" status = "Confirmed"/>
            <retrieveStatus>true</retrieveStatus>
        </Tickets>
        <BookingBreakdown>
            <AmountBreakdown currency = "EUR" totalAmount = "0.0000"/>
        </BookingBreakdown>
        <Itineraries>
            <Itinerary id = "0" HasObFees = "false">
                <Journeys>
                    <Journey id = "0" duration = "100">
                        <Segments>
                            <Segment id = "0">
                                <SegmentInfo
                                    id = "0"
                                    transportationId = "IB3857"
                                    transportationType = "V"
                                    operatinCarrier = "IB"
                                    marketingCarrier = "IB"
                                    departureTerminal = "1"
                                    departureDate = "2015-09-06T11:25:00"
                                    arrivalDate = "2015-09-06T15:00:00"
                                    segmentDuration = "0"
                                    maxCheckinDate = "2015-08-25T00:00:00"
                                    planeType = "32S"
                                    segmentStatus = "HK"
                                    electronicTicket = "true"
                                    hasTechnicalStop = "false">
                                    <OriginLoc type = "A" code = "ACE" citycode = "false"/>
                                    <DestinationLoc type = "A" code = "MAD" citycode = "false"/>
                                </SegmentInfo>
                                <SegmentClasses>
                                    <SegmentClass cabinClass = "N" class = "A" paxRef = "2" fareBasis = "AJSK" fareType = "PUB"/>
                                    <SegmentClass cabinClass = "N" class = "A" paxRef = "3" fareBasis = "AJSK" fareType = "PUB"/>
                                </SegmentClasses>
                                <ReservationToken>
                                    <Attribute key = "quotingMethod" value = "A"/>
                                    <Attribute key = "tstIndicator" value = "I"/>
                                </ReservationToken>
                            </Segment>
                        </Segments>
                    </Journey>
                </Journeys>
                <ChargeBreakdown currency = "EUR" totalAmount = "67">
                    <ChargeBreakdowns/>
                    <PaxBreakdowns>
                        <PaxBreakdown paxType = "ADT" amount = "67" taxes = "0" tasaDU = "0"/>
                    </PaxBreakdowns>
                </ChargeBreakdown>
                <PaxConfigurations/>
                <Emisiones/>
            </Itinerary>
        </Itineraries>
        <PaymentMethod PaymentType = "CASH"/>
        <Locators>
            <id>KENHSR</id>
            <type>PROVEEDOR</type>
        </Locators>
        <Locators>
            <id>225901#</id>
            <type>TFBOOKINGREFERENCE</type>
        </Locators>
        <commission>0</commission>
    </RetrieveReservationRS>

|

RetrieveReservationRS Description
=================================


| **Element**				| **Number**	| **Type**	| **Description**					|
| ------------------------------------- | ------------- | ------------- | ----------------------------------------------------- |
| RetrieveReservationRS          	| 1  		|    		| Root node.                          			|
| Passengers                     	| 1  		|    		| Contains a list of Passengers.      			|
| Passengers/Passenger           	| 1..n 		|    		| Contains information of the Passenger.         	|
| @passengerType	            	| 1  		| String 	| Treatment: MR, MRS, CHD and INF.    			|
| @name                     		| 1  		| String 	| Name of the Passenger.              			|
| @surname                  		| 1  		| String 	| Surname/s of the Passenger.         			|
| @bithDate                 		| 1  		| String 	| Date of birth.                      			|
| @codeDCO                  		| 1  		| String 	| Document code.                      			|
| @documentType             		| 1  		| String 	| Documentation type.                 			|
| @documentId               		| 1  		| String 	| Unique identifier of the documentation.           	|
| @documentExpiration       		| 1  		| String 	| Expiration date of the documentation.              	|
| @nationality              		| 1  		| String 	| Nationality.                        			|
| Segments                       	| 1  		|    		| Contains a list of Segment.         			|
| Segments/Segment               	| 0..n 		|    		| Contains details of the Segment.    			|
| @id                       		| 1  		| Integer 	| Unique identifier of the SegmentInfo.           	|
| @transportationId         		| 1  		| String 	| Unique Id of the transportation.    			|
| @transportationType       		| 1  		| String 	| Transport type: V ( Flight ), T ( Train ), B ( Bus ) & F ( Ferry ).  |
| @operatinCarrier          		| 1  		| String 	| Company which operates the transportation.         	|
| @marketingCarrier         		| 1  		| String 	| Company which commercializes the transportation.   	|
| @departureTerminal        		| 1  		| String 	| Departure terminal.                 			|
| @arrivalTerminal          		| 1  		| String 	| Arrival terminal.                   			|
| @departureDate            		| 1  		| Date 		| Departure date.                     			|
| @arrivalDate              		| 1  		| Date 		| Arrival date.                       			|
| @segmentDuration          		| 1  		| Integer 	| Transport duration ( in minutes ).  			|
| @planeType                		| 1  		| String 	| Plane type. Flights parameter.      			|
| @maxCheckinDate           		| 1  		| String 	| Maximum date to make the check-in.  			|
| @segmentStatus            		| 1  		| String 	| SegmentInfo status: HK (OK), TK (Change of programming), UC (Unconfirmed), UN( Unable), NO (No action taken) & UD (Undefined).    |
| @hasTechnicalStop         		| 1  		| Boolean 	| If true, the SegmentInfo has a technical stop.     	|
| @electronicTicket         		| 1  		| Boolean 	| If true, the SegmentInfo uses a electronic ticket.    |
| Segments/Segment/OriginLoc    	| 1  		|    		| Origin location.                    			|
| @type                     		| 1  		| String 	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).    |
| @code                     		| 1  		| String 	| Location code.                      			|
| @cityCode                 		| 1  		| Boolean 	| If true, the field code indicates a city code, if false, it will indicate an airport code.	|
| Segments/Segment/DestinationLoc 	| 1  		|    		| Destination location.               			|
| @type                     		| 1  		| String 	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).     |
| @code                     		| 1  		| String 	| Location code.                      			|
| @cityCode                 		| 1  		| Boolean 	| If true, the field code indicates a city code, if false, it will indicate an airport code. |
| Segments/Segment/TechnicalStops 	| 0..1 		|    		| Contains a list of TechnicalStops.  			|
| @totalTechnicalStops      		| 1  		| Integer 	| Total number of TechnicalStops.     			|
| Segments/Segment/TechnicalStops /TechnicalStop | 1..n |    		| Contains the details of the TechnicalStop.        	|
| @location                 		| 1  		| String 	| TechnicalStop location.             			|
| @stopDate                 		| 1  		| Date 		| Approx. stop date and time.         			|
| @departureDate            		| 1  		| Date 		| Approx. departure date and time.    			|
| Segments/Segment/SegmentClasses 	| 0..1 		|    		| Contains a list of SegmentClasses.  			|
| Segments/Segment/SegmentClasses /SegmentClass | 0..n 	|    		| Contains details of the SegmentClass.             	|
| @cabinClass               		| 1  		| String 	| Cabin class of the seat: N (Not specified), Y (Tourist), C (Business), F (First), CA (Cabin, only for ferries), YP (Tourist Plus).    |
| @class                    		| 1  		| String 	| Fare class.                         			|
| @paxRef                   		| 1  		| Integer 	| Reference for the Passenger which is using this fare in the transport.    |
| @fareBasis                		| 1  		| String 	| Fare basis.                         			|
| @fareType                 		| 1  		| String 	| Fare type: PUB ( Public ), PRI ( Private ), NEGO ( Negotiated ) & CORP ( Corporate ).    |
| Segments/Segment/ReservationToken 	| 0..1 		|    		| Contains specific attributes of each provider.    	|
| Segments/Segment/ReservationToken /Attribute | 0..n 	|    		| Contains details of the attribute.  			|
| @id                       		| 1  		|    		| Keyword or id to identify a parameter.        	|
| @value                    		| 1  		|    		| Value of the parameter.             			|
| Tickets                        	| 1  		|    		| List of issued tickets.             			|
| Tickets/retrieveStatus         	| 1  		| Boolean 	| Indicates whether or not the reservation had its tickets issued.       |
| Tickets/errorRetrieve          	| 1  		| String 	| Indicates error in the ticket retrieval.      	|
| Tickets/Ticket                 	| 1..n 		|    		| Details of issued ticket.           			|
| @id                       		| 1  		| Integer 	| Unique identifier of the ticket.    			|
| @ticketNum                		| 1  		| String 	| Ticket number.                      			|
| @paxName                  		| 1  		| String 	| Name of the passenger associated to the ticket. 	|
| @status                   		| 1  		| String 	| Current status of the ticket: OPEN, CONFIRMED, VOIDED, REFUNDED. |
| BookingBreakdown               	| 1  		|    		| Contains price information.         			|
| BookingBreakdown/AmountBreakdown 	| 1  		|    		| Total amount information.           			|
| @currency                 		| 1  		| String 	| Currency.                           			|
| @totalAmount              		| 1  		| Decimal 	| Total price.                        			|
| Itineraries                    	| 1  		|    		| List of Itineraries.                			|
| Itineraries/Itinerary          	| 1..n 		|    		| Details of the Itinerary.           			|
| @id                       		| 1  		| Integer 	| Unique identifier of the Itinerary. 			|
| @fareRef                  		| 1  		| Integer 	| Reference identifier to the original Fare. Flights parameter.   |
| @HasObFees                		| 1  		| Boolean 	| If true then there is an extra fee for using credit card.  |
| @carrier                  		| 1  		| String 	| Validating carrier. Flights parameter.        	|
| Itineraries/Itinerary/Journeys 	| 0..1 		|    		| Contains a list of Journeys.        			|
| Itineraries/Itinerary/Journeys /Journey | 0..n 	|    		| Contains details of the Journeys.   			|
| @id                       		| 1  		| Integer 	| Unique identifier of the Journey in scope.		|
| @duration                 		| 1  		| Integer 	| Duration of the Journey in minutes. 			|
| Itineraries/Itinerary/Journeys /Journey/Segments | 0..1 |    		| Contains a list of Segments associated to the Journey.    |
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment | 0..n |   	| Contains details of the SegmentInfo.             	|
| @id                       		| 1  		| Integer 	| Unique SegmentInfo identifier.      			|
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /SegmentInfo | 0..n |    | Contains information of the SegmentInfo.       |
| @id                       		| 1  		| Integer 	| Unique identifier of the SegmentInfo.           	|
| @transportationId         		| 1  		| String 	| Unique Id of the transportation.    			|
| @transportationType       		| 1  		| String 	| Transport type: F ( Flight ), T ( Train ), B ( Bus ) & F ( Ferry ).|
| @operatinCarrier          		| 1  		| String 	| Company which operates the transportation.          	|
| @marketingCarrier         		| 1  		| String 	| Company which commercializes the transportation.   	|
| @departureTerminal        		| 1  		| String 	| Departure terminal.                 			|
| @arrivalTerminal          		| 1  		| String 	| Arrival terminal.                   			|
| @departureDate            		| 1  		| Date 		| Departure date.                     			|
| @arrivalDate              		| 1  		| Date 		| Arrival date.                       			|
| @segmentDuration          		| 1  		| Integer 	| Transport duration ( in minutes ).  			|
| @planeType                		| 1  		| String 	| Plane type. Flights parameter.      			|
| @maxCheckinDate           		| 1  		| String 	| Maximum date to make the check-in.  			|
| @segmentStatus            		| 1  		| String 	| SegmentInfo status: HK (OK), TK (Change of programming), UC (Unconfirmed), UN( Unable), NO (No action taken) & UD (Undefined).     |
| @hasTechnicalStop         		| 1  		| Boolean 	| If true, the SegmentInfo has a technical stop.     	|
| @electronicTicket         		| 1  		| Boolean 	| If true, the SegmentInfo uses a electronic ticket.    |
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /SegmentInfo/OriginLoc | 1  |    | Origin location.                  |
| @type                     		| 1  		| String 	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).      |
| @code                     		| 1  		| String 	| Location code.                      			|
| @cityCode                 		| 1  		| Boolean 	| If true, the field code indicates a city code, if false, it will indicate an airport code. |
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /SegmentInfo/DestinationLoc | 1  |    | Destination location.        |
| @type                     		| 1  		| String 	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).     |
| @code                     		| 1  		| String 	| Location code.                      			|
| @cityCode                 		| 1  		| Boolean 	| If true, the field code indicates a city code, if false, it will indicate an airport code.  |
| Transportation/Segments/Segment /TechnicalStops | 0..1 |    		| Contains a list of TechnicalStops.  			|
| @totalTechnicalStops      		| 1  		| Integer 	| Total number of TechnicalStops.     			|
| Transportation/Segments/Segment /TechnicalStops/TechnicalStop | 1..n |    | Contains the details of the TechnicalStop.        |
| @location                 		| 1  		| String 	| TechnicalStop location.             			|
| @stopDate                 		| 1  		| Date 		| Approx. stop date and time.         			|
| @departureDate            		| 1  		| Date 		| Approx. departure date and time.    			|
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /SegmentClasses | 0..1 |    | Contains a list of SegmentClasses.  	|
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /SegmentClasses/SegmentClass  | 0..n |    | Contains details of the SegmentClass.            |
| @cabinClass               		| 1  		| String 	| Cabin class of the seat: N (Not specified), Y (Tourist), C (Business), F (First), CA (Cabin, only for ferries), YP (Tourist Plus).    |
| @class                    		| 1  		| String 	| Fare class.                         			|
| @paxRef                   		| 1  		| Integer 	| Reference for the Passenger which is using this fare in the transport.   |
| @fareBasis                		| 1  		| String 	| Fare basis.                         			|
| @fareType                 		| 1  		| String 	| Fare type: PUB ( Public ), PRI ( Private ), NEGO ( Negotiated ) & CORP ( Corporate ).   |
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /ReservationToken | 0..1 |    | Contains specific attributes of each provider.  |
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /ReservationToken/Attribute | 0..n |    | Contains details of the attribute.  |
| @id                       		| 1  		|    		| Keyword or id to identify a parameter.          	|
| @value                    		| 1  		|    		| Value of the parameter.             			|
| Itineraries/Itinerary/AmountBreakdown | 1  		|    		| Contains details of the AmountBreakdown.              |
| @currency                 		| 1  		| String 	| Currency code of the fare.          			|
| @totalAmount              		| 1  		| Decimal 	| Total amount. with taxes and other charges included. 	|
| @notCommissionableAmount  		| 1  		| Decimal 	| Total amount that can not be commissioned.       	|
| @commission               		| 1  		| Decimal 	| Commission.                         			|
| Itineraries/Itinerary/AmountBreakdown /ChargeBreakdowns  | 0..1 |    	| Contains a list of ChargeBreakdowns.                 	|
| Itineraries/Itinerary/AmountBreakdown /PaxBreakdowns | 0..1 |    	| Contains a list of breakdown amounts for each Passenger ( ADT amount, etc. ).     |
| Itineraries/Itinerary/AmountBreakdown /PaxBreakdowns/PaxBreakdown | 0..n |    | Contains details of breakdown amounts for each Passenger.  |
| @paxType                  		| 1  		| String 	| Passenger type: ADT ( Adult ), CHD ( Child ) & INF ( Infant ). |
| @amount                   		| 1  		| Decimal 	| Total amount, with taxes included, associated to the Passenger. |
| @taxes                    		| 1  		| Integer 	| If they exist, taxes are applied for this Passenger type.     |
| @tasaDU                   		| 1  		| Integer 	| Deprecated                          			|
| Itineraries/Itinerary/PaxConfigurations | 1  		|    		| Contains a list of PaxConfigurations.                 |
| Itineraries/Itinerary /PaxConfigurations/PaxConfiguration  | 1  |    	| Contains details of the PaxConfiguration.             |
| @id                       		| 1  		| Integer 	| Unique identifier of thePaxConfiguration.             |
| @paxRef                   		| 1  		| Integer 	| Reference to the Passenger Id from the request.  	|
| @age                      		| 1  		| Integer 	| Age of the Passenger.               			|
| @paxType                  		| 1  		| String 	| Passenger type based on the age of the Passenger: ADT (Adult), CHD (Child), INF (Infant), YOU (Young) and SEN (Senior). |
| @code                     		| 1  		| String 	| String with the PTC code.           			|
| PaymentMethod                  	| 1  		|    		| Defines the payment method used in the reservation. 	|
| @paymentType              		| 1  		| String 	| Payment type: CASH, CARD and EMIT.  			|
| PaymentMethod/PaymentDatas     	| 1  		|    		| List of PaymentData.                			|
| PaymentMethod/PaymentDatas /PaymentData | 1..n 	|    		| Contains the details of PaymentData.            	|
| @paymentType              		| 1  		| String 	| Payment type: CASH, CARD and EMIT.  			|
| PaymentMethod/PaymentDatas /PaymentData/CardInfo | 1  |    		| Contains details of the credit card.     		|
| @provType                 		| 1  		| String 	| Card type.                          			|
| @holder                   		| 1  		| String 	| Holder.                             			|
| @number                   		| 1  		| String 	| Credit card number.                 			|
| @cvv                      		| 1  		| String 	| Verification code.                  			|
| @expirationMonth          		| 1  		| String 	| Expiration month.                   			|
| @expirationYear           		| 1  		| String 	| Expiration year.                    			|
| Locators                       	| 1  		|    		| Contains a list of locators.        			|
| Locators/Locator               	| 1  		|    		| Contains details of the locator.    			|
| Locators/Locator/Id            	| 1  		| String 	| Unique identifier of the locator.   			|
| Locators/Locator/Type          	| 1  		| String 	| Locator type: PROVIDER, TFBOOKINGREFERENCE, UNIVERSAL, EMISSION and CARRIER.     |


