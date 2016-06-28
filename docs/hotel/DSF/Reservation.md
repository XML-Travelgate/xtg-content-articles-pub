---
title: Reservation
keywords: hotel, data structure, reservation
sidebar: mydoc_sidebar
permalink: /docs/hotel/DSF/Reservation
---



### Method Goals


This method aims to book an option.



### Request Format


The request format works the same way as *Valuation* but
with the list of passengers.



### Response Format


The result returns the booking locator (booking code), which could be the
supplier's own code or the one sent in request.



It also returns all the charges associated with the booking as well as its status.



### Remarks


**180000** milliseconds is the maximum amount of time permitted in our system before the connection
is closed. 



### ReservationRQ Example


~~~xml
    <ReservationRQ>
        <ClientLocator>2537459</ClientLocator>
        <OnRequest>false</OnRequest>
        <Parameters>
            <Parameter key = "extra" value = "31"/>
        </Parameters>
        <DeltaPrice amount="10" percent="5" applyBoth="false"/>
        <StartDate>28/01/2014</StartDate>
        <EndDate>29/01/2014</EndDate>
        <MealPlanCode>D</MealPlanCode>
        <HotelCode>10</HotelCode>
        <Nationality>ES</Nationality>
        <Price currency = "EUR" amount = "36.20" binding = "false" commission = "-1"/>
        <ResGuests> 
            <Guests>
                <Guest roomCandidateId = "1" paxId = "1">
                    <GivenName>Test11</GivenName>
                    <SurName>TestAp11</SurName>
                </Guest>
                <Guest roomCandidateId = "1" paxId = "2">
                    <GivenName>Test12</GivenName>
                    <SurName>TestAp12</SurName>
                </Guest>
            </Guests>
        </ResGuests>
        <PaymentType>MerchantPay</PaymentType>
        <Rooms>
            <Room id = "4582" roomCandidateRefId = "1" code = "506" description = "Double Standard.."/>
        </Rooms>
        <RoomCandidates>
            <RoomCandidate id = "1">
                <Paxes>
                    <Pax age = "30" id = "1"/>
                    <Pax age = "30" id = "2"/>
                </Paxes>
            </RoomCandidate>
        </RoomCandidates>
        <Remarks>I want it a double bed.</Remarks>
    </ReservationRQ>
~~~


### ReservationRQ Description



| **Element**					| **Number**	| **Type**	| **Description**					|
| --------------------------------------------- | ------------- | ------------- | ----------------------------------------------------- |
| ReservationRQ 				| 1      	|		| Root node.						|
| ClientLocator 				| 1  		| String	| Booking ID in client's system.					|
| OnRequest     				| 1  		| Boolean	| Indicates if you want to receive the onrequest options in AvailRS, as long as the supplier returns it in this method (see StaticConfiguration).	|
| Parameters    				| 0..1    	|		| Parameters for additional information that have been reported in ValuationRS.	|
| Parameters/Parameter				| 1..n    	|		| List of parameters.					|
| @key     					| 1  		| String	| Contains the keyword/Id to identify a parameter.	|
| @value   					| 1  		| String	| Contains the value of the parameter.			|
| DeltaPrice    				| 0..1    	|		| Indicates price variation permitted by the client.	|
| @amount  					| 0..1		| String	| Amount (in the currency returned into the option) that is accepted by the client to be higher than the valuation price. |
| @percent 					| 0..1		| String	| Percentage accepted by the client to be higher than the valuation price.	|
| @applyBoth					| 1  		| Boolean	| Indicates that the range between valuation price and the new price does not exceed the amount and/or porcentage indicated by the client.  |
| StartDate     				| 1  		| String 	| Start date to search rates.				|
| EndDate       				| 1  		| String	| End date to search rates.				|
| MealPlanCode  				| 1  		| String	| MealPlan code.					|
| HotelCode     				| 1  		| String	| Hotel code.						|
| Nationality   				| 0..1		| String	| Nationality of the Holder (use ISO3166_1_alfa_2). This informations will be mandatory depending on the supplier (see StaticConfiguration).  |
| Price         				| 1      	|		| Total price of this valuation.			|
| @currency					| 1  		| String	| Currency code.					|
| @amount  					| 1  		| Decimal	| Option Amount.					|
| @binding 					| 1  		| Boolean	| Identifies if is the price is binding (When true the sale price returned **must** not be less than the price informed.  |
| @commission					| 1  		| Decimal	| Commission (-1 = not specified, 0 = net price, X = % of the commission applied to the amount.	|
| ResGuests     				| 1      	|		| 				|
| ResGuests/Guests				| 1      	|		| List of passengers.					|
| ResGuests/Guests/Guest			| 1..n    	|		| Detail of each passenger.				|
| @roomCandidateId				| 1  		| Integer	| Room candidate Identifier				|
| @paxId   					| 1  		| Integer	| Passenger id (starting at 1).				|
| ResGuests/Guests/Guest/GivenName		| 1 	 	| String	| Guest's given name.						|
| ResGuests/Guests/Guest/SurName		| 1   		| String	| Guest's last name.						|
| PaymentType   				| 1  		| String	| Indicates the type of payment.			|
| Rooms          				| 1      	|		| Rooms within this option (room list).			|
| Rooms/Room    				| 1..n    	|		| Detail of room. 					|
| @id      					| 1  		| String	| Room identifier.				|
| @roomCandidateRefId				| 1  		| Integer	| Room candidate identifier.				|
| @code    					| 1  		| String	| Room code.						|
| @description					| 1  		| String	| Room description.					|
| RoomCandidates/RoomCandidate			| 1..n    	|		| Room required.					|
| @id      					| 1  		| Integer	| Id of the requested room (starting at 1).		|
| RoomCandidates/RoomCandidate/Paxes/Pax	| 1..n    	|		| Pax required.						|
| @age     					| 1  		| Integer	| Passenger age. 					|
| @id      					| 1  		| Integer	| Passenger id (starting at 1). 			|
| Remarks       				| 0..1    	| 		| Any customer comments for the supplier to consider (as long as the supplier returns it in this method, see StaticConfiguration).	|
  



### ReservationRS Example


~~~xml
    <ReservationRS>
        <ProviderLocator>102</ProviderLocator>
        <ResStatus>OK</ResStatus>
        <Price currency = "EUR" amount = "36.20" binding = "false" commission = "-1"/>
    </ReservationRS>
~~~


### ReservationRS Description



| **Element**					| **Number**	| **Type**	| **Description**					|
| --------------------------------------------- | ------------- | ------------- | ----------------------------------------------------- |
| ReservationRS					| 1       	|		| Root node.						|
| ProviderLocator 				| 1  		| String	| Booking ID in the Supplier´s system					|
| ResStatus					| 1  		| String	| reservation status  (OK = confirmed, RQ = on request, CN = cancelled, UN = unknown.	|
| Price  					| 0..1     	|		| Total price of this reservation.				|
| @currency					| 1  		| String	| Currency code.					|
| @amount					| 1  		| Decimal	| Book Amount.						|
| @binding					| 1  		| Boolean	| Identifies if is the price is binding (when true the sale price returned **must** not be less than the price informed. |
| @commission					| 1  		| Decimal	| Commission (-1 = not specified, 0 = net price, X = % of the commission that applies to the amount.	|
| Remarks					| 0..1		| String	| Any remarks about this reservation			|
| BillingSupplierCode				| 0..1		| String	| Supplier's billing code. Will be returned if the supplier has different billing accounts and this is informed in the reservation.	|
| Payable					| 0..1     	|		| Payable.						|
| @value					| 1       	|		| Informs Payable.					|
  



### Detailed description


**ResStatus:**

When making a reservation,  there will be a field named
ResStatus in the response indicating the status of the reservation. It
can have four values: OK, RQ, CN and UN.

-   *OK:* The reservation was completed with no problems.
-   *RQ:* The reservation was completed but the product is still not
    available, so the reservation goes into a waiting list (Request).
-   *CN:* The reservation was completed but due to a supplier error or a timeout
    the system will immediately cancel the reservation to prevent further possible errors.
-   *UN:* The reservation was completed but due to a supplier error or a timeout, the reservation status is unknown.
   It is the client's responsibility to check if the booking is OK.



**Note:** *Keep the parameters in the valuation response to include them in the reservation request.*



**MerchantPay, LaterPay, CardBookingPay & CardCheckInPay**

CardChekInPay:payment using the card used in the ReservationRQ at the time of check in. 
CardBookingPay: payment completed in the day of the booking using the same card  provided in the ReservationRQ 
LaterPay: payment completed at the hotel (cash, card or another type as per each hotel's payment options.)
MerchantPay: paid by invoice.

~~~xml
    <PaymentType>MerchantPay</PaymentType>
~~~

If the payment is done by credit card, is it mandatory to specify the payment type and the credit card information in the XML request as in the example below:

~~~xml
    <PaymentType>LaterPay/CardBookingPay/CardCheckInPay</PaymentType>
      <CardInfo>
       <CardCode>XX</CardCode>
       <Number>XXXXXXXXXX</Number>
       <Holder>XXXX</Holder>
       <ValidityDate>   
         <Month>XX</Month>
         <Year>XX</Year>
       </ValidityDate>
       <CVC>XXX</CVC>
     </CardInfo>    
~~~


### DeltaPrice description


**applyBoth:**

Depending on the value of applyBoth:

-   *applyBoth ="false"*: Indicates that one of the conditions (amount
    or percentage) has to meet the criteria before confirmation
    process.
-   *applyBoth ="true"*: Indicates that the new price cannot exceed
    the amount or percentage indicated by the client.

In case that the checking is not correct, an error will be returned
before confirmation process. If DeltaPrice tag is not sent in case that
the integration implements it, we will take into account that the price
range is 0 so the process will keep on in case that the price is lower
or equal to the price showed in valuation process.

This field it is implemented if the provider has it as a native or if it
is necessary to do another availability/valuation process. In case that
the provider blocks the option in valuation process, confirmation
process will be done directly (because the provider does not have native
delta price and this will not be implemented). Static configuration of
each provider informs if it is implemented or it is not.



