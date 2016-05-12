---
title: Cancel Booking
keywords: transfers, data structure, cancel booking, cancellation
sidebar: mydoc_sidebar
permalink: /developer-documentation/car/DSF/cancel
---

|

Method Goals
============

This method aims to cancel a booking

|

Remarks
=======

Not implemented by all suppliers

|

OTA VehCancelRQ Example
=======================

:

    <OTA_VehCancelRQ>
        <POS>
            <Source ISOCountry = "ESP">
                <RequestorID Type = "LAN" ID = "es"/>
            </Source>
        </POS>
        <VehCancelRQCore>
            <UniqueID ID = "XXXX" Type = "4"/>
            <PersonName>
                <GivenName>TEST</GivenName>
                <Surname>TEST</Surname>
            </PersonName>
        </VehCancelRQCore>
    </OTA_VehCancelRQ>

|

OTA VehCancelRQ Description
===========================

The request requires the booking code and the name of the customer.

  --------------------------------------------------------------------------
  Element        Numb Type    Description
                 er           
  -------------- ---- ------- ----------------------------------------------
  OTA\_VehCancel 1            Root Node
  RQ                          

  OTA\_VehCancel 1    Pos     Contains information of the Point Of Sale.
  RQ/POS                      

  OTA\_VehCancel 1    CancelI It has the UniqueID that identifies the
  RQ/VehCancelRQ      nfoRQ   reservation for the provider to cancel it.
  Core                        

  VehCancelRQ/Un 1    UniqueI Locator code that identifies the reservation.
  iqueID              D       

  VehCancelRQ/Pe 1    PersonN Object that contains the name of the customer.
  rsonName            ame     

  OTA\_VehCancel 1    vehCanc Contains the dates of the reservation and the
  RQ/VehCancelRQ      elRQInf selected offices. Most of the providers don't
  Info                o       require this information.

  vehCancelRQInf 1    RentalI Contains the locations and dates of the
  o/RentalInfo        nfo     rental.
  --------------------------------------------------------------------------

|

OTA VehCancelRS Example
=======================

:

    <OTA_VehCancelRS>
        <Success/>
        <VehCancelRSCore CancelStatus = " ">
            <CancelRules>
                <CancelRule Amount = " " CurrencyCode = " "/>
                ...
            </CancelRules>
            <UniqueID Type = " " ID = " "/>
        </VehCancelRSCore>
        <Errors>
            <Error></Error>
            ...
        </Errors>
        <Warnings>
            <Warning></Warning>
            ...
        </Warnings>
    </OTA_VehCancelRS>

|

OTA VehCancelRS Description
===========================

The result returns the new status of the reservation and the possible
cost of the cancellation.

  -------------------------------------------------------------------------
  Element               Number Type            Description
  --------------------- ------ --------------- ----------------------------
  OTA\_VehCancelRS      1                      Root Node

  OTA\_VehCancelRS/VehC 1      VehCancelRSCore Contains the Cancelation
  ancelRSCore                                  rules.

  VehCancelRSCore/Cance 1      eTransactionSta It showns the new status of
  lStatus                      tusType         the reservation.
  -------------------------------------------------------------------------

|
