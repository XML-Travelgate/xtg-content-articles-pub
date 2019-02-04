---
title: Reservation
keywords: transportation, data structure, flights, reservation
search: Transportation - Flights - Data Structure - Reservation
sidebar: mydoc_sidebar
permalink: /docs/transportation/DSF/flights/reservation
---



### Method Goals


This method aims to book one or more Itineraries.



### Request Format


The request format works the same way as the Valuation request. It can
work with one or with two Itineraries. The request will also contain a
list of Passengers and the PaymentInfo, such as payment method.



### Response Format


The result returns a list of Locators (booking codes). It can be the
supplier's or the one sent in the request. It also returns all the
charges associated to the booking.



### Remarks


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


### ReservationRQ Description 




| **Element** 				| **Number**	| **Typre**	| **Description**					|
| ------------------------------------- | ------------- | ------------- | ----------------------------------------------------- |
| ReservationRQ                  	| 1  		|    		| Root node.                          			|
| Itineraries                 		| 1     	|		| Contains a list of Itineraries.|
| Itineraries/Itinerary       		| 1..n    	|		| Details of the Itinerary.|
| @id                    		| 1 		| Integer	| Unique identifier of the Itinerary.|
| @fareRef	               		| 1 		| String	| Reference identifier to the original Fare.|
| @hasObFees             		| 1 		| Boolean	| If true then there is an extra fee for using credit card.|
| @carrier               		| 1 		| String	| Validating carrier.|
| Itineraries/Itinerary/Conditions	| 0..1 |	| Contains a list of Fare Conditions. |
| Itineraries/Itinerary/Conditions/Condition	| 1..n |	| Contains details of the Condition that applies to the condition. |
| @cia	| 0..1	| String	| Carrier applying the condition.	|
| @code	| 0..1	| String	| Code of the condition.	|
| @id	| 1	| String	| Unique id of the condition.	|
| @language	| 1	| String	| Language in which the condition is written.	|
| @Text | 0..1	| String	| Description of the condition.	|
| Transportation/Fares/Fare/Conditions/<br>Condition/Paragraph	| 0..n | | List of Sentences and titles. |
| @title | 0..1	| String	| Title content.	|
| Transportation/Fares/Fare/Conditions/<br>Condition/Paragraph/Sentence	| 0..n | String	| List of Sentences contents. |
| Itineraries/Itinerary/Journeys	| 1    	|		| Contains a list of Journeys.|
| Itineraries/Itinerary/Journeys/Journey | 1..n    	|		| Contains details of the Journeys.|
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
| @transportationName    		| 0..1 		| String	| Name of the transportation.	|
| @transportationCode	| 0..1	| String	| Code of the transportation. |
| @operatingCarrier      		| 1 		| String	| Company which operates the transportation.		|
| @marketingCarrier      		| 1 		| String	| Company which commercializes the transportation.	|
| @departureTerminal     | 0..1 		| String	| Departure terminal.|
| @arrivalTerminal       		| 0..1 		| String	| Arrival terminal.|
| @departureDate         		| 1 		| Date		| Departure date.|
| @arrivalDate           		| 1 		| Date		| Arrival date. |
| @segmentDuration       		| 0..1 		| Integer	| Transport duration ( in minutes ).|
| @segmentStatus	| 1	| String	| Segment status: HK (Holding confirmed), TK(Confirming new flight times), UC(Unable to confirm), UN(Flight cancelled by airline), NO (No action taken), UD (Undefined). |
| @planeType | 0..1 		| String	| Plane type. Flights parameter.|
| @maxCheckinDate     | 0..1 		| String	| Maximum date to make the check-in.|
| @hasTechnicalStop   | 1 | Boolean	| If true, the segment has a technical stop. 		|
| @electronicTicket      		| 1 		| Boolean	| If true, the segment uses a electronic ticket. 	| 
| @secureFlight          		| 1		| Boolean	| If true, the provider requires extra information of the passengers. Flights parameter.	|
| Transportation/Segments/Segment/OriginLoc | 1     	|		| Origin location.					|
| @type                  		| 1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).	|
| @code                  		| 1 		| String	| Location code.					|
| @name	| 0..1 		| String	| Location full name.	|
| @radius					| 0..1			| Integer	| Area radius from location.|
| @cityCode              		| 1 		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.	|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/OriginLoc/<br>AlternativeLocations	| 0..1		|	| Contains a list of AlternativeLocations.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/OriginLoc/<br>AlternativeLocations/AlternativeLocation	| 1..n	|	| Contains the information of the alternative location.|
| @code						| 1			| String	| Location code.|
| @cityCode        			| 1  		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.|
| @name						| 0..1			| String	| Location long name.|
| @type						| 1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/DestinationLoc | 1   |  		| Destination location.					|
| @type  | 1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).	|
| @code                  		| 1 		| String	| Location code. 					|
| @name	| 0..1 		| String	| Location full name.	|
| @radius					| 0..1			| Integer	| Area radius from location.|
| @cityCode              		| 1 		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.	||
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/<br>DestinationLoc/AlternativeLocations	| 0..1		|	| Contains a list of AlternativeLocations.
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/<br>DestinationLoc/AlternativeLocations/<br>AlternativeLocation	| 1..n	|	| Contains the information of the alternative location.|
| @code						| 1			| String	| Location code.|
| @cityCode        			| 1  		| Boolean	| If true, the field code indicates a city code, if false, it will indicate an airport code.|
| @name						| 0..1			| String	| Location long name.|
| @type						| 1 		| String	| Type of station of the location indicated with A ( AirPort ), T ( Train Station ) & P ( Port ).|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/TechnicalStops | 0..1 |   		| Contains a list of TechnicalStops.		|
| @totalTechnicalStops   | 1 		| Integer	| Total number of TechnicalStops.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/TechnicalStops/<br>TechnicalStop | 0..n | | Contains the details of the TechnicalStop.|
| @location          | 1 		| String	| TechnicalStop location.|
| @stopDate       | 1 		| Date		| Approx. stop date and time.|
| @departureDate    | 1 		| Date		| Approx. departure date and time.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses | 1 | | Contains a list of SegmentClasses.	|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses/<br>SegmentClass | 1..n | | Contains details of the SegmentClass.   |
| @cabinClass            		| 1 		| String	| Cabin class of the seat: N (Not specified), Y (Tourist), C (Business), F (First), CA (Cabin, only for ferries), YP (Tourist Plus).	|
| @class                 		| 1 		| String	| Fare class. |
| @paxRef               	 	| 1 		| Integer	| Passenger reference. 					|
| @fareBasis             		| 0..1 		| String	| Identifier of the fare.				|
| @fareType              		| 1 		| String	| Fare type: PUB ( Public ), PRI ( Private ), NEGO ( Negotiated ) and CORP ( Corporate ).	|
| @avail                 		| 0..1 		| Integer	| Available seats remaining for this class (In flights, the maximum is 9).  |
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses/<br>SegmentClass/Modifiable | 0..1 |  | Contains the information of the modifiable fare.	|
| @Description                 		| 0..1 		| String	| Modification description. |
| @amount                 			| 0..1 		| Decimal	| Modification amount. |
| @modifiable                 		| 1 		| Boolean	| If true, the fare allows this modification. |
| @currency                 		| 0..1 		| String	| Modification currency. |
| @amountType                 		| 1 		| String	| Modification amount type: AMOUNT (Fare amount), FEE (Fee amount), TOTAL (Total fare amount), PERCENTUAL (Percentual amount). |
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses/<br>SegmentClass/CancellationPolicies | 0..1 |  | Contains a list of CancellationPolicies.	|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/SegmentClasses/<br>SegmentClass/CancellationPolicies/<br>CancellationPolicy | 1..n |  |Contains details of the CancelationPolicy.	|
| @fromDate                 		| 0..1 		| Date	| Date of the begining of the policy. |
| @amount                 			| 0..1 		| Decimal	| Policy amount. |
| @refundable                 		| 1 		| Boolean	| If true, the fare allows the refundation. |
| @currency                 		| 0..1 		| String	| Policy currency. |
| @amountType                 		| 1 		| String	| Policy amount type: AMOUNT (Fare amount), FEE (Fee amount), TOTAL (Total fare amount), PERCENTUAL (Percentual amount).|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/ReservationTokens | 0..1 |  | Specific attribute used for each provider.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/ReservationTokens/<br>Attribute | 1..n |  | Type of attribute.|
| @key   | 1 		| String	| Contains the keyword/ Id to identify a parameter.	|
| @value     | 1 		| String	| Contains the value of the parameter.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/CheckinInformation | 0..1 |  | Checkin information.|
| @openingTime | 0..1 		| Date	| Checkin opening time.|
| @closingTime | 0..1 		| Date	| Checkin closing time.|
| @estimatedCheckinTime | 0..1 		| Date	| Estimated checkin time.|
| Itineraries/Itinerary/Journeys/Journey/<br>Segments/Segment/CheckinInformation/<br>Status | 0..1 |  | Status checkin information.|
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
| @cia              		| 0..1 		| String	| Carrier.			|
| @code              		| 0..1 		| String	| Concept code.			|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakDowns/ChargeBreakdown<br>/Concept/Text | 0..1 | String | Remarks.	|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakDowns/ChargeBreakdown<br>/Concept/Paragraph | 0..n |  | Contains a list of Sentences and titles.	|
| @title	| 0..1	| String	| Title.	|
| Itineraries/Itinerary/AmountBreakdown/<br>ChargeBreakDowns/ChargeBreakdown/<br>Concept/Paragraph/Sentence | 0..n | String | Sentence|
| Itineraries/Itinerary/AmountBreakdown/<br>PaxBreakdown | 1    	|		| Contains a list of breakdown amounts for each passenger ( ADT amount, etc. ).|
| Itineraries/Itinerary/AmountBreakdown/<br>PaxBreakdowns/PaxBreakdown | 1..n | 	| Contains details of breakdown amounts for each passenger.|
| @paxType               		| 1 		| String	| Passenger type: ADT ( Adult ), CHD ( Child ) & INF ( Infant ).|
| @amount                		| 1 		| Decimal	| Total amount, with taxes included, associated to the passenger.	|
| @taxes                 		| 1 		| Decimal	| If they exist, taxes are applied for this passenger type. |
| @tasaDU                		| 0..1 		| Decimal	| DU taxes. 						|
| @fees                			| 0..1 		| Decimal	| Fees. 						|
| Itineraries/Itinerary/AmountBreakdown/<br>PaxBreakdowns/PaxBreakdown/<br>Taxes | 0..1 | 	| Contains a list of Taxes.|
| Itineraries/Itinerary/AmountBreakdown/<br>PaxBreakdowns/PaxBreakdown/<br>Taxes/Tax | 1..n | 	| Code and amount of each tax.|
| @code				| 1	| String	| Code.	|
| @amount				| 1	| Decimal	| Amount.	|
| Itineraries/Itinerary/PaxConfigurations		| 1     	|		| Contains a list of PaxConfiguration.	|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration | 1..n |   		| Contains details of PaxConfiguration.	|
| @id                    		| 1 		| Integer	| Unique identifier of the PaxConfiguration. 		|
| @paxRef                		| 1 		| Integer	| Reference to the passenger Id from the request. 	|
| @age                   		| 0..1 		| Integer	| Age of the passenger. 				|
| @nacionality                   	| 0..1 		| String	| Nacionality of the passenger. 			|
| @paxType               		| 1 		| String	| Passenger type based on the age of the passenger: ADT (Adult), CHD (Child), INF (Infant), YOU (Young) and SEN (Senior).	|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses | 0..1 | | Applied discounts.			|
| @resident              	| 1 		| String	| [Resident discount type.](#valuation-enumerate-description)|
| @largeFamily           		| 1 		| String	| Family discount type: N(None), F1(Large family), F2 (Special large family). |
| @discountCardCode		| 0..1	| String	| Discount card code.|
| @discountCard		| 1	| String	| [Discount card type.](#valuation-enumerate-description)|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses/<br>DiscountCards	| 0..1	|	| Contains a list of DiscountCards.|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses/<br>DiscountCards/DiscountCard| 1..n	|	| DiscountCard details.|
| @code	| 0..1	| String | Discount card code.|
| @id	| 1	| String	| Unique identifier of discound card.|
| @type	| 1	| String	| [Discount card type.](#valuation-enumerate-description)|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses/<br>PaxTypeCodes		| 0..1	|		| Contains a list of PaxTypeCodes.|
| Itineraries/Itinerary/PaxConfigurations/<br>PaxConfiguration/AppliedBonuses/<br>PaxTypeCodes/PaxTypeCode	| 1..n	|	| Contains the code type of the passenger.|
| @code		| 1		| String	| Code type of the passenger.|
| Itineraries/Itinerary/Emissions	| 0..1	|	| Contains a list of Issuances.|
| Itineraries/Itinerary/Emissions/<br>Emission	| 1..n	|	| Contains the key of the Issuance.|
| @key		| 1		| String	| Key of the Issuance.|
| Passengers     | 1  		|    		| Contains a list of Passengers.|
| Passengers/Passenger   | 1..n 	|	  | Contains information of the Passenger.|
| @id    | 1  		| Integer | Unique identifier of the passenger.|
| @passengerType    | 1  		| String 	| Treatment: MR, MRS, CHD and INF.|
| @name            | 1  		| String 	| Name of the Passenger.|
| @surname        	| 1  		| String 	| Surname/s of the Passenger.|
| @bithDate      | 1  		| Date 	| Date of birth.|
| @codeDCO     	| 1  		| Integer 	| Consolidate document number.|
| @documentType    | 1  	| String 	| Document type: NATIONAL_ID, PASSPORT, RESIDENT_ID, FOREIGN_PASSPORT, BIRTH_NOTIFICATION.|
| @documentId     | 1  	| String 	| Unique identifier of the documentation.|
| @documentExpiration  	| 1 | Date 	| Expiration date of the documentation.|
| @documentExpedition  	| 1 | Date 	| Expedition date of the documentation.|
| @nationality   | 1  		| String 	| Nationality.|
| @gender   | 1  		| Char | Gender.|
| @language   | 1  		| String 	| Language.|
| Passengers/Passenger/PaxBonusDetails 	| 1  		|  | Contains details of the Passenger bonus.|
| Passengers/Passenger/PaxBonusDetails/<br>AppliedBonuses | 1  |    	| Contains details of the applied bonus.|
| Passengers/Passenger/PaxBonusDetails/<br>AppliedBonuses | 0..1 | | Applied discounts.			|
| @resident              	| 1 		| String	| [Resident discount type.](#valuation-enumerate-description)|
| @largeFamily           		| 1 		| String	| Family discount type: N(None), F1(Large family), F2 (Special large family). |
| @discountCardCode		| 0..1	| String	| Discount card code.|
| @discountCard		| 1	| String	| [Discount card type.](#valuation-enumerate-description)|
| Passengers/Passenger/PaxBonusDetails/<br>AppliedBonuses/DiscountCards	| 0..1	|	| Contains a list of DiscountCards.|
| Passengers/Passenger/PaxBonusDetails/<br>AppliedBonuses/DiscountCards/<br>DiscountCard| 1..n | | DiscountCard details.|
| @code	| 0..1	| String | Discount card code.|
| @id	| 1	| String	| Unique identifier of discound card.|
| @type	| 1	| String	| [Discount card type.](#valuation-enumerate-description)|
| Passengers/Passenger/PaxBonusDetails/<br>AppliedBonuses/PaxTypeCodes		| 0..1	|		| Contains a list of PaxTypeCodes.|
| Passengers/Passenger/PaxBonusDetails/<br>AppliedBonuses/PaxTypeCodes/<br>PaxTypeCode	| 1..n	|	| Contains the code type of the passenger.|
| @code		| 0..1		| String	| Code type of the passenger.|
| Passengers/Passenger/PaxBonusDetails/<br>ResidentCityCode	| 0..1	| String	| If required, city code for the Spanish Resident discount (070407, PALMA DE MALLORCA).|
| Passengers/Passenger/PaxBonusDetails/<br>LargeFamilyId | 0..1	| String	| Spanish family id.|
| Passengers/Passenger/PaxBonusDetails/<br>LargeFamilyCityCode | 0..1	| String	| City code for the Spanish Family discount (070407, Islas Baleares).|
| Passengers/Passenger/PaxBonusDetails/<br>ResidentCertificateId | 0..1	| String	| Resident certification number.|
| Passengers/Passenger/PaxBonusDetails/<br>DetailName | 0..1	|  | Passenger name expanded (more details).|
| Passengers/Passenger/PaxBonusDetails/<br>DetailName/name | 0..1	| String | Name.|
| Passengers/Passenger/PaxBonusDetails/<br>DetailName/firstSurname | 0..1	| String | First surname.|
| Passengers/Passenger/PaxBonusDetails/<br>DetailName/secondSurname | 0..1	| String | Second surname.|
| Passengers/Passenger/ | 0..1	| String | Second surname.|
| Client   	| 1  		|    		| Contains client's information.      |
| @passengerType   | 1  		| String 	| Treatment.                          |
| @name     | 1  		| String 	| Name.                               |
| @surname     | 1  		| String 	| SurName.                            |
| @eMail   | 1  		| String 	| eMail address.                      |
| @countryPrefix  	| 1  		| String 	| Country telephone prefix.           |
| @telephone   | 1  		| String 	| Telephone.                          |
| @mobilephone   | 1  		| String 	| Mobilephone Telephone.              |
| Client/Address 	| 1  		|    		| Contains the client's address.      |
| @zipCode   | 1  		| String 	| Zip code.                           |
| @countryCode   | 1  		| String 	| Country code.                       |
| Client/Address/Street  | 1  | String 	| Contains the street name of the address.   |
| Client/Address/City | 1  		| String 	| Contains the locality.              |
| PaymentInfo    | 1  		|    		| Contains the information of the payment.     |
| @paymentInfo  | 1  		| String 	| Payment type.                       |
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



### ReservationsRS Description

 
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



### ReservationRQ Example


~~~xml
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
~~~

### ReservationsRS Example

 
~~~xml
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
~~~