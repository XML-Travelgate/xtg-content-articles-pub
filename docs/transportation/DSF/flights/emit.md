---
title: Emit
keywords: transportation, data structure, flights, emit
search: Transportation - Flights - Data Structure - Emit
sidebar: mydoc_sidebar
permalink: /docs/transportation/DSF/flight/emit
---

### Method Goals

This method aims to issue the tickets.


### Request Format

The request indicate the booking locator and the issue type (which tickets have to be issued: all, only passengers, only extras). 


### Response Format

The result returns a list of Locators (booking codes). It can be the
supplier's or the one sent in the request. It also returns all the
charges associated to the booking, the passengers and the tickets issued (if any).

### Remarks

Not all suppliers need to issue the tickets. For some suppliers, the payment info is mandatory.


### EmitRQ Description


| **Element**						| **Number**| **Type**	| **Description**													|
| --------------------------------- | --------- | ----------|------------------------------------------------------------------	|
| EmitRQ							| 1			|			| Root node.|
| @locator							| 1			| String	| Provider's locator from which the tickets will be emited.|
| EmissionType						| 1			|			| Contains the type of emission.|
| @type								| 1			|[Issue type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#issue-type)|Issue type|
| PaymentInfo						| 0..1  	|    		| Contains the information of the payment.|
| @paymentType						| 1  		|[Payment type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#payment-type)|Payment type|
| PaymentInfo/PaymentDatas       	| 0..1  	|    		| Contains a list of payment data.|
| PaymentInfo/PaymentDatas/<br>PaymentData					| 1..n  || Contains details of the payment data.|
| @paymentType              		| 1  		|[Payment type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#payment-type)|Payment type|
| PaymentInfo/PaymentDatas/<br>PaymentData/CardInfo			| 1  	|| Contains details of the debit/credit card.|
| @provType                 		| 1  		| String 	| Card type (provider format, for instance MC -> MasterCard). Each provider configuration indicates the available card type formats.|
| @number                   		| 1  		| String 	| Card number.|
| @expirationMonth          		| 1  		| String 	| Expiration month.|
| @expirationYear           		| 1  		| String 	| Expiration year.|
| @holder                   		| 0..1  	| String 	| Holder.|
| @cvv                      		| 0..1  	| String 	| Verification code.|
| PaymentInfo/PaymentDatas/<br>PaymentData/InstalmentsNumber | 0..1  	|| Number of instalments.|
| PaymentInfo/PaymentDatas/<br>PaymentData/Amount			| 0..1  	|| Contains a list of Amount.|
| PaymentInfo/PaymentDatas/<br>PaymentData/Amount/<br>Amount| 1..n  	|| Amount by type. It is used to specify for example the Service Fees associated to a credit card.|
| @currency           				| 1  		| String 	| Currency.|
| @amount           				| 1  		| Decimal 	| Amount.|
| @amountType           			| 0..1  	| [Amount type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#amount-type)  	| Amount Type.|



### EmitRS Description

| **Element**						| **Number**| **Type**	| **Description**													|
| --------------------------------- | --------- | ----------|------------------------------------------------------------------	|
| EmitRS							| 1			|			| Root node.|
| Passengers						| 0..1  	|    		| Contains a list of Passengers.|
| Passengers/Passenger				| 1..n 		|			| Contains information of the Passenger.|
| @id								| 1  		| Integer	| Unique identifier of the passenger.|
| @title							| 1  		|[Title type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#title-type)|Title type|
| @name								| 1  		| String 	| Name of the Passenger.|
| @surname        					| 1  		| String 	| Surname/s of the Passenger.|
| @bithDate							| 1  		| Date 		| Date of birth. Example: 2019-04-15T18:25:00|
| @codeDCO     						| 0..1  	| Integer 	| Consolidate document number.|
| @documentType						| 0..1  	|[Document type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#document-type)|Document type.|
| @documentId						| 0..1  	| String 	| Unique identifier of the documentation.|
| @documentExpiration  				| 0..1		| Date 		| Expiration date of the documentation. Example: 2019-04-15T18:25:00|
| @documentExpedition  				| 0..1		| Date 		| Expedition date of the documentation. Example: 2019-04-15T18:25:00|
| @nationality						| 0..1  	| String 	| Nationality. ISO 3166-1 Alpha-2 Code|
| @gender							| 0..1  	| Char		| Gender.|
| @language							| 0..1  	| String 	| Language. ISO 3166-1 alpha-2 format lowercase.|
| Passengers/Passenger/PaxBonusDetails 						| 0..1  || Contains details of the Passenger bonus.|
| Passengers/Passenger/PaxBonusDetails/<br>AppliedBonuses	| 0..1  || Contains details of the applied bonus.|
| @resident              			| 0..1 		|[Resident discount type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#resident-discount-type)|Resident discount type.|
| @largeFamily           			| 0..1 		|[Large Family discount type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#large-family-discount-type)|Large family discount type|
| @discountCardCode					| 0..1		| String	| Discount card code.|
| @discountCard						| 0..1		|[Discount Card type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#discount-card-type)|Discount card type.|
| Passengers/Passenger/PaxBonusDetails/<br>AppliedBonuses/DiscountCards	| 0..1	|| Contains a list of DiscountCards.|
| Passengers/Passenger/PaxBonusDetails/<br>AppliedBonuses/DiscountCards/<br>DiscountCard| 1..n || DiscountCard details.|
| @type								| 1			|[Discount Card type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#discount-card-type)|Discount card type.|
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
| @type								| 1  		|[Discount type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#discount-type)|Discount type|
| @status							| 1  		|[Discount status type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#discount-status)|Discount status|
| @numAttempts						| 0..1  	| String 	| Number of retry attempts for spanish resident validation.|
| @code								| 0..1  	| String 	| Discount/Bonus associated code provided by the supplier.|
| Passengers/Passenger/SpecialPetitions						| 0..1	|| Contains information of the bags, seats or other supplements requested by the passenger.|
| Passengers/Passenger/SpecialPetitions/<br>NumSuitcases	| 0..1	|| Number of bags requested by the passenger.|
| Passengers/Passenger/SpecialPetitions/<br>PaxBaggageInfos | 0..1	|| Contains a list of PaxBaggageInfo.|
| Passengers/Passenger/SpecialPetitions/<br>PaxBaggageInfos/PaxBaggageInfo | 1..n	|| Specifies the luggage of the passenger.|
| @type								| 1  		|[Baggage type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#baggage-type)|Baggage type|
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
| @type								| 1  		|[Optional Element type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#optional-element-type)|Optional element type|
| @specialSupplementType			| 1			|[Special Supplement type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#special-supplement-type)|Special supplement type|
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
| @appliesFixAmount					| 0..1 		|  [Amount Applies To Type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#amount-applies-to-type)	| The fixes amount application|
| @minFixAmount             		| 0..1 		| Decimal	| Minimal fixed amount.|
| @maxFixAmount             		| 0..1 		| Decimal	| Maximal fixed amount.|
| @minAmountPercentage             	| 0..1 		| Decimal	| Minimal percentage amount.|
| @maxAmountPercentage             	| 0..1 		| Decimal	| Maximal percentage amount.|
| @percentage             			| 0..1 		| Decimal	| Total percentage amount.|
| @percentageApplied             	| 0..1 		| [Amount Applies To type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#amount-applies-to-type)	| The percentage amount application.|
| Passengers/Passenger/SpecialPetitions/<br>Seating			| 0..1    	|| Seating availability.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/BlockRules    | 0..1    	|| Contains a list of Block Rules.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/BlockRules/BlockRule 		| 1..n    	|| Block Rules.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/BlockRules/BlockRule/References | 1    	|| References for the Block Rule.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/BlockRules/BlockRule/References/<br>BlockReferences		| 1	||	Contains a list of references to block elements.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/BlockRules/BlockRule/References/<br>BlockReferences/BlockReference | 1..n || Block element reference.|
| @blockTypeRef						| 1  		| [Block Type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#block-type)	| Block type: CABIN (The entire cabin of the plane).|
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
| @amountType             			| 0..1  	| [Amount type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#amount-type) 	| Amount type.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/Blocks  | 1    	|| Contains a list of seating blocks.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/Blocks/Block    | 1..n    	|| Seating details.|
| @type								| 1  		| [Block Type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#block-type)	| Block type: CABIN (The entire cabin of the plane).|
| @id								| 1  		| Integer	| Unique id.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/Blocks/Block/References/<br>SegmentReferences		| 1	||	Contains a list of segment references for the Block.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/Blocks/Block/References/<br>SegmentReferences/SegmentReference		| 1..n	||	Segment reference.|
| @itineraryRef						| 1 		| Integer	| Unique identifier of the Itinerary.|
| @journeyRef						| 1 		| Integer	| Unique identifier of the Journey.|
| @segmentRef						| 1 		| Integer	| Unique identifier of the Segment.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/Blocks/Block/Blocks | 1    	|| Contains a list of row blocks.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/Blocks/Block/Blocks/Block 	| 1..n    	|| Row block.|
| @type    							| 1  		| [Block Type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#block-type)	| Block type: ROW|
| @id     							| 1  		| Integer	| Unique row id.|
| @number							| 1  		| Integer	| Row number in the cabin.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/Blocks/Block/Blocks/Block/<br>Blocks | 1    	|| Contains a list of seat blocks.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/Blocks/Block/Blocks/Block/<br>Blocks/Block | 1..n  || Seat block.|
| @type								| 1  		| [Block Type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#block-type)	| Block type: SEAT.|
| @id								| 1  		| Integer	| Unique seat id.|
| @number    						| 1  		| String	| Seat identifier.|
| @token    						| 0..1  	| String	| Reservation seat token.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/Blocks/Block/Blocks/Block/<br>Blocks/Block/Availability | 0..1 || Availability of the seat.|
| @isAvailable						| 1  		| Boolean	| Indicates whether the seat is available.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/Blocks/Block/Blocks/Block/<br>Blocks/Block/BlockAttributes | 0..1 || Contains a list of Seat attributes.|
| Passengers/Passenger/SpecialPetitions/<br>Seating/Blocks/Block/Blocks/Block/<br>Blocks/Block/BlockAttributes/<br>BlockAttribute | 1..n |  | Seat attribute.|
| @type                   			| 1  		|[Block Attribute Type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#block-attribute-type) | Block Attribute type|
| Locator               			| 1..n  	|    		| Contains details of the locator.|
| Locator/Id            			| 1  		| String 	| Unique identifier of the locator.|
| Locator/Type          			| 1  		| [Locator type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#locator-type)| The locator's type	| 
| Tickets							| 1			|			|Contains a list of tickets associated to the booking.|
| Tickets/Ticket					| 1..n		|			| Contains the details of the ticket.|
| @ticketNum						| 1			| String	| Ticket number.|
| @type								| 1			|[Ticket Type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#ticket-type) | Ticket type|
| @status							| 1			|[Ticket Status type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#ticket-status-type)|Ticket Status type|
| @id								| 0..1		| Integer	| Unique identifier of the ticket.|
| @paxName							| 0..1		| String	| Passenger name.|
| @paxType							| 0..1		|[Passenger type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#passenger-type)|Passenger type based on the age of the passenger.|
| @url								| 0..1		| String	| Url.|
| Tickets/Ticket/PNRLoc				| 0..1		|			| Provider Locator associated to a Booking.|
| @code								| 1			| String	| Locator code.|
| Invoice							| 0..1		|			| Detailed pricing information.|
| @carrier							| 0..1		| String	| Fare carrier.|
| @agencyCode						| 0..1		| String	| Agency code.|
| @instalmentsNumber					| 0..1		| Integer	| Number of instalments in which the amount will be charged to the credit card.|
| @lastTicketingDateUTC				| 0..1		| Date		| Maximum date allowed to make the ticket emission (in UTC format if filled)|
| Invoice/AmountBreakdown			| 1			|			| Breakdown of the fare amount.|
| @currency              			| 1 		| String	| Currency code of the fare.|
| @totalAmount           			| 1 		| Decimal	| Total amount. with taxes and other charges included.	|
| @notCommissionableAmount			| 0..1 		| Decimal	| Total amount that can not be commissioned.|
| @commission            			| 0..1 		| Decimal	| Commission.|
| Invoice/AmountBreakdown/<br>ChargeBreakdowns				| 0..1   || Contains a list of breakdown amounts ( taxes, mandatory charges.. ).|
| Invoice/AmountBreakdown/<br>ChargeBreakdowns/<br>ChargeBreakdown | 1..n || Contains details of the BreakdownAmount.|
| @amount                			| 1    	 	| Decimal	| Charge amount.|
| @type                  			| 0..1 		| [Type of charge.](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#charge-type) | Type of charge. |
| @included							| 0..1		| Boolean	| If true, the charge is included to the total fare amount.|
| Invoice/AmountBreakdown/<br>ChargeBreakdowns/<br>ChargeBreakdown/Concept | 0..1 || Contains details of the charge.|
| @id                    			| 0..1 		| String	| Unique id of the Concept.|
| @language              			| 0..1 		| String	| Language. ISO 3166-1 alpha-2 format lowercase.|
| @carrier              			| 0..1 		| String	| Carrier.|
| @code              				| 0..1 		| String	| Concept code.|
| Invoice/AmountBreakdown/<br>ChargeBreakDowns/<br>ChargeBreakdown/Concept/Text | 0..1 | String | Remarks|
| Invoice/AmountBreakdown/<br>ChargeBreakDowns/<br>ChargeBreakdown/Concept/Paragraph | 0..n || Contains a list of Sentences and titles.|
| @title							| 0..1		| String	| Title.|
| Invoice/AmountBreakdown/<br>ChargeBreakDowns/<br>ChargeBreakdown/Concept/Paragraph/<br>Sentence | 0..n | String | Sentence|
| Invoice/AmountBreakdown/<br>PaxBreakdown					| 1    || Contains a list of breakdown amounts for each passenger ( ADT amount, etc. ).|
| Invoice/AmountBreakdown/<br>PaxBreakdowns/<br>PaxBreakdown| 1..n || Contains details of breakdown amounts for each passenger.|
| @paxType               			| 1 		|[Passenger type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#passenger-type)|Passenger type|
| @amount                			| 1 		| Decimal	| Total amount, with taxes included, associated to the passenger.|
| @taxes                 			| 1 		| Decimal	| If they exist, taxes are applied for this passenger type.|
| @taxesDU                			| 0..1 		| Decimal	| DU taxes.|
| @fees                				| 0..1 		| Decimal	| Fees.|
| Invoice/AmountBreakdown/<br>PaxBreakdowns/PaxBreakdown/<br>Taxes | 0..1 || Contains a list of Taxes.|
| Invoice/AmountBreakdown/<br>PaxBreakdowns/PaxBreakdown/<br>Taxes/Tax | 1..n || Code and amount of each tax.|
| @code								| 1			| String	| Code.|
| @amount							| 1			| Decimal	| Amount.|


### EmitRQ Example

~~~xml
<EmitRQ>
</EmitRQ>
~~~