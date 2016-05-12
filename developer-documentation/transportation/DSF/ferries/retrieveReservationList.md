---
title: RetrieveReservationList
keywords: transportation, data structure, ferries, retrieve reservation list
sidebar: mydoc_sidebar
permalink: /developer-documentation/transportation/DSF/ferries/retrieveReservationList
---

|

Method Goals
============

This method aims to return a list of bookings for a given time period
being that either booking date or the travelling date.

|

Request Format
==============

The request requires a date (of reservation or departure) and all the
bookings that match this date will be returned.

|

Response Format
===============

The response contains a list of bookings that match the requested date.

RetrieveReservationListRQ Example
=================================

:

    <RetrieveReservationListRQ>
        <Configuration/>
        <ClientConfiguration currencyCode = "EUR"/>
        <ReservationDate>2014-03-04T00:00:00</ReservationDate>
        <DepartureDate>2010-09-09T00:00:00</DepartureDate>
        <ClientEmail>client@clientmail.com</ClientEmail>
        <OriginCode></OriginCode>
        <DestinationCode></DestinationCode>
        <AgencyCode></AgencyCode>
    </RetrieveReservationListRQ>

|

RetrieveReservationListRQ Description
=====================================

  ------------------------------------------------------------------------
  Element                        Nu Ty Description
                                 mb pe 
                                 er    
  ------------------------------ -- -- -----------------------------------
  RetrieveReservationListRQ      1     Root node.

  ReservationDate                1  St Reservation date.
                                    ri 
                                    ng 

  DepartureDate                  1  St Departure date.
                                    ri 
                                    ng 

  ClientEmail                    1  St Client's email.
                                    ri 
                                    ng 

  OriginCode                     1  St Origin code.
                                    ri 
                                    ng 

  DestinationCode                1  St Destination code.
                                    ri 
                                    ng 

  AgencyCode                     1  St Contains a list of Passengers.
                                    ri 
                                    ng 
  ------------------------------------------------------------------------

|

RetrieveReservationListRS Example
=================================

:

    <RetrieveReservationListRS xmlns:xsd = "http://www.w3.org/2001/XMLSchema" xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance">
    <ResponseStatus tripType = "IDA" petitionType = "OW" status = "ok"/>
    <ReservationList>
        <PaymentInfo locator = "V65CQC" totalAmount = "0">
            <OriginCode>PAL</OriginCode>
            <DestinationCode>BAR</DestinationCode>
            <ReservationDate>0001-01-01T00:00:00</ReservationDate>
            <DepartureDate>2014-03-25T20:30:00</DepartureDate>
            <MainPaxName/>
            <HolderName>TESTNAME1</HolderName>
            <ProviderReservationStatus/>
            <ReservationStatus>
                <ReservationStatusType>CONFIRMED</ReservationStatusType>
            </ReservationStatus>
        </PaymentInfo>
        <PaymentInfo locator = "M3LIUI" totalAmount = "0">
            <OriginCode>PAL</OriginCode>
            <DestinationCode>VAL</DestinationCode>
            <ReservationDate>0001-01-01T00:00:00</ReservationDate>
            <DepartureDate>2014-05-12T16:10:00</DepartureDate>
            <MainPaxName/>
            <HolderName>TESTNAME2</HolderName>
            <ProviderReservationStatus/>
            <ReservationStatus>
                <ReservationStatusType>CONFIRMED</ReservationStatusType>
            </ReservationStatus>
        </PaymentInfo>
    </ReservationList>

\</RetrieveReservationListRS\>

|

RetrieveReservationListRS Description
=====================================

  ------------------------------------------------------------------------
  Element                        Nu Ty Description
                                 mb pe 
                                 er    
  ------------------------------ -- -- -----------------------------------
  RetrieveReservationListRS      1     Root node.

  ReservationList                1     Contains a list of Reservations.

  ReservationList/PaymentInfo    1.    Contains the information of the
                                 .n    payment.

  <*@locator>\*                  1  St Unique identifier of the locator.
                                    ri 
                                    ng 

  <*@totalAmount>\*              1  De Total amount. with taxes and other
                                    ci charges included.
                                    ma 
                                    l  

  <*@currency>\*                 1  St Currency code of the fare.
                                    ri 
                                    ng 

  ReservationList/PaymentInfo/Or 1  St Trip origin location code.
  iginCode                          ri 
                                    ng 

  ReservationList/PaymentInfo/De 1  St Trip destination location code.
  stinationCode                     ri 
                                    ng 

  ReservationList/PaymentInfo/Re 1  Da Date on which the reservation was
  servationDate                     te made.

  ReservationList/PaymentInfo/De 1  Da Departure date.
  partureDate                       te 

  ReservationList/PaymentInfo/Ma 1  St Name and surname of the main
  inPaxName                         ri passenger of the reservation.
                                    ng 

  ReservationList/PaymentInfo/Ho 1  St Name of the holder of the
  lderName                          ri reservation.
                                    ng 

  ReservationList/PaymentInfo/Re 1     Current status of the reservation.
  servationStatus                      

  ReservationList/PaymentInfo/Re 1  St Reservation status: CONFIRMED (OK),
  servationStatus/ReservationSta    ri CANCELLED (Change of programming)
  tusType                           ng 
  ------------------------------------------------------------------------

|
