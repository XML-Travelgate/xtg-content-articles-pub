---
title: Reservation Read
keywords: activities, data structure, reservation read
sidebar: mydoc_sidebar
permalink: /developer-documentation/activities/DSF/reservation-read
---

|

Method Goals
============

This method aims to consult a reservation

|

Request Format
==============

The request requires the booking code and the name of the customer

|

Response Format
===============

The result returns the new status of the reservation and the possible
cost of the consultation.

|

Remarks
=======

Not implemented by all suppliers

|

ReservationReadRQ Example
=========================

:

    <OTA_ReadRQ
        xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance"
        xmlns:xsd = "http://www.w3.org/2001/XMLSchema"
        PrimaryLangID = "es">
        <UniqueID ID = "1283712#1" Type = "PROVIDER"/>
    </OTA_ReadRQ>

|

ReservationReadRQ Description
=============================

  ------------------------------------------------------------------------
  Element    Numbe Type  Description
             r           
  ---------- ----- ----- -------------------------------------------------
  OTA\_ReadR 1           Root node.
  Q                      

  @PrimaryLa 1     Strin Language code (ISO 3166-1 alpha-2) format.
  ngID             g     

  UniqueID   1           Contains information of the activity booked..

  @ID        1     Strin Activity booked identifier.
                   g     

  @type      1     Strin Activity booked type (Possible values: "PROVIDER"
                   g     or "CLIENT"). Usually by provider locator.
  ------------------------------------------------------------------------

|

ReservationReadRS Example
=========================

:

    <OTA_TourActivityResRetrieveRS xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd = "http://www.w3.org/2001/XMLSchema">
        <operationImplemented>true</operationImplemented>
        <Detail ResStatus = "Confirmed" CreateDateTime = "2013-11-21T00:00:00" LastModifyDateTime="2014-02-19T00:00:00">
            <BasicInfo Name = "Palma Aquarium" TourActivityID = "000200515"/>
            <Confirmation ID = "1283712#1" type = "PROVIDER"/>
            <PaymentInfo Description = "El importe total de esta factura PRO-FORMA debe obrar en poder de Beds On Line, Banco: CITIBANK(Avenida de Europa, 19 - P.E. la Moraleja, 108 - Alcobendas, Madrid) Cuenta:ES35 1474 0000 10 0012272006,  SWIFT:CITIESMX,  7 das antes de la llegada de los clientes (excepto reservas de grupos. Das de antelacin fijados en el momento de la confirmacin). En la orden de pago rogamos indiquen nuestro nmero de referencia.    Gracias por su colaboracin., AVISO: CAMBIO CDIGO SWIFT"/>
            <PickupDropoff OtherInfo = "El cliente puede canjear el bono en la oficina de billetes de Aquarium en C/ Manuela de los Herreros i Sor, 21 | 07610 Palma de Mallorca 

            Invierno (1 de noviembre a 31 de marzo):
            Lunes a viernes de 10:00 a 15:30 h
            Sbado & Domingo de 10:00h a 16:30h
            Verano (1 de abril a 31 de octubre):
            Todos los das de 9:30h a 18:30h

            El cliente no puede olvidar llevar su documento de identidad.

            En caso de emergencia, el cliente deber llamar al siguiente nmero: (+34) 902 430 419

             "/>
            <Pricing>
                <Summary Amount = "33.340" CurrencyCode = "EUR">
                    <PricingType Extension = "PerTotal">Other_</PricingType>
                </Summary>
                <ParticipantCategory age = "30">
                    <QualifierInfo>Adult</QualifierInfo>
                    <Price
                        Amount = "19.660"
                        CurrencyCode = "EUR"/>
                </ParticipantCategory>
                <ParticipantCategory age = "2">
                    <QualifierInfo>Infant</QualifierInfo>
                    <Price
                        Amount = "0.000"
                        CurrencyCode = "EUR"/>
                </ParticipantCategory>
                <ParticipantCategory age = "10">
                    <QualifierInfo>Children</QualifierInfo>
                    <Price
                        Amount = "13.681"
                        CurrencyCode = "EUR"/>
                </ParticipantCategory>
            </Pricing>
            <Schedule>
                <Detail>
                    <OperationTimes>
                        <OperationTime StartDate = "2013-12-18T00:00:00" EndDate = "2013-12-18T00:00:00"/>
                    </OperationTimes>
                </Detail>
            </Schedule>
        </Detail>
    </OTA_TourActivityResRetrieveRS>

|

ReservationReadRS Description
=============================

  -------------------------------------------------------------------------
  Element            Num Type Description
                     ber      
  ------------------ --- ---- ---------------------------------------------
  OTA\_TourActivityR 1        Root node.
  esRetrieveRS                

  Detail             1        Information about reservation status and date
                              time.

  @ResStatus         1   Enum Information about reservation status
                              (Possibles types: "Confirmed", "Cancel" or
                              "Unknow").

  @CreateDateTime    1   Date Information about create reservation date
                              time.

  @LastModifyDateTim 1   Date Information about last modify reservation
  e                           date time. For example, if cancel we return
                              date time when client cancel this
                              reservation.

  Detail/BasicInfo   0..      If need search by activity provider code.
                     1        

  @Name              0.. Stri Name of ticket.
                     1   ng   

  @TourActivityID    0.. Stri Code of ticket.
                     1   ng   

  Detail/Confirmatio 1        Contains information of the activity booked.
  n                           

  @ID                1   Stri Activity booked identifier.
                         ng   

  @type              1   Stri Activity booked type (Possible values:
                         ng   "PROVIDER").

  Detail/PaymentInfo 0..      Payment details that may be associated with
                     1        an individual participant, a participant
                              category and/or a group.

  @Description       0.. Stri A description of the charge.
                     1   ng   

  Detail/PickupDropo 0.. Stri The pickup and/or dropoff information if
  ff                 1   ng   transportation is provided to/ from the
                              tour/activity location.

  @OtherInfo         0.. Stri Other instructions pertaining to the pickup/
                     1   ng   dropoff.

  Pricing/Summary    0..      Summary price for option, this element we
                     1        return if OpenAvailability = false

  @Amount            0.. Deci Option price.
                     1   mal  

  @CurrencyCode      0.. Stri Currency code (ISO 4217).
                     1   ng   

  Detail/Pricing/Sum 0.. Stri Specifies type of the option price, if value
  mary/PricingType   1   ng   = Other then is mandatory specify Extension
                              type.

  @Extension         0.. Stri Specifies type of the option price.
                     1   ng   

  Detail/Pricing/Par 0.. Stri Specifies price and participant category.
  ticipantCategory   n   ng   

  @age               0.. Inte Age of participant category.
                     1   ger  

  Detail/Pricing/Par 0.. Stri Specifies participant type (Adult, Children
  ticipantCategory/Q 1   ng   or Baby). If value = Other then then is
  ualifierInfo                mandatory specify Extension provider type.

  @Extension         0.. Stri Specifies provider code of participant
                     1   ng   category.

  Detail/Pricing/Par 1        Specific price for each participantCategory.
  ticipantCategory/P          
  rice                        

  @Amount            1   Stri ParticipantCategory price.
                         ng   

  @CurrencyCode      0.. Stri Currency code (ISO 4217).
                     1   ng   

  Detail/Schedule    0..      Information about dates range on which you
                     1        can enjoy the activity. The same information
                              that send in request.

  Detail/Schedule/De 0..      Information about specify dates on which you
  tail               1        can enjoy the activity.

  Detail/Schedule/De 0..      Information about specify dates on which you
  tail/OperationTime 1        can enjoy the activity.
  s                           

  Detail/Schedule/De 0..      Information when activity starts.
  tail/OperationTime 1        
  s/OperationTime             

  @Start             0.. Date Start date activity.
                     1        

  @End               0.. Date End date activity.
                     1        
  -------------------------------------------------------------------------

|
