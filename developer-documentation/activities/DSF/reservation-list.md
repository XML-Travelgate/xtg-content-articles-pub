---
title: Reservation List
keywords: activities, data structure, reservation list
sidebar: mydoc_sidebar
permalink: /developer-documentation/activities/DSF/reservation-list
---

|

Method Goals
============

This method aims to return all the reservation list of each activity
confirm for a given specific date from which you want to search and Date
type.

|

Request Format
==============

It is mandatory to pass a date range and a Date type. Depends the Date
type, you obtain different reservation list.

**Date types**

-   ArrivalDate : The arrival date of the reservation.
-   CreateDate : The date the reservation was created.
-   DepartureDate : The departure date of the reservation.
-   LastUpdateDate : The date the reservation was last updated.

|

ReservationsListRQ Example
==========================

:

    <OTA_ReadRQ
        xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance"
        xmlns:xsd = "http://www.w3.org/2001/XMLSchema"
        PrimaryLangID = "es">
        <ReadRequests>
            <TourActivityReadRequest>
                <SelectionCriteria
                    DateType = "ArrivalDate"
                    End = "2013-12-19T12:32:15"
                    Start = "2013-12-18T12:32:15"/>
            </TourActivityReadRequest>
        </ReadRequests>
    </OTA_ReadRQ>

|

ReservationsListRQ Description
==============================

  -------------------------------------------------------------------------
  Element          Num Typ Description
                   ber e   
  ---------------- --- --- ------------------------------------------------
  OTA\_ReadRQ      1       Root node.

  @PrimaryLangID   1   Str Language code (ISO 3166-1 alpha-2) format.
                       ing 

  ReadRequests     1       Retrieve a activity reservation list when the
                           booking reference is not known.

  ReadRequests/Tou 1       Retrieve a activity reservation list when the
  rActivityReadReq         booking reference is not known.
  uest                     

  ReadRequests/Tou 1       Retrieve a activity reservation list with range
  rActivityReadReq         date.
  uest/SelectionCr         
  iteria                   

  @DateType        1   Enu Specifies the type of date provided in the date
                       m   time span attributes (Possible values:
                           "ArrivalDate", "CreateDate", "ArrivalDate",
                           "DepartureDate", "LastUpdateDate").

  @End             1   Dat End date from which you want to search
                       e   reservation list.

  @Start           1   Dat Start date from which you want to search
                       e   reservation list.
  -------------------------------------------------------------------------

|

ReservationsListRS Example
==========================

:

    <OTA_TourActivityResRetrieveRS xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd = "http://www.w3.org/2001/XMLSchema">
        <operationImplemented>true</operationImplemented>
        <Detail ResStatus = "Confirmed" CreateDateTime = "2013-11-21T00:00:00">
            <BasicInfo Name = "Palma Aquarium" TourActivityID = "000200515"/>
            <Confirmation ID = "1283712#1" type = "PROVIDER"/>
            <Pricing>
                <Summary Amount = "33.341" CurrencyCode = "EUR">
                    <PricingType Extension = "PerTotal">Other_</PricingType>
                </Summary>
            </Pricing>
            <Schedule>
                <Detail>
                    <OperationTimes>
                        <OperationTime Start = "2013-12-18T00:00:00" End = "2013-12-18T00:00:00"/>
                    </OperationTimes>
                </Detail>
            </Schedule>
        </Detail>
        <Detail ResStatus = "Cancel" CreateDateTime = "2013-11-21T00:00:00">
            <BasicInfo Name = "Palma Aquarium" TourActivityID = "000200515"/>
            <Confirmation ID = "1283722#1" type = "PROVIDER"/>
            <Pricing>
                <Summary Amount = "0.000" CurrencyCode = "EUR">
                    <PricingType Extension = "PerTotal">Other_</PricingType>
                </Summary>
            </Pricing>
            <Schedule>
                <Detail>
                    <OperationTimes>
                        <OperationTime Start = "2013-12-18T00:00:00" End = "2013-12-18T00:00:00"/>
                    </OperationTimes>
                </Detail>
            </Schedule>
        </Detail>
        <Detail ResStatus = "Confirmed" CreateDateTime = "2013-11-21T00:00:00">
            <BasicInfo Name = "Palma Aquarium" TourActivityID = "000200515"/>
            <Confirmation ID = "1283723#1" type = "PROVIDER"/>
            <Pricing>
                <Summary Amount = "19.660" CurrencyCode = "EUR">
                    <PricingType Extension = "PerTotal">Other_</PricingType>
                </Summary>
            </Pricing>
            <Schedule>
                <Detail>
                    <OperationTimes>
                        <OperationTime Start = "2013-12-19T00:00:00" End = "2013-12-19T00:00:00"/>
                    </OperationTimes>
                </Detail>
            </Schedule>
        </Detail>
    </OTA_TourActivityResRetrieveRS>

|

ReservationsListRS Description
==============================

  ------------------ ---- --- ---------------------------------------------
  Element            |Num |Ty |Description|
                     ber  pe  

  OTA\_TourActivityR 1        Root node.
  esRetrieveRS                

  Detail             1..n     Information about reservation status and date
                              time for each reservation activity.

  @ResStatus         1    Enu Information about reservation status
                          m   (Possibles types: "Confirmed", "Cancel" or
                              "Unknow").

  @CreateDateTime    1    Dat Information about create reservation date
                          e   time.

  @LastModifyDateTim 0..1 Dat Information about last modify reservation
  e                       e   date time. For example, if cancel we return
                              date time when client cancel this
                              reservation.

  Detail/BasicInfo   0..1     If need search by activity provider code.

  @Name              0..1 Str Name of ticket.
                          ing 

  @TourActivityID    0..1 Str Code of ticket.
                          ing 

  Detail/Confirmatio 1        Contains information of the activity booked.
  n                           

  @ID                1    Str Activity booked identifier.
                          ing 

  @type              1    Str Activity booked type (Possible values:
                          ing "PROVIDER").

  Detail/PaymentInfo 0..1     Payment details that may be associated with
                              an individual participant, a participant
                              category and/or a group.

  @Description       0..1 Str A description of the charge.
                          ing 

  Detail/PickupDropo 0..1 Str The pickup and/or dropoff information if
  ff                      ing transportation is provided to/ from the
                              tour/activity location.

  @OtherInfo         0..1 Str Other instructions pertaining to the pickup/
                          ing dropoff.

  Pricing/Summary    0..1     Summary price for option, this element we
                              return if OpenAvailability = false

  @Amount            0..1 Dec Option price.
                          ima 
                          l   

  @CurrencyCode      0..1 Str Currency code (ISO 4217).
                          ing 

  Detail/Pricing/Sum 0..1 Str Specifies type of the option price, if value
  mary/PricingType        ing = Other then is mandatory specify Extension
                              type.

  @Extension         0..1 Str Specifies type of the option price.
                          ing 

  Detail/Pricing/Par 0..n Str Specifies price and participant category.
  ticipantCategory        ing 

  @age               0..1 Int Age of participant category.
                          ege 
                          r   

  Detail/Pricing/Par 0..1 Str Specifies participant type (Adult, Children
  ticipantCategory/Q      ing or Baby). If value = Other then then is
  ualifierInfo                mandatory specify Extension provider type.

  @Extension         0..1 Str Specifies provider code of participant
                          ing category.

  Detail/Pricing/Par 1        Specific price for each participantCategory.
  ticipantCategory/P          
  rice                        

  @Amount            1    Str ParticipantCategory price.
                          ing 

  @CurrencyCode      0..1 Str Currency code (ISO 4217).
                          ing 

  Detail/Schedule    0..1     Information about dates range on which you
                              can enjoy the activity. The same information
                              that send in request.

  Detail/Schedule/De 0..1     Information about specify dates on which you
  tail                        can enjoy the activity.

  Detail/Schedule/De 0..1     Information about specify dates on which you
  tail/OperationTime          can enjoy the activity.
  s                           

  Detail/Schedule/De 0..1     Information when activity starts.
  tail/OperationTime          
  s/OperationTime             

  @Start             0..1 Dat Start date activity.
                          e   

  @End               0..1 Dat End date activity.
                          e   
  ------------------ ---- --- ---------------------------------------------

|
