---
title: Common Elements
keywords: transportation, data structure, ferries, common elements
sidebar: mydoc_sidebar
permalink: /developer-documentation/transportation/DSF/ferries/common-elements
---

|

Introduction
============

In every petition there some nodes which will always appear, there for
this chapter is dedicated for said nodes.

|

Request Format
==============

The common elements in all of the petitions are: source of the petition,
Timeout, the indication if you wish to register the transactions and the
provider configuration.

|

Response Format
===============

The response will contain the indication if the function is implemented
or not, application errors, if any, the providers traces if requested
and the response status.

|

Common Elements RQ Example
==========================

:

    <TransportationBaseRQ>
       <source>
          <agencyCode>XXXXX</agencyCode>
          <languageCode>es</languageCode>
       </source>
       <timeoutMilliseconds>20000</timeoutMilliseconds>
       <filterAuditData>
          <registerTransactions>true</registerTransactions>
       </filterAuditData>
       <Configuration codigoProveedor="xx">
          <Credenciales User="xx " Password="xx">
             <UrlGeneric>https://xxx</UrlGeneric>
             <UrlAvail>https://xxx</UrlAvail>
             <UrlValuation>https://xxx</UrlValuation>
             <UrlReservation>https://xxx</UrlReservation>
             <UrlsEspecificas />
          </Credenciales>
       </Configuration>
       …
    </TransportationBaseRQ>

|

Common Elements RQ Description
==============================

  -------------------------------------------------------------------------
  Element          Numb Type Description
                   er        
  ---------------- ---- ---- ----------------------------------------------
  TransportationBa 1         Root node.
  seRQ                       

  timeoutMillisenc 1    Inte Timeout in milliseconds that the client will
  ods                   ger  be waiting for the response.

  source           1         Information about source requesting the
                             operation.

  source/agencyCod 0..1 Stri Agency code that requests the operation.
  e                     ng   

  source/languageC 1    Stri Language code (ISO 3166-1 alpha-2) format
  ode                   ng   lowercase.

  filterAuditData  1         Enables or disables information returned in
                             audit data.

  filterAuditData/ 1    Bool Returns all the transactions (XMLs) exchanged
  registerTransact      ean  with the provider.
  ions                       

  Configuration    1         Information about source requesting the
                             operation.

  Configuration/Us 0..1 Stri User code for connection.
  er                    ng   

  Configuration/Pa 0..1 Stri Password for the connection.
  ssword                ng   

  Configuration/Ur 0..1 Stri Url generic connection.
  lGeneric              ng   

  Configuration/Ur 0..1 Stri Url for Avail method.
  lAvail                ng   

  Configuration/Ur 0..1 Stri Url for Valuation method.
  lValuation            ng   

  Configuration/Ur 0..1 Stri Url for Reservation method.
  lReservation          ng   

  Configuration/Pa 0..1      Parameters for additional information.
  rameters                   

  Configuration/Pa 0..n      List of parameter.
  rameters/Paramet           
  er                         

  <*@key>\*        1    Stri Contains the keyword/Id to identify a
                        ng   parameter.

  <*@value>\*      1    Stri Contains the value of the parameter
                        ng   

  ClientConfigurat 1         Client's configuration.
  ion                        

  <*@agency>\*     1    Stri Agency name.
                        ng   

  <*@mark>\*       1    Stri Mark.
                        ng   

  <*@businessLine> 1    Stri Business line.
  \*                    ng   

  <*@accessLevel>\ 1    Stri Access level.
  *                     ng   

  <*@mean>\*       1    Stri Mean.
                        ng   

  <*@accessType>\* 1    Stri Access type: WEB (Web) and WS (WebService).
                        ng   

  <*@currencyCode> 1    Stri Currency code.
  \*                    ng   
  -------------------------------------------------------------------------

|

Common Elements RS Example
==========================

:

    <TransportationBaseRS>
       <operationImplemented>true</operationImplemented>
       <applicationErrors>
          <ApplicationError>
             <type>102</type>
             <code>xxx</code>
             <description>xxx</description>
          </ApplicationError>
       </applicationErrors>
       <auditData>
          <transactions>
             <Transaction>
                <timeStamp>2011-10-6T15:19:45.3544495+02:00</timeStamp>
                <RQ />
                <RS />
             </Transaction>
          </transactions>
          <timeStamp>2011-10-26T15:19:43.4014745+02:00</timeStamp>
          <processTimeMilliseconds>19532</processTimeMilliseconds>
       </auditData>
       <EstadoRespuesta tripType = "IDA" petitionType = "OW" status = "ok"/>
       …
    </TransportationBaseRS>

|

Common Elements RS Description
==============================

  --------------------------------------------------------------------------
  Element               Number Type   Description
  --------------------- ------ ------ --------------------------------------
  TransportationBaseRS  1             Root node.

  OperationImplemented  1      Boolea If the operation is implemented by
                               n      this provider or not.

  applicationErrors     0..n          Application errors reported by
                                      provider.

  applicationErrors/typ 1      String Error Type as specified by XML
  e                                   Travelgate.

  applicationErrors/cod 1      String Native error code reported by
  e                                   provider.

  applicationErrors/des 1      String Error description.
  cription                            

  auditData             1             Information about processing that
                                      transaction.

  auditData/transaction 0..n          List of transactions communicated with
  s                                   provider.

  auditData/transaction 1      Intege TimeStamp in which has been generated
  s/timeStamp                  r      that transaction.

  auditData/transaction 1      String Transaction Request.
  s/RQ                                

  auditData/transaction 1      String Transaction Response.
  s/RS                                

  auditData/timeStamp   1      Intege imeStamp in which response has been
                               r      generated

  auditData/processTime 1      Intege Time in milliseconds consumed by this
  Milliseconds                 r      method.

  EstadoRespuesta       1             Status of the ticket.

  <*@tripType>\*        1      String Journey type.

  <*@petitionType>\*    1      String Petition type: OW or RT.

  <*@status>\*          1      String Status.
  --------------------------------------------------------------------------

|
