---
title: Reservation
keywords: transportation, data structure, flights, reservation
sidebar: mydoc_sidebar
permalink: /developer-documentation/transportation/DSF/flights/reservation
---



Method Goals
============

This method aims to book one or more Itineraries.



Request Format
==============

The request format works the same way as the Valuation request. It can
work with one or with two Itineraries. The request will also contain a
list of Passengers and the PaymentInfo, such as payment method.



Response Format
===============

The result returns a list of Locators (booking codes). It can be the
supplier's or the one sent in the request. It also returns all the
charges associated to the booking.



Remarks
=======

This method **must** be called **after** the Valuation method.

The maximum time that our systems permits before closing the connexion
is of **25000** milliseconds.

The booking data should meet the following requirements. ADVICE: All
requirements are only indicative and could change in the future.

- Passenger Type: Adult: \>11 years. Child: 2-11 years. Infant: 0-1 years.

- Companies with mandatory nationality (2 digit codes): AK D7 FD I5 PQ QZ
XJ XT Z2 E9 SL

- Mandatory personal identification: - (NIF, NIE) Bookings with spanish
resident discount or some of this companies: NT H2 1T ZY 9C - (Passport)
Intercontinental flights or when origin or destination are one of this
countries: CN DM JP CU US CA GM MX RU ID DO or when the airline is one
of this: RI TR SU TT 3O AT H2 NT OB U6 UN UT V0 XY E9 - Passport data
includes passport number and expedition date and expiration date. If the
company is E9 country and city of expedition must be included.

- Discounts: - Spanish resident discount: first and second surname must be
included in proper mean and also resident code and zip code. - Large
Family discount: large family number must be included and also large
family code and region code.


     

ReservationRQ Example
===================== 



    <ReservationRQ>
        <Configuration/>
        <ClientConfiguration currencyCode = "GBP"/>
        <Itineraries>
            <Itinerary id = "0" carrier = "UX">
                <Conditions/>
                <Journeys>
                    <Journey id = "0">
                        <Segments>
                            <SegmentInfo id = "0">
                                <SegmentInfo transportationId = "ZB 226" operatingCarrier = "ZB" marketingCarrier = "ZB" departureTerminal = "LGW" arrivalTerminal = "PMI" departureDate = "2014-04-08T08:00:00" arrivalDate = "2014-04-08T11:20:00" segmentStatus = "HK">
                                    <OriginLoc type = "A" code = "LGW" cityCode = "false"/>
                                    <DestinationLoc type = "A" code = "PMI" cityCode = "false"/>
                                </SegmentInfo>
                                <SegmentClasses>
                                    <SegmentClass cabinClass = "Y" class = "E" paxRef = "0" fareBasis = "EO" fareType = "PUB"/>
                                </SegmentClasses>
                                <ReservationTokens>
                                    <Attribute key = "JourneySellKey" value = "ZB~ 226~ ~~LGW~04/08/2014 08:00~PMI~04/08/2014 11:20~"/>
                                    <Attribute key = "FareSellKey" value = "0~E~~EO~ZB03~~7~X"/>
                                </ReservationTokens>
                            </SegmentInfo>
                        </Segments>
                    </Journey>
                </Journeys>
                <ChargeBreakdown currency = "GBP" totalAmount = "40.99000000">
                    <ChargeBreakdowns/>
                    <PaxBreakdowns>
                        <PaxBreakdown paxType = "ADT" amount = "40.99000000" taxes = "40.50000000" tasaDU = "0"/>
                    </PaxBreakdowns>
                </ChargeBreakdown>
                <PaxConfigurations>
                    <PaxConfiguration id = "0" paxRef = "0" age = "30" paxType = "ADT"/>
                </PaxConfigurations>
            </Itinerary>
        </Itineraries>
        <Passengers>
            <Passenger
                passengerType = "MR"
                name = "TestNom"
                surname = "TestApe"
                birthDate = "1984-03-17T00:00:00+01:00"
                codeDCO = "0"
                documentType = "NATIONAL_ID"
                documentId = "44183932N"
                documentExpiration = "2014-03-17T17:24:46.1611924+01:00"
                nationality = "ESP">
            </Passenger>
        </Passengers>
        <Client passengerType = "MR" name = "TestNom" surname = "TestApe" eMail = "transportation@xmltravelgate.com" countryPrefix = "+34" telephone = "+34 858 275 617" mobilephone = "+34 858 275 617">
            <Address zipCode = "12159" countryCode = "es">
                <Street>C/ test, 28</Street>
                <City>test</City>
            </Address>
        </Client>
        <PaymentInfo paymentInfo = "CARD">
            <PaymentDatas>
                <PaymentData paymentType = "CARD">
                    <CardInfo provType = "VI" holder = "testnom1 testape1 testape2" number = "4444333322221111" cvv = "737" expirationMonth = "06" expirationYear = "2016"/>
                </PaymentData>
            </PaymentDatas>
        </PaymentInfo>
        <Locators>
            <Locator>
                <id>Logi123456</id>
            </Locator>
        </Locators>
    </ReservationRQ>



ReservationRQ Description 
=========================



| **Element** 				| **Number**	| **Typre**	| **Description**					|
| ------------------------------------- | ------------- | ------------- | ----------------------------------------------------- |
| ReservationRQ                  	| 1  		|    		| Root node.                          			|
| Itineraries                    	| 1  		|    		| List of Itineraries.                			|
| Itineraries/Itinerary          	| 1..n 		|    		| Details of the Itinerary.           			|
| @id                       		| 1  		| Integer 	| Unique identifier of the Itinerary. 			|
| @fareRef                  		| 1  		| Integer 	| Reference identifier to the original Fare. Flights parameter.     |
| @HasObFees                		| 1  		| Boolean 	| If true then there is an extra fee for using credit card. |
| @carrier                  		| 1  		| String 	| Validating carrier. Flights parameter.        	|
| Itineraries/Itinerary/Journeys 	| 0..1 		|    		| Contains a list of Journeys.        			|	
| Itineraries/Itinerary/Journeys /Journey | 0..n 	|    		| Contains details of the Journeys.   			|
| @id                       		| 1  		| Integer 	| Unique identifier of the Journey in scope.		|
| @duration                 		| 1  		| Integer 	| Duration of the Journey in minutes. 			|
| Itineraries/Itinerary/Journeys /Journey/Segments | 0..1 |    		| Contains a list of Segments associated to the Journey.   |
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment | 0..n |    	| Contains details of the SegmentInfo.             	|
| @id                       		| 1  		| Integer 	| Unique SegmentInfo identifier.      			|
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /SegmentInfo | 0..n |    | Contains information of the SegmentInfo.  |
| @id                       		| 1  		| Integer 	| Unique identifier of the SegmentInfo.           	|
| @transportationId         		| 1  		| String 	| Unique Id of the transportation.    			|
| @transportationType       		| 1  		| String 	| Transport type: F ( Flight ), T ( Train ), B ( Bus ) & F ( Ferry ).  |
| @operatinCarrier          		| 1  		| String 	| Company which operates the transportation.         	|
| @marketingCarrier         		| 1  		| String 	| Company which commercializes the transportation.    	|
| @departureTerminal        		| 1  		| String 	| Departure terminal.                 			|	
| @arrivalTerminal          		| 1  		| String 	| Arrival terminal.                   			|
| @departureDate            		| 1  		| Date 		| Departure date.                     			|
| @arrivalDate              		| 1  		| Date 		| Arrival date.                       			|
| @segmentDuration          		| 1  		| Integer 	| Transport duration ( in minutes ).  			|
| @planeType                		| 1  		| String 	| Plane type. Flights parameter.      			|
| @maxCheckinDate           		| 1  		| String 	| Maximum date to make the check-in.  			|
| @segmentStatus            		| 1  		| String 	| SegmentInfo status: HK (OK), TK (Change of programming), UC (Unconfirmed), UN( Unable), NO (No action taken) & UD (Undefined).    |
| @hasTechnicalStop         		| 1  		| Boolean 	| If true, the SegmentInfo has a technical stop.      	|
| @electronicTicket         		| 1  		| Boolean 	| If true, the SegmentInfo uses a electronic ticket.    |
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /SegmentInfo/OriginLoc | 1  |    | Origin location.                    |
| @type                     		| 1  		| String 	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).    |
| @code                     		| 1  		| String 	| Location code.                      			|
| @cityCode                 		| 1  		| Boolean 	| If true, the field code indicates a city code, if false, it will indicate an airport code. |
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /SegmentInfo/DestinationLoc | 1  |    | Destination location.       |
| @type                     		| 1  		| String 	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).     |
| @code                     		| 1  		| String 	| Location code.                      			|
| @cityCode                 		| 1  		| Boolean 	| If true, the field code indicates a city code, if false, it will indicate an airport code. |
| Transportation/Segments /Segment/TechnicalStops | 0..1 |    		| Contains a list of TechnicalStops.  			|
| @totalTechnicalStops      		| 1  		| Integer 	| Total number of TechnicalStops.     			|
| Transportation/Segments /Segment/TechnicalStops /TechnicalStop | 1..n |    | Contains the details of the TechnicalStop.       |
| @location                 		| 1  		| String 	| TechnicalStop location.             			|
| @stopDate                 		| 1  		| Date 		| Approx. stop date and time.         			|
| @departureDate            		| 1  		| Date 		| Approx. departure date and time.    			|
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /SegmentClasses | 0..1 |    | Contains a list of SegmentClasses.  	|
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /SegmentClasses/SegmentClass | 0..n |    | Contains details of the SegmentClass.       |
| @cabinClass               		| 1  		| String 	| Cabin class of the seat: N (Not specified), Y (Tourist), C (Business), F (First), CA (Cabin, only for ferries), YP (Tourist Plus).    |
| @class                    		| 1  		| String 	| Fare class.                         			|
| @paxRef                   		| 1  		| Integer 	| Reference for the Passenger which is using this fare in the transport.   |
| @fareBasis                		| 1  		| String 	| Fare basis.                         			|
| @fareType                 		| 1  		| String 	| Fare type: PUB ( Public ), PRI ( Private ), NEGO ( Negotiated ) &  CORP ( Corporate ).    |
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /ReservationToken | 0..1 |    | Contains specific attributes of each provider.  |
| Itineraries/Itinerary/Journeys /Journey/Segments/Segment /ReservationToken/Attribute | 0..n |    | Contains details of the attribute.  |
| @id                       		| 1  		|    		| Keyword or id to identify a parameter.       	|
| @value                    		| 1  		|    		| Value of the parameter.             		|
| Itineraries/Itinerary/AmountBreakdown | 1  		|    		| Contains details of the AmountBreakdown.      |
| @currency                 		| 1  		| String 	| Currency code of the fare.          		|
| @totalAmount              		| 1  		| Decimal 	| Total amount. with taxes and other charges included. |
| @notCommissionableAmount  		| 1  		| Decimal 	| Total amount that can not be commissioned.        |
| @commission               		| 1  		| Decimal 	| Commission.                        		|
| Itineraries/Itinerary /AmountBreakdown/ChargeBreakdowns  | 0..1 |    	| Contains a list of ChargeBreakdowns.                 |
| Itineraries/Itinerary /AmountBreakdown/PaxBreakdowns | 0..1 |    	| Contains a list of breakdown amounts for each Passenger ( ADT amount, etc. ).      |
| Itineraries/Itinerary /AmountBreakdown/PaxBreakdowns /PaxBreakdown | 0..n |    | Contains details of breakdown amounts for each Passenger. |
| @paxType                  		| 1  		| String 	| Passenger type: ADT ( Adult ), CHD ( Child ) & INF ( Infant ).  |
| @amount                   		| 1  		| Decimal 	| Total amount, with taxes included, associated to the Passenger. |
| @taxes                    		| 1  		| Integer 	| If they exist, taxes are applied for this Passenger type.   |
| @tasaDU                   		| 1  		| Integer 	| Deprecated.                          |
| Itineraries/Itinerary /PaxConfigurations | 1  	|    		| Contains a list of PaxConfigurations.                 |
| Itineraries/Itinerary /PaxConfigurations/PaxConfiguration | 1  |    	| Contains details of the PaxConfiguration.             |
| @id                       		| 1  		| Integer 	| Unique identifier of the PaxConfiguration.           |
| @paxRef                   		| 1  		| Integer 	| Reference to the Passenger Id from the request. |
| @age                      		| 1  		| Integer 	| Age of the Passenger.               |
| @paxType                  		| 1  		| String 	| Passenger type based on the age of the Passenger: ADT (Adult), CHD (Child), INF (Infant), YOU (Young) and SEN (Senior). |
| @code                     		| 1  		| String 	| String with the PTC code.           |
| Passengers                     	| 1  		|    		| Contains a list of Passengers.      |
| Passengers/Passenger           	| 1..n 		|	    	| Contains information of the Passenger.         |
| @passengerType            		| 1  		| String 	| Treatment: MR, MRS, CHD and INF.    |
| @name                     		| 1  		| String 	| Name of the Passenger.              |
| @surname                  		| 1  		| String 	| Surname/s of the Passenger.         |
| @bithDate                 		| 1  		| String 	| Date of birth.                      |
| @codeDCO                  		| 1  		| String 	| Document code.                      |
| @documentType             		| 1  		| String 	| NATIONAL_ID, PASSPORT, RESIDENT_ID.              |
| @documentId               		| 1  		| String 	| Unique identifier of the documentation.           |
| @documentExpiration       		| 1  		| String 	| Expiration date of the documentation.             |
| @nationality              		| 1  		| String 	| Nationality.                        |
| Passengers/Passenger/PaxBonusDetails 	| 1  		|    		| Contains details of the Passenger bonus.  |
| Passengers/Passenger/PaxBonusDetails /AppliedBonuses | 1  |    	| Contains details of the applied bonus.    |
| @resident                 		| 1  		| String 	| Resident.                           |
| @largeFamily              		| 1  		| String 	| Large family discount: N (none), F1 (5% discount) and F2 (10% discount). |
| @discountCard             		| 1  		| String 	| Discount card.                      |
| Client                         	| 1  		|    		| Contains client's information.      |
| @passengerType            		| 1  		| String 	| Treatment.                          |
| @name                     		| 1  		| String 	| Name.                               |
| @surname                  		| 1  		| String 	| SurName.                            |
| @eMail                    		| 1  		| String 	| eMail address.                      |
| @countryPrefix            		| 1  		| String 	| Country telephone prefix.           |
| @telephone                		| 1  		| String 	| Telephone.                          |
| @mobilephone              		| 1  		| String 	| Mobilephone Telephone.              |
| Client/Address                 	| 1  		|    		| Contains the client's address.      |
| @zipCode                  		| 1  		| String 	| Zip code.                           |
| @countryCode              		| 1  		| String 	| Country code.                       |
| Client/Address/Street          	| 1  		| String 	| Contains the street name of the address.    |
| Client/Address/City            	| 1  		| String 	| Contains the locality.              |
| PaymentInfo                    	| 1  		|    		| Contains the information of the payment.     |
| @paymentInfo              		| 1  		| String 	| Payment type.                       |
| PaymentInfo/PaymentDatas       	| 1  		|    		| Contains a list of payment data.    |
| PaymentInfo/PaymentDatas /PaymentData | 1  		|    		| Contains details of the payment data.    |
| @paymentType              		| 1  		| String 	| Payment type: CASH, CARD and EMIT.  |
| PaymentInfo/PaymentDatas /PaymentData/CardInfo | 1  	|    		| Contains details of the credit card.     |
| @provType                 		| 1  		| String 	| Card type.                          |
| @holder                   		| 1  		| String 	| Holder.                             |
| @number                   		| 1  		| String 	| Credit card number.                 |
| @cvv                      		| 1  		| String 	| Verification code.                  |
| @expirationMonth          		| 1  		| String 	| Expiration month.                   |
| @expirationYear           		| 1  		| String 	| Expiration year.                    |
| Locators                       	| 1  		|    		| Contains a list of locators.        |
| Locators/Locator               	| 1  		|    		| Contains details of the locator.    |
| Locators/Locator/Id            	| 1  		| String 	| Unique identifier of the locator.   |
| Locators/Locator/Type          	| 1  		| String 	| Locator type: PROVIDER, TFBOOKINGREFERENCE, UNIVERSAL, EMISSION and CARRIER.             |




ReservationsRS Example
=====================
 

    <ReservationsRS>
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
                Sexo = "72"
                resident = "NO_VERIFICADO">
            </Passenger>
        </Passengers>
        <Locators>
            <id>KENHSR</id>
            <Type>PROVEEDOR</Type>
        </Locators>
        <Locators>
            <id>225901#</id>
            <Type>TFBOOKINGREFERENCE</Type>
        </Locators>
        <Invoice>
            <AmountBreakdown currency = "GBP" totalAmount = "40.99000000">
                <ChargeBreakdowns/>
                <PaxBreakdowns>
                    <PaxBreakdown paxType = "ADT" amount = "40.99000000"/>
                </PaxBreakdowns>
            </AmountBreakdown>
        </Invoice>
    </ReservationsRS>



ReservationsRS Description
==========================
 


| **Element**				| **Number**	| **Type**	| **Description**						|
| ------------------------------------- | ------------- | ------------- | ------------------------------------------------------------- |
| ReservationsRS                	| 1    		|		| Root node.							|
| Passengers                    	| 1    		|		| Contains a list of Passengers.				|
| Passengers/Passenger          	| 1..n   	|		| Contains information of the Passenger.			|
| @passengerType           		| 1 		| String	| Treatment: MR, MRS, CHD and INF.				|
| @name                    		| 1 		| String	| Name of the Passenger.					|
| @surname                 		| 1 		| String	| Surname/s of the Passenger.					|
| @bithDate                		| 1 		| String	| Date of birth.						|
| @codeDCO                 		| 1 		| String	| Document code.						|
| @documentType            		| 1 		| String	| Documentation type.						|
| @documentId              		| 1  		| String	| Unique identifier of the documentation.			|
| @documentExpiration      		| 1 		| String	| Expiration date of the documentation.				|
| @nationality             		| 1 		| String	| Nationality.							|
| Locators                      	| 1    		|		| Contains a list of locators.					|
| Locators/Locator              	| 1    		|		| Contains details of the locator.				|
| Locators/Locator/Id           	| 1 		| String	| Unique identifier of the locator.				|
| Locators/Locator/Type         	| 1 		| String	| Locator type: PROVIDER, TFBOOKINGREFERENCE, UNIVERSAL, EMISSION and CARRIER.	|
| Invoice                       	| 1     	|		|								| 
| Invoice/AmountBreakdown       	| 1     	|		|								|
| @currency                		| 1 		| String	| Currency code of the fare.					|
| @totalAmount             		| 1 		| Decimal	| Total amount. with taxes and other charges included.		|
| @notCommissionableAmount 		| 1 		| Decimal	| Total amount that can not be commissioned.			|
| @commission              		| 1 		| Decimal	| Commission.							|
| Invoice/AmountBreakdown /ChargeBreakdowns | 0..1   	|		| Contains a list of ChargeBreakdowns.				|
| Invoice/AmountBreakdown /PaxBreakdowns | 0..1   	|		| Contains a list of breakdown amounts for each Passenger ( ADT amount, etc. ).	|
| Invoice/AmountBreakdown /PaxBreakdowns/PaxBreakdown | 0..n |  	| Contains details of breakdown amounts for each Passenger.	|
| @paxType                 		| 1 		| String	| Passenger type: ADT ( Adult ), CHD ( Child ) & INF ( Infant ). |
| @amount                   		| 1  		| Decimal	| Total amount, with taxes included, associated to the Passenger. |
| @taxes                   		| 1 		| Integer	| If they exist, taxes are applied for this Passenger type. 	|
| @tasaDU                  		| 1 		| Integer	| Deprecated.							|



