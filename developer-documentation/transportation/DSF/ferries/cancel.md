---
title: Cancellation
keywords: transportation, data structure, ferries, cancellation
sidebar: mydoc_sidebar
permalink: /developer-documentation/transportation/DSF/ferries/cancel
---

|

Method Goals
============

This method aims to cancel a booking.

|

Request Format
==============

The request requires the booking code or locator.

|

Response Format
===============

If the provider returns a Breakdown, this will be informed in
CancellarionRS.

|

CancellationRQ Example
======================

:

    <CancellationRQ>
       <Locator>XXX</Locator>
       <CancellationCosts>0</CancellationCosts>
    </CancellationRQ>

|

CancellationRQ Description
==========================

  -------------------------------------------------------------------------
  Element                      Nu Typ Description
                               mb e   
                               er     
  ---------------------------- -- --- -------------------------------------
  CancellationRQ               1      Root node.

  Locator                      1      Contains a list of Tickets.

  CancellationCosts            1      Contains details of the Ticket.
  -------------------------------------------------------------------------

|

CancellationRS Example
======================

:

    <CancellationRS>
    </CancellationRS>

|

CancellationRS Description
==========================

  ------------------------------------------------------------------------
  Element                        Nu Ty Description
                                 mb pe 
                                 er    
  ------------------------------ -- -- -----------------------------------
  CancellationRS                 1     Root node.

  AmountBreakdown                0.    Contains details of the
                                 .1    AmountBreakdown.

  <*@currency>\*                 1  St Currency code of the fare.
                                    ri 
                                    ng 

  <*@totalAmount>\*              1  De Total amount. with taxes and other
                                    ci charges included.
                                    ma 
                                    l  

  <*@notCommissionableAmount>\*  1  De Total amount that can not be
                                    ci commissioned.
                                    ma 
                                    l  

  <*@commission>\*               1  De Commission percentage. A -1 value
                                    ci will be returned if the provider
                                    ma doesn't return any comission
                                    l  information.

  Itineraries/Itinerary/AmountBr 0.    Contains a list of
  eakdown/ChargeBreakdowns       .1    ChargeBreakdowns.

  Itineraries/Itinerary/AmountBr 0.    Contains a list of breakdown
  eakdown/PaxBreakdowns          .1    amounts for each Passenger ( ADT
                                       amount, etc. ).

  Itineraries/Itinerary/AmountBr 0.    Contains details of breakdown
  eakdown/PaxBreakdowns/PaxBreak .n    amounts for each Passenger.
  down                                 

  <*@paxType>\*                  1  St Passenger type: ADT ( Adult ), CHD
                                    ri ( Child ) & INF ( Infant ).
                                    ng 

  <*@amount>\*                   1  De Total amount, with taxes included,
                                    ci associated to the Passenger.
                                    ma 
                                    l  

  <*@taxes>\*                    1  In If they exist, taxes are applied
                                    te for this Passenger type.
                                    ge 
                                    r  
  ------------------------------------------------------------------------

|
