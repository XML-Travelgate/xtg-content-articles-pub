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
| RefundProcess									| 1     	|			| Allows selecting refund operation mode	|
| RefundProcess/@process						| 1     	|	Enum	| Select operation mode		|
| RefundType									| 1     	|			| Contains the type of refund|
| RefundType/@type								| 1     	|	Enum	| Refund type|
| refundAmounts			 						| 0..1     	|			| Contains refund amounts|
| refundAmounts/refundAmount					| 0..n     	|			| Contains a refund amount|
| refundAmounts/refundAmount/@refundAmountType	| 1     	|	Enum	| Contains refund amount type|
| refundAmounts/refundAmount/@amount			| 1     	|	Decimal*	| Amount value|
| refundAmounts/refundAmount/@amountCode		| 1     	|	String	| Provider amount code|
| @penaltyAmount								| 0..1     	|	Decimal	| Indicate penalty amount	|
| Tickets		           						| 1     	|			| Tickets to refund	|
| Tickets/Ticket		           				| 1..n     	|			| Ticket to refund	|
| Tickets/Ticket/@ticketNum		           		| 1     	|	String	| Ticket number	|
| Tickets/Ticket/@paxName		           		| 0..1     	|	String	| Ticket's passenger name	|
| Tickets/Ticket/@paxType		           		| 0..1     	|	Enum	| Ticket's passenger type	|
| Tickets/Ticket/PNRLoc		           			| 1     	|			| Ticket's passenger PNR	|
| Tickets/Ticket/PNRLoc/@code		           	| 1     	|	String	| PNR code value	|

*Float in base 10. For more info, please visit: https://docs.microsoft.com/en-us/dotnet/api/system.decimal?view=netframework-4.7.2

### CancellationRS Example

~~~xml
<ReembolsoRS>
    <ResponseStatus tipoTrayecto = "IDA" tipoPet = "OW" estado = "ok"/>
    <DesgloseImporte currency = "EUR" totalAmount = "15.00" nonCommissionableAmount = "0" commission = "-1">
        <ChargeBreakdowns/>
        <PaxBreakdowns>
            <PaxBreakdown paxType = "ADT" amount = "5.00" taxes = "6.48" fees = "0" tasaDU = "0"/>
        </PaxBreakdowns>
    </DesgloseImporte>
    <Billetes>
        <Ticket
            id = "0"
            ticketNum = ""
            paxName = ""
            paxType = ""
            cancelled = "0"
            joined = "0"
            seatType = "UNKNOWN"
            type = "eTicket"
            status = "Confirmed">
            <PNRLoc code = "NBBS"/>
        </Ticket>
        <retrieveStatus>false</retrieveStatus>
    </Billetes>
    <Localizadores>
        <Locator>
            <Id>NBBS</Id>
            <Type>PROVIDER</Type>
        </Locator>
    </Localizadores>
</ReembolsoRS>
~~~


### RefundRS Description

| **Element**				| **Number**	| **Type**	| **Description**						|
| ------------------------------------- | ------------- | ------------- | ------- |
| RefundRS                			| 1    		|		| Root node			 |							
| ResponseStatus                	| 1    		|		| Response status	 |
| ResponseStatus/@tripType          | 1    		|	Enum	| the type of the trip|	
| ResponseStatus/@petitionType      | 1    		|	Enum	| the type of the request|
| ResponseStatus/@status			| 1    		|	Enum	| the status of the response|																	
| AmountBreakdown                	| 1    		|		| Amount breakdown	 |									
| Tickets		           			| 1     	|			| Tickets to refund	|
| Tickets/Ticket		           	| 1..n     	|			| Ticket to refund	|
| Tickets/Ticket/@ticketNum		    | 1     	|	String	| Ticket number	|
| Tickets/Ticket/@paxName		    | 0..1     	|	String	| Ticket's passenger name	|
| Tickets/Ticket/@paxType		    | 0..1     	|	Enum	| Ticket's passenger type	|
| Tickets/Ticket/PNRLoc		        | 1     	|			| Ticket's passenger PNR	|
| Tickets/Ticket/PNRLoc/@code		| 1     	|	String	| PNR code value	|			
| Locators                			| 1    		|		| Reservation locators|
| Locators/Locator                  | 1..n    		|		| Reservation locator|			
| Locators/Locator/Id               | 1    		|		| Locator id|	
| Locators/Locator/Type             | 1    		|		| Locator Type|	
			
### Refund Enumerate description

| **Element**				| **Possible Values**	| **Description**	|
| ------------------------- | --------------------- | ------------------ |
| RefundType/@type			| All | Fare and taxes will be refunded |
| 							| Fare | Only fare will be refunded |
| 							| Taxes | Only taxes will be refunded |
| 							| Auto | GDS automatic ticket change |

| **Element**				| **Possible Values**	| **Description**	|
| ------------------------- | --------------------- | ------------------ |
| RefundProcess/@process	| Info | Informative refund operation |
| 							| Process | Efective refund operation |

| **Element**				| **Possible Values**	| **Description**	 |
| ------------------------- | --------------------- | ------------------ |
| @refundAmountType			| Other | Other refund amount  |
| 							| Tax | Tax amount |
| 							| Flown | For partial refund when some segment is already flown |
| 							| Penalty | Penalty amount|

| **Element**				| **Possible Values**	| **Description**	|
| ------------------------- | --------------------- | ------------------ |
| @paxType					| ADT | Adult  |
| 							| CHD | Child |
| 							| INF | Infant|

| **Element**				| **Possible Values**	| **Description**	|
| ------------------------- | --------------------- | ------------------ |
| ResponseStatus/@tripType					| DEPARTURE | Outbound  |
| 							| RETURN | Inbound |
| 							| DEPARTURE_RETURN | Outbound and Inbound|

| **Element**				| **Possible Values**	| **Description**	|
| ------------------------- | --------------------- | ------------------ |
| ResponseStatus/ @status	| ok | ok status response |
| 							| err | error status response|
| 							| timeout | timeout status response|

| **Element**				| **Possible Values**	| **Description**	|
| ------------------------- | --------------------- | ------------------ |
| ResponseStatus/@petitionType				| RT | Round Trip. Outbound and inbound with same origin and destination |
| 							| OW | One Way. Outbound|
| 							| OJ | Open Jaw. Outbound and inbound with diferent origin or destination|
| 							| CT | Cicle Trip. Round trip with multiple destinations|

| **Element**				| **Possible Values**	| **Description**	|
| ------------------------- | --------------------- | ------------------ |
| Locator/Type				| PROVIDER | Round Trip. Outbound and inbound with same origin and destination |
| 							| UNIVERSAL | One Way. Outbound|
| 							| EMISSION | Open Jaw. Outbound and inbound with diferent origin or destination|
| 							| CARRIER | Cicle Trip. Round trip with multiple destinations|
| 							| SERVICE | Cicle Trip. Round trip with multiple destinations|
| 							| REFUND | Cicle Trip. Round trip with multiple destinations|
| 							| CHECKIN | Cicle Trip. Round trip with multiple destinations|