---
title: Flights Data Structure
keywords: transportation, flights data structure
sidebar: mydoc_sidebar
permalink: /developer-documentation/transportation/flights
---

The structure of the API specification follows a standard. This document
intends to explain every aspect of this structure and their fields.

|

The integration will have the following methods:

|

  --------------------------------------------------------------------------
  Method         Input           Output          Require escription
                                                 d       
                                                 | D     
  -------------- --------------- --------------- ------- -------------------
  Availability   AvailabilityRQ  AvailabilityRS  Yes | M akes a availability
                                                         call

  Valuation      ValuationRQ     ValuationRS     Yes | M akes a pre-booking

  Reservation    ReservationRQ   ReservationRS   Yes | M akes a booking

  RetrieveReserv RetrieveReserva RetrieveReserva No | G  ets booking details
  ation          tionRQ          tionRS                  

  RetrieveReserv RetrieveReserva RetrieveReserva No | G  ets booking list
  ationList      tionListRQ      tionListRS              

  Cancellation   CancellationRQ  CancellationRS  No | C  ancels a booking
  --------------------------------------------------------------------------

|

Each request sent to the **service url** requires a node called rqXML .
Inside this node travels the current method's Input object.

|

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
> Avail \<./DSF/flights/avail.rst\> Valuation
> \<./DSF/flights/valuation.rst\> Reservation
> \<./DSF/flights/reservation.rst\> RetrieveReservation
> \<./DSF/flights/recover-reserve.rst\> RetrieveReservationList
> \<./DSF/flights/recover-reserve-list.rst\> Cancellation
> \<./DSF/flights/cancel.rst\> Code Lists
> \<./DSF/commoen/codes-list.rst\>
