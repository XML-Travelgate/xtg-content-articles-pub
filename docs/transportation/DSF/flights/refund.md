---
title: Refund
keywords: transportation, data structure, flights, refund
search: Transportation - Flights - Data Structure - Refund
sidebar: mydoc_sidebar
permalink: /docs/transportation/DSF/flights/refund
---



### Method Goals


This method aims to refund tickets issued previously.



### Request Format


The request must indicate the tickets to be refunded, PNR code, the refund operation type and refund type.



### Response Format


The result returns empty response



### Remarks


Not implemented by all suppliers



### RefundRQ Example


~~~xml
<RefundRQ penaltyAmount="0">
  <timeoutMilliseconds>18000</timeoutMilliseconds>
  <source>
    <languageCode>es</languageCode>
  </source>
  <filterAuditData>
    <registerTransactions>true</registerTransactions>
  </filterAuditData>
  <optionsQuota>0</optionsQuota>
  <Configuration providerCode="">
    <Credentials user="" password="">
      <UrlGeneric>xxxx</UrlGeneric>
    </Credentials>
    <Attributes>
      <Attribute key="" value="" />
    </Attributes>
   </Configuration>
  <ClientConfiguration agency="" mark="" businessLine="" mean="" accessLevel="" accessType="" currencyCode="" />
  <RefundProcess process="" />
  <RefundType type="" />
  <refundAmounts>
    <refundAmount refundAmountType="" amount="" amountCode="" />
  </refundAmounts>
  <Tickets>
    <Ticket ticketNum="">
      <PNRLoc code="" />
    </Ticket>
  </Tickets>
</RefundRQ>
~~~


### RefundRQ Description



| **Element**			| **Number**	| **Type**	| **Description**			|
| ----------------------------- | ------------- | ------------- | ------------------------------------- |
| RefundRQ              						| 1     	|			| Root node.				|
| @penaltyAmount								| 0..1     	|	Decimal	| Indicate penalty amount	|
| RefundProcess									| 1     	|			| Allows selecting refund operation mode	|
| @process										| 1     	|	String	| Select operation mode		|
| RefundType									| 1     	|			| Contains the type of refund|
| @type											| 1     	|	String	| Refund type|
| RefundAmounts			 						| 0..1     	|			| Contains refund amounts|
| RefundAmounts/RefundAmount					| 0..n     	|			| Contains a refund amount|
| @refundAmountType								| 1     	|	String	| Contains refund amount type|
| @amount										| 1     	|	Decimal	| Amount value|
| @amountCode									| 1     	|	String	| Provider amount code|
| Tickets		           						| 1     	|			| Tickets to refund	|
| Tickets/Ticket		           				| 1..n     	|			| Ticket to refund	|
| @ticketNum		           					| 1     	|	String	| Ticket number	|
| @paxName		           						| 0..1     	|	String	| Ticket's passenger name	|
| @paxType		           						| 0..1     	|	String	| Passenger type: ADT ( Adult ), CHD ( Child ) & INF ( Infant ).	|
| Tickets/Ticket/PNRLoc		           			| 1     	|			| Ticket's passenger PNR	|
| @code											| 1     	|	String	| PNR code value	|

### RefundRS Example

~~~xml
<RefundRS>
    <ResponseStatus tripType = "DEPARTURE" petitionType = "OW" status = "ok"/>
    <AmountBreakdown currency = "EUR" totalAmount = "15.00" nonCommissionableAmount = "0" commission = "-1">
        <PaxBreakdowns>
            <PaxBreakdown paxType = "ADT" amount = "5.00" taxes = "6.48" fees = "0" />
        </PaxBreakdowns>
    </AmountBreakdown>
    <Tickets>
        <Ticket
            id = "0"
            ticketNum = ""
            paxName = ""
            paxType = ""
            cancelled = "0"
            joined = "0"
            type = "eTicket"
            status = "Confirmed">
            <PNRLoc code = "xxxx"/>
        </Ticket>
        <RetrieveStatus>false</RetrieveStatus>
    </Tickets>
    <Locators>
        <Locator>
            <Id>xxxx</Id>
            <Type>PROVIDER</Type>
        </Locator>
    </Locators>
</RefundRS>
~~~


### RefundRS Description



| **Element**				| **Number**	| **Type**	| **Description**|
| ------------------------------------- | ------------- | ------------- | ------- |
| RefundRS                			| 1    		|			| Root node			 |							
| ResponseStatus                	| 1    		|			| Response status	 |
| @tripType          | 1    		|	String	| the type of the trip|	
| @petitionType      | 1    		|	String	| the type of the request|
| @status			| 1    		|	String	| the status of the response|																	
| AmountBreakdown  		| 1     	|		| Breakdown of the fare amount.		|
| @currency              		| 1 		| String	| Currency code of the fare.				|
| @totalAmount           		| 1 		| Decimal	| Total amount. with taxes and other charges included.	|
| @notCommissionableAmount		| 1 		| Decimal	| Total amount that can not be commissioned.  		|
| @commission            		| 1 		| Decimal	| Commission. 						|
| AmountBreakdown/PaxBreakdown | 1    	|		| Contains a list of breakdown amounts for each passenger ( ADT amount, etc. ).|
| AmountBreakdown/PaxBreakdowns/<br>PaxBreakdown | 1..n | 	| Contains details of breakdown amounts for each passenger.|
| @paxType               		| 1 		| String	| Passenger type: ADT ( Adult ), CHD ( Child ) & INF ( Infant ).|
| @amount                		| 1 		| Decimal	| Total amount, with taxes included, associated to the passenger.	|
| @taxes                 		| 1 		| Decimal	| If they exist, taxes are applied for this passenger type. |						|
| @fees                			| 0..1 		| Decimal	| Fees. 						|
| AmountBreakdown/PaxBreakdowns/<br>PaxBreakdown/Taxes | 0..1 | 	| Contains a list of Taxes.|
| AmountBreakdown/PaxBreakdowns/<br>PaxBreakdown/Taxes/Tax | 1..n | 	| Code and amount of each tax.|									
| Tickets		           			| 1     	|			| Tickets to refund	|
| Tickets/Ticket		           	| 1..n     	|			| Ticket to refund	|
| @ticketNum		    | 1     	|	String	| Ticket number	|
| @paxName		    | 1     	|	String	| Ticket's passenger name	|
| @paxType		    | 1     	|	String	| Passenger type: ADT ( Adult ), CHD ( Child ) & INF ( Infant ).	|
| @status			| 1     	|	String	| Ticket's status: Open, Confirmed, Voided, Refunded |
| @type				| 1     	|	String	| Ticket's type: Paper, eTicket, Extra 	|
| Tickets/Ticket/PNRLoc		        | 1     	|			| PNR passenger's ticket	|
| @code		| 1     	|	String	| PNR code value	|
| Locators                			| 1    		|			| Reservation locators|
| Locators/Locator                  | 1..n    	|			| Reservation locator|			
| Locators/Locator/Id               | 1    		|	String	| Locator id|	
| Locators/Locator/Type             | 1    		|	String	| Locator Type|	