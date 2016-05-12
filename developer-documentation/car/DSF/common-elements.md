---
title: Common Elements
keywords: transfers, data structure, common elements
sidebar: mydoc_sidebar
permalink: /developer-documentation/car/DSF/common-elements
---


This node will be in every request and response objects.

The request objects contains the supplier's configuration, urls and
credentials.

The response object contains the operation status and errors if any.

|

Common Elements RQ Example
==========================

:

    <CarBaseRQ>
       <timeoutMilliseconds>20000</timeoutMilliseconds>
       <filterAuditData>
          <registerTransactions>true</registerTransactions>
       </filterAuditData>
       <Configuration ProviderCode="xx">
          <Credentials user="testUser" password="testPass">
             <genericURL>https://xxx</genericURL>
             <identificationURL>https://xxx</identificationURL>
             <availRateURL>https://xxx</availRateURL>
             <rateRuleURL>https://xxx</rateRuleURL>
             <vehResURL>https://xxx</vehResURL>
             <specificURLs />
          </Credentials>
          <Attributes />
       </Configuration>
       <ClientConfiguration agency = "agencyName" SellCurrency = "EUR"/>
       …
    </CarBaseRQ>

|

Common Elements RQ Description
==============================

  -------------------------------------------------------------------------
  Element            Numbe Type          Description
                     r                   
  ------------------ ----- ------------- ----------------------------------
  CarBaseRQ          1                   Root node.

  echoToken          0..1  String        Echo token to be returned in
                                         response (valid for test
                                         purposes).

  timeoutMillisencod 1     Integer       Timeout in milliseconds that the
  s                                      client will be waiting for a
                                         response.

  source             1     source        Information about source
                                         requesting the operation.

  source/agencyCode  0..1  String        Agency code that requests the
                                         operation.

  source/languageCod 1     String        Language code (ISO 3166-1 alpha-2)
  e                                      format.

  filterAuditData    1     FilterAuditDa Information about enable or enable
                           ta            information returned in audit
                                         data.

  filterAuditData/re 1     Boolean       Active register of transactions
  gisterTransactions                     with provider.

  CarBaseRQ/Configur 1     Configuracion Configuration needed to send the
  ation                    Proveedor     transaction to the provider.

  @Configuration/Pro 1     String        Provider's code.
  viderCode                              

  Configuration/Cred 1     Configuracion Connection credentials.
  entials                  Credenciales  

  @Credentials/user  1     String        User of the session for the
                                         connection.

  @Credentials/passw 1     String        Password of the session for the
  ord                                    connection.

  Credentials/generi 0..1  String        Generic URL.
  cURL                                   

  Credentials/identi 0..1  String        Specific URL for identification.
  ficationURL                            

  Credentials/availR 0..1  String        Specific URL for OTA\_VehAvailRate
  ateURL                                 operation.

  Credentials/rateRu 0..1  String        Specific URL for OTA\_VehRateRule
  leURL                                  operation.

  Credentials/vehRes 0..1  String        Specific URL for OTA\_VehRes
  URL                                    operation.

  Credentials/specif 0..1  Atributos     Specific URLs organized in
  icURLs                                 Key/value pairs.

  Credentials/specif 0..1  Atributos     Specific parameter configuration
  icURLs/                                for this connector.
  Configuration/Attr                     
  ibutes                                 

  Configuration/Attr 0..n  List of       List of Atributo.
  ibutes/Attribute         Atributo      

  @Atributo/key      1     String        Unique key that identifies the
                                         value.

  @Atributo/value    1     String        Value of the Atributo.

  @Atributo/value    1     String        Value of the Atributo.

  CarBaseRQ/ClientCo 1     Configuracion Client configuration information.
  nfiguration              Cliente       

  @ClientConfigurati 1     String        Agency name.
  on/agency                              

  @ClientConfigurati 1     String        Preferred currency code.
  on/SellCurrency                        
  -------------------------------------------------------------------------

|

Common Elements RS Example
==========================

:

    <CarBaseRS>
       <operationImplemented>true</operationImplemented>
       <Errors>
            <Error Code = "101" ShortText = "3">Unable to make a reservation</Error>
       </Errors>
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
       <Warnings>
         <Warning Code = " " text = " " />
       </Warnings>
       …
    </CarBaseRS>

|

Common Elements RS Description
==============================

  ------------------------------------------------------------------------
  Element    Num Type   Description
             ber        
  ---------- --- ------ --------------------------------------------------
  CarBaseRS  1          Root node.

  CarBaseRS/ 0.. String This object doesn't contain any information. A
  Success    1          response with a "Success" object indicates that
                        everything went ok.

  CarBaseRS/ 0.. Warnin Contains a list of warning elements. Important but
  Warnings   1   gs     non critical information returned in the
                        provider's response is shown in this object.

  Warning/co 1   String A code that identifies the warning.
  de                    

  Warning/te 1   String Message of the warning.
  xt                    

  CarBaseRS/ 0.. Errors Contains a list of error elements. Important and
  Errors     1          critical information returned in the provider's
                        response is shown in this object.

  Errors/Err 0.. List   Important and critical information returned in the
  or         n   of     provider's response is shown in this object.
                 MyErro 
                 r      

  @Error/Cod 1   errorC Code that indicates the error type.
  e              odesTy 
                 pe     

  @Error/Sho 1   String Brief description of the returned error.
  rtText                

  Error/text 1   String Complete error message.

  CarBaseRS/ 1   AuditD In case registerTransactions has been set to true
  auditData      ata    on the request this object will provide
                        information about the communication with the
                        provider. Otherwise it will be null.

  auditData/ 1   List   Object that contains information of a transaction
  Transactio     of     sent to the provider's system.
  ns             Transa 
                 ction  

  transactio 1   timeSt Indicates the time in which the message has been
  n/timeStam     amp    sent.
  p                     

  transactio 1   String Serialized request object sent to the provider.
  n/RQ                  

  transactio 1   String Serialized response object sent to the provider.
  n/RS                  

  auditData/ 1   TimeSt Time in which our response has been generated.
  timeStamp      amp    

  auditData/ 1   Intege Time in milliseconds consumed by this method.
  processTim     r      (currently unused).
  eMilliseco            
  nds                   
  ------------------------------------------------------------------------

|
