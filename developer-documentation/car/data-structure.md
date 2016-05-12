---
title: Data Structure
keywords: transfers, data structure
sidebar: mydoc_sidebar
permalink: /developer-documentation/car/data-structure
---

This document intends to explain every aspect of this structure and
their fields.

The integration will have the following methods:

  ------------------------------------------------------------------------
  Method   Input     Output    Req Description Endpoint
                               uir 
                               ed  
  -------- --------- --------- --- ---------------------------------------
  OTA\_Veh OTA\_VehA OTA\_VehA Yes Makes a availability call
  AvailRat vailRateR vailRateR     Car Booking Endpoint\_
  e        Q         S             

  OTA\_Veh OTA\_VehR OTA\_VehR Yes Makes a pre-booking
  RateRule ateRuleRQ ateRuleRS     Car Booking Endpoint\_

  OTA\_Veh OTA\_VehR OTA\_VehR Yes Makes a booking Car Booking Endpoint\_
  Res      esRQ      esRS          

  OTA\_Veh OTA\_VehL OTA\_VehL Yes Gets a static offices list
  LocSearc ocSearchR ocSearchR     Car Batch Endpoint\_
  h        Q         S             

  OTA\_Veh OTA\_VehR OTA\_VehR No  Gets booking details
  RetRes   etResRQ   etResRS       Car Booking Endpoint\_

  OTA\_Veh OTA\_VehC OTA\_VehC No  Cancels a booking
  Cancel   ancelRQ   ancelRS       Car Booking Endpoint\_

  StaticCo StaticCon StaticCon Yes Returns the information related to the
  nfigurat figuratio figuratio     configuration of the provider.
  ion      nRQ       nRS           Car Batch Endpoint\_

  RuntimeC RuntimeCo RuntimeCo Yes Returns information related to the
  onfigura nfigurati nfigurati     behaviour of the integration.
  tion     onRQ      onRS          Car Batch Endpoint\_
  ------------------------------------------------------------------------

Each request sent to the **service url** requires a node called rqXML .
Inside this node travels the current method's Input object.

|

**Typical Exchange Message Scenario**

Typical use case of message exchange flow between Providers and Sellers
can be resumed as:

1.  **Retrieve and purchase of car rental product**:

    > 1.  Agencies retrieve the available product from the provider
    >     using OTA\_VehAvailRate.
    > 2.  Once the final customer selects an option, a pre-booking must
    >     be done using OTA\_VehRateRule.
    > 3.  Finally when the customer agrees purchasing the option, the
    >     booking is created using OTA\_VehRes.

2.  **Manage Bookings:**

    > 1.  The information related to a booking previously created can be
    >     retrieved usingOTA\_VehRetRes.
    > 2.  A previously made reservation can be cancelled
    >     usingOTA\_VehCancel.

3.  **Office Mapping:**

    > 1.  Agencies can retrieve the available offices
    >     usingOTA\_VehLocSearch.

|

**Data structure content:**

> maxdepth
>
> :   3
>
> numbered
>
> :   
>
> Common Elements\<./DSF/common-elements.rst\>
> OTA\_VehAvailRate\<./DSF/avail.rst\>
> OTA\_VehRateRule\<./DSF/rate-rule.rst\>
> OTA\_VehRes\<./DSF/reservation.rst\> OTA\_VehLocSearch
> \<./DSF/routes.rst\> OTA\_VehRetRes\<./DSF/valuation.rst\>
> OTA\_VehCancel\<./DSF/cancel.rst\> Static configuration
> \<./DSF/static-configuration.rst\> Run Time Configuration
> \<./DSF/runtimeconfiguration.rst\> Code Lists \<./DSF/code-lists\>
