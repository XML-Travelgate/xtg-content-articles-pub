---
title: Emit
keywords: transportation, data structure, flights, emit
search: Transportation - Flights - Data Structure - Emit
sidebar: mydoc_sidebar
permalink: /docs/transportation/DSF/flight/emit
---

### Method Goals

description

### Request Format

description rq

### Response Format

description rs

### Remarks

dunno m8

###EmitRQ Example

~~~xml
<EmitRQ>
</EmitRQ>
~~~
| **Element**				| **Number**	| **Type**	| **Description**|				
| ------------------------- | ------------- | --------- | -------------- |
|EmitRQ|1| |Root node.|
|@locator|1|String |Provider's locator from which the tickets will be emited.|
|EmissionType|1| |Contains the type of emission.|
|@type|1| |[Emission Type.](#emission-type-enumerate-description)|
|PaymentInfo|1| |Information about the method of payment for the ticket.|
|@paymentType|0..1| |[Payment Type.](#payment-type-enumerate-description)|
|PaymentInfo/PaymentDatas|1| |List of payment information.|
|PaymentInfo/PaymentDatas/ <br> PaymentData|1..n||Payment method data.|
|@paymentType|1| |[Payment Type.](#payment-type-enumerate-description)|
|@installmentsNumber|1|Integer|Number of installments to be paid.|
|PaymentInfo/PaymentDatas/<br> PaymentData/CardInfo|1| |Information about the card.|
|@provType|1|String|Credit card type in provider format (VI, MC, etc.)|
|@type|1|String|Credit Card type in API format (1:Visa, 2:VisaDebito...)|
|@holder|1|String|Credit card holder.|
|@number|1|String|Credit card number.|
|@cvv|1|String|Credit card verification number.|
|@expirationMonth|1|String|Expiration month (2 characters).|
|@expirationYear|1|String|Expiration year (4 characters).|
|PaymentInfo/PaymentDatas/<br> PaymentData/Amount|1| |Amounts by type.|
|PaymentInfo/PaymentDatas/<br> PaymentData/Amount/Amount|1| |List of amounts.|
|@currency|1|String|Currency code of the amount.|
|@amount|1|Decimal|Amount.|
|@amountType|1| |[Amount Type.](#amount-type-enumerate-description)|

##[WIP]

###Amount Type Enumerate Description
| **Element**				| **Possible Values**	| **Description**	|
| ------------------------- | --------------------- | ------------------ |
| @paymentType              | N                     | None |
| 							| AMOUNT                | |
| 							| FEE                   | |
| 							| TOTAL                 | |
| 							| PERCENTUAL            | |

### Payment Type Enumerate Description
| **Element**				| **Possible Values**	| **Description**	|
| ------------------------- | --------------------- | ------------------ |
| @paymentType              | N                     | None |
| 							| CASH                  | |
|                           | CARD                  | |
|                           | EMIT                  | |

### Emission Type Enumerate Description
| **Element**				| **Possible Values**	| **Description**	|
| ------------------------- | --------------------- | ------------------ |
| @type        				| N                     | None |
| 							| Air                   |Passenger tickets  |
| 							| Extra                 |Ancillaries (bags, seats, etc.) |
| 							| All                   |Both |
