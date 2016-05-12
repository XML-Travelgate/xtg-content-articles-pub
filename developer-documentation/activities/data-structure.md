---
title: Data Structure
keywords: activities, data structure
sidebar: mydoc_sidebar
permalink: /developer-documentation/activities/data-structure
---

The structure of the API specification follows a standard. This document
intends to explain every aspect of this structure and their fields.

The integration will have the following methods:

  -------------------------------------------------------------------------
  Method     Input       Output      Requi Description
                                     red   
  ---------- ----------- ----------- ----- --------------------------------
  Search     SearchRQ    SearchRS    Yes   Gets destinations and events
                                           available

  Avail      AvailRQ     AvailRS     Yes   Makes an availability call

  Valuation  ValuationRQ ValuationRS Yes   Makes a valuation for refresh
                                           ticket price (pre-book)

  Reservatio Reservation Reservation Yes   Makes a booking
  n          RQ          RS                

  Reservatio Reservation Reservation No    Information about one
  nRead      ReadRQ      ReadRS            reservation

  Cancel     CancelRQ    CancelRS    No    Cancel a reservation

  Reservatio Reservation Reservation No    List of Reservations
  nsList     sListRQ     sListRS           
  -------------------------------------------------------------------------

Each request sent to the **service url** requires a node called rqXML .
Inside this node travels the current method's Input object.

The data structure will always have common elements in all objects and
the specific objects related to the operation

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
> Common-Elements\<./DSF/common-elements.rst\> Search
> \<.DSF/search.rst\> Avail\<./DSF/avail.rst\>
> Valuation\<./DSF/valuation.rst\> Reservation\<./DSF/reservation.rst\>
> Reservation Read\<./DSF/reservation-read.rst\>
> Cancel\<./DSF/cancel.rst\> Reservation
> List\<./DSF/reservation-list.rst\> StaticConfiguration
> \<./DSF/static-configuration.rst\> RunTimeConfiguration
> \<./DSF/runtimeconfiguration.rst\>
