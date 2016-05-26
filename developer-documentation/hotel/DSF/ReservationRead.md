---
title: ReservationRead
keywords: hotel, data structure, reservation
sidebar: mydoc_sidebar
permalink: /developer-documentation/hotel/DSF/ReservationRead
---



### Method Goals


This method aims to retrieve a booking with its full details.



### Request Format


The request requires one of the following data depending on provider:

-   *Locators*: booking codes (this element contains two elements
    *Client* (client's booking code) and *Provider* (provider's booking
    code), one or both will be required depending on the provider)
-   *Currency*: the currency code
-   *CreationDate*: the booking date
-   *StardDate*: the check-in date
-   *EndDate*: the check-out date



### Response Format


The result returns the full details of a booking. It is very similar to
the *Option* in the Availability Response, the cancel policies and
holder of booking.



### Remarks


The maximum time, that is permitted in our system, before the connection
is closed, is of **180000** millisecond.



### ReservationReadRQ Example


    <ReservationReadRQ>
        <Locators>
            <Client>5356342</Client>
            <Provider>MGNZ12345</Provider>
        </Locators>
        <Currency>EUR</Currency>
        <StartDate>28/01/2014</StartDate>
        <EndDate>29/01/2014</EndDate>
        <CreationDate>17/01/2014</CreationDate>
    </ReservationReadRQ>



### ReservationReadRQ Description


  
| **Element** 		| **Number**	| **Type**	| **Description**					|
| --------------------- | ------------- | ------------- | ----------------------------------------------------- |
| ReservationReadRQ	| 1		|		| Root node.						|
| Locators   		| 1          	|		| Information of the locators (it is mandatory indicate one of two, or client or provider). |
| Locators/Client	| 0..1		| String	| Client locator.					|
| Locators/Provider	| 0..1		| String	| Provider locator.					|
| Currency   		| 1    		| String	| Currency code.					|
| StartDate  		| 1    		| String	| Start date of booking. 				|
| EndDate    		| 1    		| String	| End date of booking.					|
| CreationDate		| 1    		| String	| Creation date of booking.				|



### ReservationReadRS Example


    <ReservationReadRS>
          <Locators>
                    <Client>2578478</Client>
                    <Provider>10TTT31</Provider>
                </Locators>
                <Hotel>
                    <Name>LEO</Name>
                    <Code>10</Code>
                    <CreationDate>17/01/2014</CreationDate>
                    <StartDate>28/01/2014</StartDate>
                    <EndDate>29/01/2014</EndDate>
                    <Holder name = "Test11" surname = "TestAp11"/>
                    <Price currency = "EUR" amount = "36.20" binding = "false" commission = "-1"/>
                    <Rooms>
                        <Room id = "4582" roomCandidateRefId = "1" description = "Doble Standard.."/>
                    </Rooms>
                    <CancelPenalties nonRefundable = "false">
                        <CancelPenalty>
                            <HoursBefore>120</HoursBefore>
                            <Penalty type = "Importe" paymentType = "pagoMinorista" currency = "EUR">72.40</Penalty>
                        </CancelPenalty>
                    </CancelPenalties>
                </Hotel>
                <TransactionStatus>
                    <ComunicationStatus>OK</ComunicationStatus>
                    <RSStatus>EXISTE</RSStatus>
                    <ResStatus>OK</ResStatus>
                </TransactionStatus>
    </ReservationReadRS>



### ReservationReadRS Description


  
| **Element**				| **Number**	| **Type**	| **Description**				|
| ------------------------------------- | ------------- | ------------- | --------------------------------------------- |
| ReservationReadRS			| 1 		|          	| Root node.					|
| Locators   				| 1          	|		| Information of the locators (it is mandatory indicate one of two, or client or provider). |
| Locators/Client			| 0..1 		| String	| Client locator.				|
| Locators/Provider			| 0..1 		| String	| Provider locator.				|
| Hotel      				| 0..1       	|		| Hotel reservation.				|
| Hotel/Name 				| 0..1 		| String	| Hotel Name.					|
| Hotel/City 				| 0..1 		| String	| Hotel city.					|
| Hotel/CreationDate			| 0..1 		| String 	| Creation date of booking.    			|
| Hotel/StartDate			| 1    		| String	| Start date of booking.			|
| Hotel/EndDate				| 1    		| String	| End date of booking.				|
| Hotel/MealPlanCode			| 0..1 		| String	| Mealplan code of booking.			|
| Hotel/Holder				| 0..1 		| String	| Holder reservation.				|
| @name>				| 1    		| String	| Holder name.					|
| @surname				| 1    		| String	| Holder surname.				|
| Hotel/Price				| 1    		| String	| Price reservation.   				|
| @currency				| 1    		| String	|						|
| @amount				| 1    		| Decimal	| Book Amount.					|
| @binding				| 1    		| Boolean	| Identifies if is the price is binding ( When true the sale price returned must not be less than the price informed). |
| @commission				| 1    		| Decimal	| Commission ( -1 = not specified (will come indicated with the provider contract ), 0 = net  price, X = % of the commission that applies to the amount . |
| Hotel/Rooms				| 0..1       	|		| Rooms reservation.				|
| Hotel/Rooms/Room			| 1..n       	|		| Room reservation.				|
| @id   				| 0..1 		| String	| Identifier of the room.			|
| @roomCandidateRefId			| 0..1 		| Integer	| Identifier of room candidate.			|
| @code 				| 0..1 		| String	| Room code.     				|
| @description				| 0..1 		| String	| Room description.				|
| Hotel/RoomCandidates			| 0..1       	|		| Rooms required in the creation of the booking.|
| Hotel/RoomCandidates/RoomCandidate	| 1..n       	|		| Room required.				|
| @id					| 0..1 		| Integer	| Id of the requested room (starting at 1). 	|
| RoomCandidates/RoomCandidate/Paxes/Pax| 1..n       	|		| Pax required.					|
| @age					| 0..1 		| Integer	| Passenger age.				|
| @id					| 0..1 		| Integer	| Id of the requested room (starting at 1).	|
| Hotel/CancelPenaltiesCancelPenalties	| 0..1       	|		| Information of cancellation policies.		|
| @nonRefundable			| 1    		| Boolean	| Indicate if this option is nonRefundable (true or false). |
| Hotel/CancelPenalties/CancelPenalty	| 0..n       	|		| Listing cancellation penalties.		|
| Hotel/CancelPenalties/CancelPenalty/HoursBefore | 1	|		|     String Number of hours prior to arrival day in which this Cancellation policy applies. |
| Hotel/CancelPenalties/CancelPenalty/Penalty |   1 	|         	| Contains the value to apply.			|
| @type 				| 1    		| String	| Type of penalty Possible values: "Noches" (nights) , "Porcentaje" (percentage) ,"Importe" (price value). |
| @paymentType				| 1    		| String	| Indicates the typology of payment.		|
| @currency				| 1    		| String	| Currency code.				|
| Hotel/Remarks				| 0..1 		| String	| Remarks.					|
| TransactionStatus			| 1    		| Trans.	| Status.					|
| TransactionStatus/ComunicationStatus	| 1    		| String	| Status communication ( OFFLINE, OK and KO).	|
| TransactionStatus/RSStatus		| 1    		| String	|  Status response (Status response (DESCONOCIDO (Unknown), EXISTE (Exists), EXISTECANCELADA (Cancelled), NO EXISTE (Does not exist)). |
| TransactionStatus/ResStatus		| 1    		| String	| Status booking (OK = confirmed, RQ = on request, CN = cancelled, UN = unknown). |
                

