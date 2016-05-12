---
title: Valuation
keywords: activities, data structure, valuation
sidebar: mydoc_sidebar
permalink: /developer-documentation/activities/DSF/valuation
---

|

ValuationRQ Example
===================

    <OTA_TourActivityBookRQ xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd = "http://www.w3.org/2001/XMLSchema" PrimaryLangID = "es">
      <BookingInfo>
        <BasicInfo Name = "Palma Aquarium" TourActivityID = "000200515"/>
        <Schedule StartPeriod = "2014-03-20T00:00:00" EndPeriod = "2014-03-21T00:00:00"/>
        <Pricing>
          <ParticipantCategory age = "30">
            <QualifierInfo>Adult</QualifierInfo>
            <Price Amount = "19.661" CurrencyCode = "EUR"/>
          </ParticipantCategory>
        </Pricing>
        <TPA_Extensions>
          <Seat>
            <Level id = "N1" description = "Nivel 1"/>
            <Area id = "A1" description = "Area 1"/>
            <Zone id = "A1_z1" description = "Parte Central"/>
            <Sector id = "A1_z1_b1" description = "Delantera Derecha"/>
            <UrlSitting>http://93.90.21.41/Janto/traveltino/public/janto/main.php?Nivel=Detalle_1_Sesion&Idioma=es&idSesion=0000000000000211&idZona=A1_z1&idBloque=A1_z1_b1&idConcesion=XXX&numEntradas=1&modo=IFRAME</UrlSitting>
          </Seat>
          <DynamicToken>pr1</DynamicToken>
          <Issue Mandatory = "false"/>
          <Attributes>
            <Attribute key = "availToken" value = "BpvkqOrfqU6ZpOqiJ0k21g=="/>
            <Attribute key = "modalityCode" value = "0#8"/>
            <Attribute key = "dateFrom" value = "20140320"/>
            <Attribute key = "dateTo" value = "20140320"/>
            <Attribute key = "limitAdult" value = "12"/>
            <Attribute key = "modeCode" value = "P"/>
          </Attributes>
        </TPA_Extensions>
      </BookingInfo>
    </OTA_TourActivityBookRQ>

|

ValuationRQ Description
=======================

  --------------------------------------------------------------------------
  Element              Num Type Description
                       ber      
  -------------------- --- ---- --------------------------------------------
  OTA\_TourActivityBoo 1        Root node.
  kRQ                           

  @PrimaryLangID       1   Stri Language code (ISO 3166-1 alpha-2) format..
                           ng   

  BookingInfo          0..      Information about specific ticket.
                       1        

  BookingInfo/BasicInf 0..      If need search by activity provider code.
  o                    1        

  @Name                0.. Stri Name of ticket.
                       1   ng   

  @TourActivityID      0.. Stri Code of ticket, mandatory if need search by
                       1   ng   activity provider code.

  BookingInfo/Schedule 1        Information about dates range on which you
                                can enjoy the activity.

  @StartPeriod         1   Date Start date that you apply availability.

  @EndPeriod           1   Date End date that you apply availability.

  BookingInfo/Category 0..      Category of Ticket.
  AndType              1        

  BookingInfo/Category 0..      Category of Ticket.
  AndType/Category     1        

  @Code                0.. Stri A category code from a predefined list, if
                       1   ng   Extension = "Other" then will be provider
                                code.

  @Extension           0.. Stri Enter a category here if you have selected
                       1   ng   "Other" from the pre-defined list.

  ParticipantCategory  0..      Information about participant type,
                       n        specifying age for each participant.

  @Age                 1   Inte Age of participant.
                           ger  

  Pricing/ParticipantC 0.. Stri Specifies participant type (Adult, Children
  ategory/QualifierInf 1   ng   or Baby). If value = Other then then is
  o                             mandatory specify Extension provider type.

  Pricing/ParticipantC 1        Specific price for each participantCategory.
  ategory/Price                 

  @Amount              1   Stri ParticipantCategory price.
                           ng   

  @CurrencyCode        0.. Stri Currency code (ISO 4217).
                       1   ng   

  Pricing/ParticipantC 0..      Necessary information that we need send
  ategory/TPA\_Extensi 1        between calls.
  ons                           

  Pricing/ParticipantC 0.. Stri Inform about the participant types to
  ategory/TPA\_Extensi 1   ng   valuate (if more than one type, the
  ons/DynamicToken              participant Types must be separated by ";").

  Pricing/ParticipantC 0..      Contains information about ticket printing.
  ategory/TPA\_Extensi 1        
  ons/Issue                     

  @Mandatory           0.. Bool Specifies if the ticket should be printed by
                       1   ean  the client.
  --------------------------------------------------------------------------

|

ValuationRS Example
===================

:

    <OTA_TourActivityBookRS>
        <ReservationDetails>
            <BasicInfo
                Name = "PALMA AQUARIUM"
                TourActivityID = "000200515"/>
            <Schedule StartPeriod = "2014-02-26T00:00:00" EndPeriod = "2014-02-27T00:00:00"/>
             <PickupDropoff OtherInfo="El cliente puede canjear el bono en la oficina de billetes de La Reserva  en Predio Son Net s/n 07194 Puigpunyent
            Abierto todos los das del ao.
            Verano: de 10:00h a 19:00h
            Invierno: de 10:00h a 18:00h  

            El cliente no puede olvidar llevar su documento de identidad.

            En caso de emergencia, el cliente deber llamar al siguiente nmero: (+34) 902 430 419
             " />

            <!--Pricing. -->
            <Pricing>
                <Summary Amount = "19.660" CurrencyCode = "EUR">
                    <PricingType Extension = "PerTotal">Other_</PricingType>
                </Summary>
                <ParticipantCategory age = "30">
                    <QualifierInfo>Adult</QualifierInfo>
                    <Price
                        Amount = "19.660"
                        CurrencyCode = "EUR"/>
                </ParticipantCategory>
            </Pricing>  
        <TPA_Extensions>
              <Attributes>
                <Attribute key = "purchaseToken" value = ""> </Attribute>
                <Attribute key = "SPUI" value = ""> </Attribute>        
                <Attribute key = "limitAdult" value="16"> </Attribute>              
              </Attributes>
            </TPA_Extensions>           
        </ReservationDetails>
    </OTA_TourActivityBookRS>

|

ValuationRS Description
=======================

  -------------------- -- --- --------------------------------------------
  @StartPeriod         1  Dat Start date that you apply availability.
                          e   

  @EndPeriod           1  Dat End date that you apply availability.
                          e   

  BookingInfo/Category 0.     Category of Ticket.
  AndType              .1     

  BookingInfo/Category 0.     Category of Ticket.
  AndType/Category     .1     

  @Code                0. Str A category code from a predefined list, if
                       .1 ing Extension = "Other" then will be provider
                              code.

  @Extension           0. Str Enter a category here if you have selected
                       .1 ing "Other" from the pre-defined list.

  ReservationDetails/P 0.     The pickup and/or dropoff information if
  ickupDropoff         .1     transportation is provided to/ from the
                              tour/activity location.

  @OtherInfo           0. Str Other instructions pertaining to the pickup/
                       .1 ing dropoff.

  ParticipantCategory  0.     Information about participant type,
                       .n     specifying age for each participant.

  @Age                 1  Int Age of participant.
                          ege 
                          r   

  Pricing/ParticipantC 0. Str Specifies participant type (Adult, Children
  ategory/QualifierInf .1 ing or Babie). If value = "Other\_" then then is
  o                           mandatory specify Extension provider type.

  Pricing/ParticipantC 1      Specific price for each participantCategory.
  ategory/Price               

  @Amount              1  Str ParticipantCategory price.
                          ing 

  @CurrencyCode        0. Str Currency code (ISO 4217).
                       .1 ing 

  Pricing/ParticipantC 0.     Necessary information that we need send
  ategory/TPA\_Extensi .1     between calls.
  ons                         

  Pricing/ParticipantC 0. Str Inform about the participant types to
  ategory/TPA\_Extensi .1 ing valuate (if more than one type, the
  ons/DynamicToken            participant Types must be separated by ";").

  Pricing/ParticipantC 0.     Contains information about ticket printing.
  ategory/TPA\_Extensi .1     
  ons/Issue                   

  @Mandatory           0. Boo Specifies if the ticket should be printed by
                       .1 lea the client.
                          n   
  -------------------- -- --- --------------------------------------------

|
