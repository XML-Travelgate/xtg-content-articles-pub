---
title: Cancellation
keywords: transportation, data structure, flights, cancellation
sidebar: mydoc_sidebar
permalink: /docs/transportation/DSF/flights/cancel
---



### Method Goals


This method aims to cancel a booking.



### Request Format


The request requires the booking code or locator.



### Response Format


The result returns empty response



### Remarks


Not implemented by all suppliers



### CancellationRQ Example


~~~xml
    <CancellationRQ>
        <timeoutMilliseconds>18000</timeoutMilliseconds>
        <source>
            <languageCode>en</languageCode>
        </source>
        <filterAuditData>
            <registerTransactions>false</registerTransactions>
        </filterAuditData>
        <Configuration>
            <Credentials user = "xxx" password = "xxx"/>
        </Configuration>
        <Locator>xxx</Locator>
    </CancellationRQ>
~~~


### CancellationRQ Description



| **Element**			| **Number**	| **Type**	| **Description**			|
| ----------------------------- | ------------- | ------------- | ------------------------------------- |
| CancellationRQ              	| 1     	|		| Root node.				|
| Locator                     	| 1     	|		| Contains a list of Tickets.		|
| CancellationCosts           	| 1     	|		| Contains details of the Ticket.	|




### CancellationRS Example


~~~xml
    <CancellationRS>
    </CancellationRS>
~~~


### CancellationRS Description



| **Element**				| **Number**	| **Type**	| **Description**						|
| ------------------------------------- | ------------- | ------------- | ------------------------------------------------------------- |
| CancellationRS                	| 1    		|		| Root node.							|
| AmountBreakdown               	| 1    		|		| Contains details of the AmountBreakdown.			|
| @currency                		| 1 		| String	| Currency code of the fare.					|
| @totalAmount             		| 1 		| Decimal	| Total amount. with taxes and other charges included.		|
| @notCommissionableAmount 		| 1 		| Decimal	| Total amount that can not be commissioned.			|
| @commission              		| 1 		| Decimal	| Commission.							|
| Itineraries/Itinerary /AmountBreakdown/ChargeBreakdowns | 0..1 |  	| Contains a list of ChargeBreakdowns.				|
| Itineraries/Itinerary /AmountBreakdown/PaxBreakdowns | 0..1 |  	| Contains a list of breakdown amounts for each Passenger ( ADT amount, etc. ).	|
| Itineraries/Itinerary /AmountBreakdown/PaxBreakdowns /PaxBreakdown | 0..n |  | Contains details of breakdown amounts for each Passenger. |
| @paxType                 		| 1 		| String	| Passenger type: ADT ( Adult ), CHD ( Child ) & INF ( Infant ).  |
| @amount                  		| 1 		| Decimal	| Total amount, with taxes included, associated to the Passenger.  |
| @taxes                  		| 1 		| Integer	| If they exist, taxes are applied for this Passenger type.	|
| @tasaDU                  		| 1 		| Integer	| Deprecated.							|

