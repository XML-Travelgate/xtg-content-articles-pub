---
title: Frequently Asked Questions!
keywords: intro
sidebar: mydoc_sidebar
permalink: /docs/hotel/FAQ
---



**How many providers can we do a one request?**

Only one provider per request. The only exception is with the
petition MultiAvail, where you can use one or more providers.

**How can I identify which providers is which in the MultiAvail call?**

By using the field ID in the request.

For example:
   
**In the request:**

~~~xml
<!--First provider-->
<ns:code>TEST</ns:code>
<ns:id>1</ns:id>
~~~
~~~xml
<!--Second provider-->
<ns:code>TEST2</ns:code>
<ns:id>2</ns:id>
~~~

**In the response:**

~~~xml
<!--Response first provider-->
<refId>1</refId>
~~~
~~~xml
<!--Response Second provider-->
<refId>2</refId>
~~~

**How does the price work and how should I interpret the value in the field "commission"?**

Every option has a price and every price indicates the currency, the
amount, if it is binding and the commission.

-   *Binding:*

If binding is set as true, then the client can't sell the product, which
is provided by the supplier, with an inferior price established by the
provider , if it set as as false, the client can sell the product with
an inferior price.

-   *Commission:*

   > -   If commission = 0 then the price returned is a net price, and
   >     the provider is informing that the commission **must** be 0.
   > -   If commission = -1 then the provider is not informing the sale
   >     price nor if the price is net. This information is obtained
   >     when signing with the provider or also if the binding price is
   >     true/false.
   > -   When commission is greater than 0, for example: commission =
   >     12, it is a sale price, and this commission is informed for
   >     the provider ( this price is mandatory if binding price is
   >     true ).



**What is a static download and why do we use it?**

There are times when you want to do a call of your information
on-line, but this call can take more that 5 minutes, so, how can
we do this quicker? We will download all of your information
necessary to our servers, so when this happens, we can send you
the static information that we have loaded into our system.

**In the tag "RequiredAllPassenger", is specifying the names of the babies necessary?**

If the value of "RequiredAllPassengers" is true in the static
data, then yes, it is necessary.
