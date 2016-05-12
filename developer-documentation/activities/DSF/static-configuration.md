---
title: Static Configuration
keywords: activities, data structure, static configuration
sidebar: mydoc_sidebar
permalink: /developer-documentation/activities/DSF/static-configuration
---

|

Method Goals
============

This method returns important information about the behaviour of the
integration (specific provider).

|

Request Format
==============

The request only requires the provider code and credentials.

|

Response Format
===============

The response contains a list of basic information about the limitations
of the integration / provider.

**OpenAvailability**

-   OpenAvailability = false: Need specify passangers in avail request.
    In response, provider return price of option that you specify.
-   OpenAvailability = true: Not neccesary specify passangers in avail
    request. In this case provider return all possible participant types
    that can provide, and you can choose the participants types that you
    are interested.

**Range**

-   Range = R: Range date, means that provider return options beetwen
    range of dates send in Avail request, anyone who is between these
    dates.
-   Range = S: Specific date, means that provider return options for
    specific range of dates send in Avail request.

|

StaticConfigurationRQ Example
=============================

:

    <StaticConfigurationRQ xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
      <timeoutMilliseconds>60000</timeoutMilliseconds>
      <filterAuditData>
        <registerTransactions>false</registerTransactions>
      </filterAuditData>
      <Configuration codeProvider="XXX">
        <Credentials user="XXXX" password="XXXXX">
          <UrlGeneric>www.test.com</UrlGeneric>
          <UrlIdentification xsi:nil="true" />
          <UrlAvailability xsi:nil="true" />
          <UrlBook xsi:nil="true" />
          <UrlsSpecific xsi:nil="true" />
        </Credentials>
        <Attributes>
          <Attribute key="destinationId" value="
          Testing.com" />
          <Attribute key="destinationName" value="Testing.com" />
        </Attributes>
      </Configuration>
    </StaticConfigurationRQ>

|

StaticConfigurationRQ Description
=================================

  --------------------------------------------------------------------------
  Element               Numbe Type   Description
                        r            
  --------------------- ----- ------ ---------------------------------------
  StaticConfigurationRQ 1            Root node.

  timeoutMilliseconds   1     Intege Timeout in milliseconds that client
                              r      will be waiting the response.

  source                1            Information about source requesting the
                                     operation.

  source/languageCode   1     String Language code (ISO 3166-1 alpha-2)
                                     format.

  filterAuditData       1            Information about enable or disable
                                     information returned in audit data.

  filterAuditData/regis 1     Boolea If true, registers the transactions
  terTransactions             n      with provider.

  Configuration         1            Information about source requesting the
                                     operation.

  @codeProvider         1     String Agency code of the provider.

  Configuration/Credent 1            Provider credentials.
  ials                               

  Configuration/Credent 0..1  String User code for connection.
  ials/User                          

  Configuration/Credent 0..1  String Password for connection.
  ials/Password                      

  Configuration/Credent 0..1  String Url generic connection.
  ials/UrlGeneric                    

  Configuration/UrlAvai 0..1  String Url for Avail method.
  l                                  

  Configuration/UrlValu 0..1  String Url for Valuation method.
  ation                              

  Configuration/UrlBook 0..1  String Url for Reservation method.

  Configuration/Attribu 0..1         Parameters for additional information.
  tes                                

  Configuration/Attribu 0..n         List of parameter.
  tes/Attribute                      

  <*@key>\*             1     String Contains the keyword/Id to identify a
                                     parameter.

  <*@value>\*           1     String Contains the value of the parameter
  --------------------------------------------------------------------------

|

StaticConfigurationRS Example
=============================

:

    <StaticConfigurationRS xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
      <operationImplemented>true</operationImplemented>
      <NumOfDestinations>1</NumOfDestinations>
      <NumOfEvents>0</NumOfEvents>
      <NumOfEventTypes>0</NumOfEventTypes>
      <DateRange>
        <Range>S</Range>
        <MaxDays>5</MaxDays>
      </DateRange>
      <Languages>
        <Language>es</Language>
      </Languages>
      <OpenAvailability>false</OpenAvailability>
      <NumMaxParticipants>12</NumMaxParticipants>
    </StaticConfigurationRS>

|

StaticConfigurationRS Description
=================================

  -------------------------------------------------------------------------
  Element  Num Type Description
           ber      
  -------- --- ---- -------------------------------------------------------
  StaticCo 1        Root node.
  nfigurat          
  ionRS             

  NumOfDes 1   Inte Number of destination that specific integration can
  tination     ger  provider/returned in one same Avail.
  s                 

  NumOfEve 1   Inte Number of TourActivityID that specific integration can
  nts          ger  provider/returned in one same Avail.

  NumOfEve 1   Inte Number of Category Code that specific integration can
  ntTypes      ger  provider/returned in one same Avail.

  DateRang 1        Number of destination that specific integration can
  e                 provider in one same Avail.

  Range    1   Enum Type of range that identifying how we can get the
                    different options for each activity depending on the
                    date range sent on Avail request.

  MaxDays  1   Inte Maximum of days that you can send in Avail request. In
               ger  case that we return 999, means that the provider
                    doesn't specify a maximum. (Possibles case: "R" or "S")

  Language 1        List of languages that provider can return different
  s                 response.

  Language 1.. Stri Language code (ISO 3166-1 alpha-2) format.
  s/Langua n   ng   
  ge                

  OpenAvai 1   Bool Type of provider, the difference is in avail response.
  lability     ean  

  NumMaxPa 1   Inte Maximum number of participants/Tickets you can request
  rticipan     ger  in availability.
  ts                
  -------------------------------------------------------------------------

|
