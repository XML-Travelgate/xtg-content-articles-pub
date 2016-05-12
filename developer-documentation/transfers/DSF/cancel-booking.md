---
title: CancelBooking
keywords: transfers, cancel booking
sidebar: mydoc_sidebar
permalink: /developer-documentation/transfers/DSF/cancel-booking
---

|

Method Goals
============

This method aims to cancel a booking.

|

CancelBookingRQ Example
=======================

    <CancelBookingRQ>
    <timeoutMilliseconds>XXXX</timeoutMilliseconds>
    <source>
        <agencyCode>XXXX</agencyCode>
        <languageCode>es</languageCode>
    </source>
    <filterAuditData>
        <registerTransactions>false</registerTransactions>
    </filterAuditData>
    <Configuration codeProvider = "XXX">
        <Credentials user = "XXX" password = "XXX">
            <UrlGeneric>http://examples.com</UrlGeneric>
            <UrlIdentification>http://examples.com</UrlIdentification>
            <UrlAvailability xsi:nil = "true"/>
            <UrlRateRule xsi:nil = "true"/>
            <UrlBook xsi:nil = "true"/>
            <UrlsSpecific xsi:nil = "true"/>
        </Credentials>
        <Attributes/>
    </Configuration>
    <Locator id = "94" type = "PROVIDER"/>

\</CancelBookingRQ\>

|

CancelBookingRQ Description
===========================

  -------------------------------------------------------------------------
  Element     Numbe Type  Description
              r           
  ----------- ----- ----- -------------------------------------------------
  CancelBooki 1           Root node.
  ngRQ                    
  -------------------------------------------------------------------------

|

CancelBookingRS Example
=======================

    <CancelBookingRS xmlns:xsd = "http://www.w3.org/2001/XMLSchema" xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance">
    <auditData>
        <timeStamp>2015-03-05T10:54:41.5860766+01:00</timeStamp>
        <processTimeMilliseconds>0</processTimeMilliseconds>
    </auditData>
    <operationImplemented>true</operationImplemented>
    <Locators>
        <Locator id = "ABCD" type = "CLIENT"/>
        <Locator id = "XYZ" type = "PROVIDER"/>
    </Locators>
    <CanceledRates>
        <CanceledRate id = "74" providerCode = "5" providerExternalCode = "UXB-A07012339" rateType = "RT">
          <SelectedOptions>
                    <SelectedOption status = "NEW" id = "0">
                        <Transfers>
                            <Transfer id = "0">
                                <Info type = "BUS" code = "XXX" typeVeh = "XXX">
                                    <vendorMessages>
                                        <vendorMessage>
                                            <Tittle>XXXX</Tittle>
                                            XXXXXXXXXX
                                        </vendorMessage>
                                    </vendorMessages>
                                </Info>
                                <LocOrigin type = "ARP" code = "XXX" date = "2014-09-19T00:00:00"/>
                                <LocDestination type = "HOT" code = "XXX" date = "2014-09-19T00:00:00"/>
                            </Transfer>
                        </Transfers>
                        <Parameters></Parameters>
                    </SelectedOption>
                </SelectedOptions>
            <CancellationPenalty currency = "EUR" amount = "0" priceType = "NET" commission = "0"/>
        </CanceledRate>
    </CanceledRates>
    <ReservationStatus>CANCELLED</ReservationStatus>

\</CancelBookingRS\>

|

GetTransferTypesRS Description
==============================

  --------------------------------------------------------------------------
  Element    Nu Type  Description
             mb       
             er       
  ---------- -- ----- ------------------------------------------------------
  CancelBook 1        Root node.
  ingRS               

  @id        1  Strin Code of the supplement. Sole codes.
                g     

  @name      1  Strin Name of the supplement.
                g     

  CancelBook 0.       
  ingRS/Loca .1       
  tors                

  CancelBook 1. Locat Contains the locator of the provider's system.
  ingRS/Loca .n or    
  tors/Locat          
  or                  

  CancelBook 1  Strin The code that's identifies the reservation in the
  ingRS/Loca    g     provider's system.
  tors/Locat          
  or/id               

  CancelBook 1  eLoca Indicates the type of the locator. The possible values
  ingRS/Loca    torTy are: **PROVIDER**.
  tors/Locat    pe    
  or/type             

  CancelBook 0. Rate  If the provider returns information related to the
  ingRS/Canc .1       cancelled rates, this will be returned.
  eledRates           

  CancelBook 1. Selec Contains a list of SelectedRate.
  ingRS/Canc .n tedRa 
  eledRates/    te    
  CancelledR          
  ate                 

  @SelectedR 1  Integ This id identifies the rate.
  ate/id        er    

  @SelectedR 1  Strin Contains the code of the rate if the provider returns
  ate/code      g     it.

  @SelectedR 1  Strin Contains the code of the provider that offers this
  ate/provid    g     rate.
  erCode              

  @SelectedR 1  eRate Indicates if the rate is OW (one-way) or RT (return).
  ate/rateTy    Type  
  pe                  

  @SelectedR 1  Selec Contains a list of SelectedOptions that belong to this
  ate/Select    tedOp rate.
  edOptions     tions 

  @SelectedR 1. Selec Contains a list of SelectedOption.
  ate/Select .n tedOp 
  edOptions/    tion  
  SelectedOp          
  tion                

  @SelectedO 1  Strin Indicates the status of the option if the provider
  ption/stat    g     returns this information. This is a plain text of the
  us                  status returned by the provider, this means that each
                      provider may send it's own status codes/messages.

  @SelectedO 1  Integ This code identifies the option.
  ption/id      er    

  @SelectedO 1  Segme Contains the segment which is served with this option.
  ption/Segm    nt    
  ent                 

  @SelectedO 1  Trans Contains a list of different transfers that serve the
  ption/Tran    fers  segment of this option.
  sfers               

  @SelectedO 1. Trans Contains a list of transfers which is served with this
  ption/Tran .n fer   option.
  sfers/Tran          
  sfer                

  @SelectedO 1  Param Contains a list of Parameter objects. The parameter
  ption/Para    eters returned in AvailabilityRS should be received by the
  meters              integration on RateRuleRQ.

  @SelectedR 1  Price Contains information about the price of this rate. If
  ate/TotalR          the rate is OW this price correspond to each option
  ate                 included in this *SelectedRate* object, if the rate is
                      RT correspond to the pair of options included in this
                      *SelectedRate* object.

  @SelectedR 1  Cance Contains a list of conditions of the penalties for the
  ate/Cancel    llati cancellation of the reservation. This object normaly
  lationPoli    onPol is not used because in this moments the providers not
  cy            icies return this informacion in *AvailabilityRS*, if there
                      are any will be returned in *RateRuleRS*.
  --------------------------------------------------------------------------

|
