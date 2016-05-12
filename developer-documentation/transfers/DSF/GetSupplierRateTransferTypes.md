---
title: GetSupplierRateTransfersTypes
keywords: transfers, get supplier rates, transfers types
sidebar: mydoc_sidebar
permalink: /developer-documentation/transfers/DSF/GetSupplierRateTransfersTypes
---

|

Method Goals
============

This method aims to retrieve a list of the suppliers including their
rates.

|

Remarks
=======

|

GetSupplierRateTransfersTypesRQ Example
=======================================

    <GetSupplierRateTransferTypesRQ>
    <timeoutMilliseconds>60000</timeoutMilliseconds>
    <source>
    <languageCode>en</languageCode>
    </source>
    <filterAuditData>
    <registerTransactions>false</registerTransactions>
    </filterAuditData>
    <Configuration codeProvider = "XXXXX">
    <Credentials user = "" password = "">
    <UrlGeneric>http://examples-com</UrlGeneric>
    </Credentials>
    <Attributes/>
    </Configuration>
    </GetSupplierRateTransferTypesRQ>

|

GetSuppliersRateTransfersTypesRQ Description
============================================

  -------------------------------------------------------------------------
  Element          Numbe Type  Description
                   r           
  ---------------- ----- ----- --------------------------------------------
  GetSupplierRateT 1           Root node.
  ransfersTypesRQ              
  -------------------------------------------------------------------------

|

GetSupplierRateTransfersTypesRS Example
=======================================

    <GetSupplierRateTransferTypesRS>
    <auditData>
    <timeStamp>2014-10-30T11:32:29.8466879+00:00</timeStamp>
    <processTimeMilliseconds>0</processTimeMilliseconds>
    </auditData>
    <operationImplemented>true</operationImplemented>
    <Suppliers>
    <Supplier id = "ext-3">
        <Rates>
            <Rate id = "7" name = "OWShuttle"/>
            <Rate id = "6" name = "RT"/>
            <Rate id = "3" name = "Rate1"/>
            <Rate id = "19" name = "RateAudit"/>
            <Rate id = "13" name = "RateAudit"/>
            <Rate id = "4" name = "Rate2"/>
            <Rate id = "15" name = "Comas Privado 5 - 8 RT"/>
            <Rate id = "11" name = "Comas Privado 13 - 20"/>
            <Rate id = "9" name = "Comas Privado 5 - 8"/>
            <Rate id = "8" name = "Comas Privado 1 - 4"/>
            <Rate id = "16" name = "Comas Privado 9 - 12 RT"/>
            <Rate id = "12" name = "Comas Privado 21 - 31"/>
            <Rate id = "17" name = "Comas Privado 13 - 20 RT"/>
            <Rate id = "14" name = "Comas Privado 1 - 4 RT"/>
            <Rate id = "10" name = "Comas Privado 9 - 12"/>
            <Rate id = "18" name = "Comas Privado 21 - 31 RT"/>
        </Rates>
    </Supplier>
    <Supplier id = "ext-2"/>
    <Supplier id = "ext-4"/>
    </Suppliers>
    </GetSupplierRateTransferTypesRS>

|

GetSupplierRateTransfersTypesRS Description
===========================================

  ------------------------------------------------------------------------
  Element           Num Typ Description
                    ber e   
  ----------------- --- --- ----------------------------------------------
  GetSupplierRateTr 1       Root node.
  ansfersTypesRS            

  GetSupplierRateTr 1       List of suppliers.
  ansfersTypesRQ/Su         
  ppliers                   

  Suppliers/Supplie 1       Supplier.
  r                         

  @id               1   Str Indicates the supplier identifier.
                        ing 

  @territoryId      1   Str The identifier of the territory where the
                        ing supplier operates.

  Supplier/Rates    1   Str List of rates.
                        ing 

  Supplier/Rates/Ra         
  te                        

  @id               1   Str Code of the rate.
                        ing 

  @name             1   Str Name of the rate.
                        ing 

  TransferTypes     1       Contains a list of TransferType. Each
                            TransferType contains information about the
                            types of transfer that are available for this
                            rate.

  TransferTypes/Tra 1..     Contains information related to a type of
  nsferType         n       transfer.

  @id               1   Str Code of the TransferType.
                        ing 

  @name             1   Str Name of the TransferType.
                        ing 

  TransferType/Vehi 1       Contains a list of vehicles included in this
  cles                      TransferType category.

  TransferType/Vehi 1..     Contains a vehicle name and its id.
  cles/Vehicle      n       

  @id               1   Str Code of the vehicle.
                        ing 

  @name             1   Str Name of the vehicle.
                        ing 
  ------------------------------------------------------------------------

|
