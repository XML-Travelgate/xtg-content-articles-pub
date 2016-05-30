---
title: Reservation
keywords: hotel, data structure, reservation
sidebar: mydoc_sidebar
permalink: /docs/hotel/DSF/Reservation
---



### Method Goals


This method aims to book an option.



### Request Format


The request format works the same way as the *Valuation* request but
with the list of passengers.



### Response Format


The result returns the booking locator (booking code). It can be the
provider's or the one sent in the request.



It also returns all the charges associated to the booking and the state
of booking.



### Remarks


The maximum time, that is permitted in our system, before the connection
is closed, is of **180000** milliseconds.



### ReservationRQ Example


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



### ReservationRQ Description



| **Element**					| **Number**	| **Type**	| **Description**					|
| --------------------------------------------- | ------------- | ------------- | ----------------------------------------------------- |
| ReservationRQ 				| 1      	|		| Root node.						|
| ClientLocator 				| 1  		| String	| Client locator.					|
| OnRequest     				| 1  		| Boolean	| Indicates if you want to receive the on request options in AvailRS, as long as the provider returns it in this call (see StaticConfiguration).	|
| Parameters    				| 0..1    	|		| Parameters for additional information that have been reported in ValuationRS.	|
| Parameters/Parameter				| 1..n    	|		| List of parameter.					|
| @key     					| 1  		| String	| Contains the keyword/Id to identify a parameter.	|
| @value   					| 1  		| String	| Contains the value of the parameter.			|
| DeltaPrice    				| 0..1    	|		| Price range accepted by the client to be higher than valuation and confirmation process.	|
| @amount  					| 0..1		| String	| Amount (in the currency returned into the option) that is accepted by the client to be higher than the valuation price. |
| @percent 					| 0..1		| String	| Percentage accepted by the client to be higher than the valuation price.	|
| @applyBoth					| 1  		| Boolean	| Indicates that the range between valuation price and the new price does not exceed the amount and/or porcentage indicated by the client.  |
| StartDate     				| 1  		| String 	| Start date to search rates.				|
| EndDate       				| 1  		| String	| End date to search rates.				|
| MealPlanCode  				| 1  		| String	| MealPlan code.					|
| HotelCode     				| 1  		| String	| Hotel code.						|
| Nationality   				| 0..1		| String	| Nationality of the Holder (use ISO3166_1_alfa_2). This informations will be mandatory depending on the provider, as long as the provider returns it in this call (see StaticConfiguration).  |
| Price         				| 1      	|		| Total price of this valuation.			|
| @currency					| 1  		| String	| Currency code.					|
| @amount  					| 1  		| Decimal	| Option Amount.					|
| @binding 					| 1  		| Boolean	| Identifies if is the price is binding ( When true the sale price returned **must** not be less than the price informed.  |
| @commission					| 1  		| Decimal	| Commission (-1 = not specified (will come indicated with the provider contract), 0 = net price, X = % of the commission that applies to the amount.	|
| ResGuests     				| 1      	|		| Structure of the passengers.				|
| ResGuests/Guests				| 1      	|		| List of passengers.					|
| ResGuests/Guests/Guest			| 1..n    	|		| Detail of each passenger.				|
| @roomCandidateId				| 1  		| Integer	| Identifier of room candidate.				|
| @paxId   					| 1  		| Integer	| Passenger id (starting at 1).				|
| ResGuests/Guests/Guest/GivenName		| 1 	 	| String	| Given name.						|
| ResGuests/Guests/Guest/SurName		| 1   		| String	| Surname.						|
| PaymentType   				| 1  		| String	| Indicates the typology of payment.			|
| Rooms          				| 1      	|		| Rooms of this option ( room list).			|
| Rooms/Room    				| 1..n    	|		| Detail of room. 					|
| @id      					| 1  		| String	| Identifier of the room.				|
| @roomCandidateRefId				| 1  		| Integer	| Identifier of room candidate.				|
| @code    					| 1  		| String	| Room code.						|
| @description					| 1  		| String	| Room description.					|
| Rooms/Room/Price				| 1      	|		| Total price of this room.				|
| @currency					| 1  		| String	| Currency code.					|
| @amount  					| 1  		| Decimal	| Room Amount.						|
| @binding 					| 1  		| Boolean	| Identifies if is the price is binding ( When true the sale price returned **must** not be less than the price informed.  |
| @commission					| 1  		| Decimal	| Commission (-1 = not specified (will come indicated with the provider contract), 0 = net price, X = % of the commission that applies to the amount.		|
| RoomCandidates/RoomCandidate			| 1..n    	|		| Room required.					|
| @id      					| 1  		| Integer	| Id of the requested room (starting at 1).		|
| RoomCandidates/RoomCandidate/Paxes/Pax	| 1..n    	|		| Pax required.						|
| @age     					| 1  		| Integer	| Passenger age. 					|
| @id      					| 1  		| Integer	| Passenger id (starting at 1). 			|
| Remarks       				| 0..1    	| 		| Customer comments for reservation option. The provider will consider it, as long as the provider returns it in this call (see StaticConfiguration).	|
  



### ReservationRS Example



    <ReservationRS>
        <ProviderLocator>102</ProviderLocator>
        <ResStatus>OK</ResStatus>
        <Price currency = "EUR" amount = "36.20" binding = "false" commission = "-1"/>
    </ReservationRS>



### ReservationRS Description



| **Element**					| **Number**	| **Type**	| **Description**					|
| --------------------------------------------- | ------------- | ------------- | ----------------------------------------------------- |
| ReservationRS					| 1       	|		| Root node.						|
| ProviderLocator 				| 1  		| String	| Provider locator.					|
| ResStatus					| 1  		| String	| Status of book (OK = confirmed, RQ = on request, CN = cancelled, UN = unknown.	|
| Price  					| 0..1     	|		| Total price of this book.				|
| @currency					| 1  		| String	| Currency code.					|
| @amount					| 1  		| Decimal	| Book Amount.						|
| @binding					| 1  		| Boolean	| Identifies if is the price is binding ( When true the sale price returned **must** not be less than the price informed. |
| @commission					| 1  		| Decimal	| Commission ( -1 = not specified (will come indicated with the provider contract ), 0 = net price, X = % of the commission that applies to the amount.	|
| Remarks					| 0..1		| String	| Remarks of this book.					|
| BillingSupplierCode				| 0..1		| String	| Society billing code, will be returned given that the supplier has different billing societies and that the supplier informs this in the reservation.	|
| Payable					| 0..1     	|		| Payable.						|
| @value					| 1       	|		| Informs Payable.					|
  



### Detailed description


**ResStatus:**

When doing a reservation, in the response, there will be a field named
ResStatus which will indicate the status of the reservation. The status
of the reservation can have fours values: OK, RQ, CN and UN.

-   *OK:* The reservation finished with no problems.
-   *RQ:* The reservation is finished but the product is still not
    available, so it will set the reservation in a waiting list (
    Request ).
-   *CN:* The reservation is finished but a provider error or a timeout
    occurred, then for some providers, the system will immediately
    cancel the reservation to prevent possible errors.
-   *UN:* The reservation is finished but a provider error or a timeout
    occurred and we can't assure 100% that the status of the reservation
    is in a OK status, therefore it is the clients responsibility to
    check if the reservation fulfilled completely.



**Note:** *Keep the parameters in the valuation response to include them in the reservation request.*



**MerchantPay & LaterPay & CardBookingPay & CardCheckInPay**

In the reservation, you can pay with cash or with a credit card. If the
payment is done by cash, in the XML petition you only have to specify
the payment type, like so:

    <PaymentType>MerchantPay</PaymentType>



If the payment is done by credit card, then in the XML petition, is it
mandatory to specify the payment type and the credit card information,
like so:

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



### DeltaPrice description


**applyBoth:**

Depending on the value of applyBoth:

-   *applyBoth ="false"*: Indicates that one of the conditions (amount
    or percentage) has to meet the critertia before confirmation
    process.
-   *applyBoth ="true"*: Indicates that the new price can not exceed
    neither amount nor percentage indicated by the client.

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



