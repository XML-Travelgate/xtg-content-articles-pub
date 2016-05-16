---
title: Availability
keywords: transfers, data structure, availability
sidebar: mydoc_sidebar
permalink: /developer-documentation/car/DSF/avail
---

|

Method Goals
============

This method aims to return all the available options for a given date
and offices.

|

Remarks
=======

This method **must** be called **before** the OTA VehRateRule method.

|

OTA VehAvailRateRQ Example
==========================



    <OTA_VehAvailRateRQ>
        <timeoutMilliseconds>60000</timeoutMilliseconds>
      <filterAuditData>
        <registerTransactions>true</registerTransactions>
      </filterAuditData>
      <Configuration ProviderCode="AVI">
        <Credentials user="testuser" password="testpass">
          <genericURL>https://testURL</genericURL>
          <identificationURL xsi:nil="true" />
          <availRateURL xsi:nil="true" />
          <rateRuleURL xsi:nil="true" />
          <vehResURL xsi:nil="true" />
          <specificURLs xsi:nil="true" />
        </Credentials>
        <Attributes>
          <Attribute key="RateCategory" value="2" />
        </Attributes>
      </Configuration>
      <ClientConfiguration agency="testAgency" SellCurrency="EUR" />
      <POS>
        <Source ISOCountry="ESP">
          <RequestorID Type="LAN" ID="es" />
        </Source>
      </POS>
      <VehAvailRQCore>
        <VehRentalCore PickUpDateTime="2014-04-07T12:00:00" ReturnDateTime="2014-04-14T12:00:00">
          <PickUpLocation LocationCode="SXF" CodeContext="IATA" />
          <ReturnLocation LocationCode="SXF" CodeContext="IATA" />
        </VehRentalCore>
        <DriverType Age="30" />
      </VehAvailRQCore>
      <VehAvailRQInfo>
        <Customer>
          <Primary>
            <CitizenCountryName Code="ES" />
          </Primary>
        </Customer>
      </VehAvailRQInfo>
    </OTA_VehAvailRateRQ>

|

OTA VehAvailRateRQ Description
==============================

The availability request is very straight forward. It only requires the
offices (airport ISO code, office code or city code), the required dates
and a few other optional filters.

|

| **Element**				| **Number**	| **Type**	| **Description**				|
| ------------------------------------- | ------------- | ------------- | --------------------------------------------- |
| OTA_VehAvailRateRQ			| 1         	|		| Root Node.					|
| OTA_VehAvailRateRQ/Configuration	| 1 		| ConfiguracionProveedor | Configuration needed to send the transaction to racionP the provider.  |
| OTA_VehAvailRateRQ/ClientConfiguration | 1		| ConfiguracionCliente | Client configuration information. 	|


  OTA_VehAvailRateRQ/POS 1  Pos     Contains information of the Point Of Sale.
               

  OTA\_VehAvai 1. List of Contains a list of SourceOTA
  lRateRQ/Pos/ .n SourceO 
  Source          TA      

  OTA\_VehAvai 1  SourceO This object has information on the market to
  lRateRQ/Pos/    TA      which the search belongs.
  Source/Sourc            
  eOTA                    

  @OTA\_VehAva 1  String  ISO code of the country of the requestor.
  ilRateRQ/Pos            
  /Source/Sour            
  ceOTA/ISOCou            
  ntry                    

  OTA\_VehAvai 1  List of An identifier of the entity making the request.
  lRateRQ/Pos/    Request Currently not used.
  Source/Sourc    orID    
  eOTA/Request            
  orID                    

  OTA\_VehAvai 1  VehAvai Contains the dates, locations and preferences for
  lRateRQ/VehA    lRQCore the availability search.
  vailRQCore              

  OTA\_VehAvai 1  VehRent Contains the dates and locations of the rental.
  lRateRQ/VehA    alCore  
  vailRQCore/V            
  ehRentalCore            

  OTA\_VehAvai 1  Locatio Location object that represents where the
  lRateRQ/VehA    n       customer is going to pick up the car.
  vailRQCore/P            
  ickupLocatio            
  n                       

  @Location/lo 1  String  Code that represents the location of the search
  cationCode              

  @Location/Co 1  eLocati Indicates the type of code. The possible values
  deContext       onCodeC are IATA, OFFICE and CITY.
                  ontextT 
                  ype     

  OTA\_VehAvai 1  Locatio Location object that represents where the
  lRateRQ/VehA    n       customer is going to return the car.
  vailRQCore/R            
  eturnLocatio            
  n                       

  OTA\_VehAvai 1  DateTim Indicates the date the customer wants to pick up
  lRateRQ/VehA    e       the car.
  vailRQCore/P            
  ickUpDateTim            
  e                       

  OTA\_VehAvai 1  DateTim Indicates the date the customer wants to return
  lRateRQ/VehA    e       the car.
  vailRQCore/R            
  eturnDateTim            
  e                       

  OTA\_VehAvai 1  VendorP Contains a list of VendorPref. A VendorPref is
  lRateRQ/Vend    refs    the vendor specific code used to identify a
  orPrefs                 special rate associated with a specific
                          organization. Used when multiple vendors have
                          been requested and there is a different code for
                          each.

  OTA\_VehAvai 1  List of List of VendorPref.
  lRateRQ/Vend    VendorP 
  orPrefs/Vend    ref     
  orPref                  

  @VendorPref/ 1  String  This is the vendor specific code used to identify
  CorpDiscount            a special rate associated with a specific
  Nmbr                    organization. Used when multiple vendors have
                          been requested and there is a different code for
                          each.

  OTA\_VehAvai 1  VehPref Contains a list of VehiclePref. A vehiclePref has
  lRateRQ/VehP    s       information related to the vehicle model.
  refs                    

  OTA\_VehAvai 1  List Of List of VehiclePref.
  lRateRQ/VehP    Vehicle 
  refs/VehPref    Pref    

  VehiclePref/ 1  Vehicle Information related to the car model.
  VehMakeModel    MakeMod 
                  elGroup 

  @VehiclePref 1  String  Name of the vehicle model in the provider's
  /VehMakeMode            system.
  l/name                  

  @VehiclePref 1  String  Código en formato SIPP.
  /VehMakeMode            
  l/Code                  

  @VehiclePref 1  String  The provider's code for the vehicle.
  /VendorCarTy            
  pe                      

  @VehiclePref 1  String  Indicates if the vehicle has air condition.
  /AirConditio            Possible values are "true" or "false".
  nInd                    

  @VehiclePref 1  String  Indicates the transmission type of the vehicle.
  /Transmissio            
  nType                   

  VehiclePref/ 1  Vehicle Specifies the vehicle category and the number of
  VehType         TypeGro doors.
                  up      

  VehicleTypeG 1  String  Indicates the category of the vehicle.
  roup/Vehicle            
  Category                

  VehicleTypeG 1  String  Indicates the number of doors of the vehicle.
  roup/doorCou            
  nt                      

  VehiclePref/ 1  Vehicle Contains the size of the vehicle.
  VehClass        ClassGr 
                  oup     

  @VehicleClas 1  String  Size of the vehicle.
  sGroup/Size             

  OTA\_VehAvai 1  DriverT Contains information related to the driver.
  lRateRQ/VehA    ype     
  vailRQCore/D            
  irverType               

  @DriverType/ 1  String  Indicates the age of the driver.
  Age                     

  OTA\_VehAvai 1  Vehicle Contains the information related to the customer.
  lRateRQ/VehA    AvailRQ 
  vailRQInfo      Additio 
                  nalInfo 
                  Type    

  OTA\_VehAvai 1  Custome Contains the information related to the customer.
  lRateRQ/VehA    rPrimar 
  vailRQInfo/C    yAdditi 
  ustomer         onal    

  OTA\_VehAvai 1  Primary Contains the information related to the customer.
  lRateRQ/VehA            
  vailRQInfo/C            
  ustomer/Prim            
  ary                     

  Primary/Pers 1  PersonN Contains the name of the customer.
  onName          ame     

  PersonName/G 1  String  Name of the customer.
  ivenName                

  PersonName/S 1  String  Surname of the customer.
  urname                  

  Primary/Tele 1  List of Contains the info of the customer's telephone.
  phone           Telepho 
                  ne      

  @Telephone/P 1  ePhoneT Type of technology used by the phone. Possible
  honeTechType    echnolo values: VOICE, DATA, FAX, PAGER ,MOBILE ,TTY
                  gyType  ,TELEX ,VOICE*OVER*IP.

  @Telephone/P 1  String  Number of the phone.
  honeNumber              

  Primary/Emai 1  Email   Specifies the email direction of the customer.
  l                       

  Primary/Emai 1  String  Text that represents the email of the customer.
  l/Text                  

  Primary/Docu 1  Documen Specifies the information of the document that
  ment            t       identificates the customer.

  Document/Doc 1  String  String that contains the DocumentID of the
  ID                      customer.

  Document/Doc 1  eDocume Represents the type of Document sent by the
  Type            ntType  customer.

  Primary/Addr 1  Address Contains the address of the customer.
  ess                     

  Address/Addr 1  List of A list that contains 1 or more addresses of the
  essLine         String  customer.

  Address/City 1  String  The name of the city where the customer lives.
  Name                    

  Address/Post 1  String  The postal code of the customer's address.
  alCode                  

  Address/Coun 1  Country This object contains the code of the country of
  tryName         Name    the customer.

  @CountryName 1  String  The country code in ISO3166 format.
  /Code                   

  CountryName/ 1  String  Name of the country.
  Text                    

  Primary/Citi 1  Citizen The country code of the driver.
  zenCountryNa    Country 
  me              NameGro 
                  up      

  @CitizenCoun 1  String  The country code of the driver.
  tryNameGroup            
  /Code                   

  Primary/birt 1  String  Birthdate in ISO 8601 prescribed format
  hdate                   (YYYY-MM-DD).
  -------------------------------------------------------------------------

|

OTA VehAvailRateRS Example
==========================

:

    <OTA_VehAvailRateRS xmlns = "" xmlns:xsd = "http://www.w3.org/2001/XMLSchema" xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance">
        <auditData>
            <transactions>
                <timeStamp>2014-02-24T09:36:27.5336632+00:00</timeStamp>
                <RQ></RQ>
                <RS></RS>
            </transactions>
            <timeStamp>2014-02-24T09:36:27.5336632+00:00</timeStamp>
            <processTimeMilliseconds>0</processTimeMilliseconds>
        </auditData>
        <operationImplemented>true</operationImplemented>
        <VehAvailRSCore>
            <VehRentalCore PickUpDateTime = "2014-04-07T12:00:00" ReturnDateTime = "2014-04-14T12:00:00">
                <PickUpLocation LocationCode = "SXF" CodeContext = "IATA"/>
                <ReturnLocation LocationCode = "SXF" CodeContext = "IATA"/>
            </VehRentalCore>
            <VehVendorAvails>
                <VehVendorAvail>
                    <VehAvails>
                        <VehAvail>
                            <VehAvailCore Status = "Available">
                                <Vehicle AirConditionInd = "true" TransmissionType = "MANUAL" VendorCarType = "FVMR">
                                    <VehType VehicleCategory = "2" doorCount = "0"/>
                                    <VehClass Size = "8"/>
                                    <VehMakeModel Name = "Group O - Ford Galaxy or similar" Code = "FVMR"/>
                                </Vehicle>
                                <RentalRate>
                                    <RateDistance Unlimited = "true" DistUnitName = "kilometer"/>
                                    <RateQualifier RateCategory = "2" CorpDiscountNmbr = "U617107" RateQualifier = "6Z"/>
                                    <VehicleCharges>
                                        <VehicleCharge Amount = "729.01" CurrencyCode = "EUR" TaxInclusive = "true" IncludedInRate = "true" Purpose = "VEHICLE_RENTAL">
                                            <Description>Minimum 1 Day(s)</Description>
                                        </VehicleCharge>
                                    </VehicleCharges>
                                </RentalRate>
                                <TotalCharge RateTotalAmount = "729.01" CurrencyCode = "EUR"/>
                                <Vendor Code = "Avis"/>
                                <VendorLocation LocationCode = "SXF" CodeContext = "IATA"/>
                                <DropOffLocation LocationCode = "SXF" CodeContext = "IATA"/>
                            </VehAvailCore>
                        </VehAvail>
                        <VehAvail>
                            <VehAvailCore Status = "Available">
                                <Vehicle AirConditionInd = "true" TransmissionType = "MANUAL" VendorCarType = "ECMR">
                                    <VehType VehicleCategory = "1" doorCount = "0"/>
                                    <VehClass Size = "3"/>
                                    <VehMakeModel Name = "Group A - Volkswagen Polo or similar" Code = "ECMR"/>
                                </Vehicle>
                                <RentalRate>
                                    <RateDistance Unlimited = "true" DistUnitName = "kilometre"/>
                                    <RateQualifier RateCategory = "2" CorpDiscountNmbr = "U617107" RateQualifier = "6Z"/>
                                    <VehicleCharges>
                                        <VehicleCharge Amount = "339.98" CurrencyCode = "EUR" TaxInclusive = "true" IncludedInRate = "true" Purpose = "VEHICLE_RENTAL">
                                            <Description>Minimum 1 Day(s)</Description>
                                        </VehicleCharge>
                                    </VehicleCharges>
                                </RentalRate>
                                <TotalCharge RateTotalAmount = "339.98" CurrencyCode = "EUR"/>
                                <Vendor Code = "Avis"/>
                                <VendorLocation LocationCode = "SXF" CodeContext = "IATA"/>
                                <DropOffLocation LocationCode = "SXF" CodeContext = "IATA"/>
                            </VehAvailCore>
                        </VehAvail>
                    </VehAvails>
                </VehVendorAvail>
            </VehVendorAvails>
        </VehAvailRSCore>
    </OTA_VehAvailRateRS>

|

OTA VehAvailRateRS Description
==============================

A list of VehAvail (Available vehicles) is returned. Each of this
vehAvails contains the details of the vehicle. The price returned should
be "all inclusive". All fares, taxes and discounts are already included
in the total price.

  -------------------------------------------------------------------------
  Element           Nu Type      Description
                    mb           
                    er           
  ----------------- -- --------- ------------------------------------------
  OTA\_VehAvailRate 1  | Root    
  RS                   Node      

  OTA\_VehAvailRate 1  VehAvailR Contains the received options of the
  RS/VehAvailRSCore    SCore     availability search.

  VehAvailRSCore/Ve 1  VehRental Contains the dates and locations of the
  hRentalCore          Core      rental.

  VehAvailRSCore/Ve 1  VehVendor Contains a List of VehAvail. Each vehAvail
  hVendorAvails        Avails    is a vehicle rental option.

  VehAvailRSCore/Ve 1  VehVendor List of VehAvail. Each vehAvail is a
  hVendorAvails/Veh    Avail     vehicle rental option.
  VendorAvail                    

  VehAvailRSCore/Ve 1  list of   List of VehAvail. Each vehAvail is a
  hVendorAvails/Veh    VehAvail  vehicle rental option.
  VendorAvail/VehAv              
  ails                           

  VehAvailRSCore/Ve 1. VehAvail  This is a rental option.
  hVendorAvails/Veh .n           
  VendorAvail/VehAv              
  ails/VehAvail                  

  VehAvail/VehAvail 1  VehAvailC Core of the option. It contains all the
  Core                 ore       information related to the vehicle, cost
                                 and included equipments.

  VehAvail/VehAvail 1  eInventor Status of the option. It's possible values
  Core/Status          yStatus   are Available, OnRequest and All.

  VehAvail/VehAvail 1  Vehicle   Includes information about the vehicle
  Core/Vehicle                   model.

  Vehicle/AirCondit 1  String    Indicates if the vehicle has air
  ionInd                         condition. Possible values are "true" or
                                 "false".

  Vehicle/Transmiss 1  eVehicleT Indicates the transmission type of the
  ionType              ransmissi vehicle.
                       onType    

  Vehicle/VehType   1  VehicleTy Specifies the vehicle category and the
                       peGroup   number of doors.

  Vehicle/VehClass  1  VehicleCl Contains the size of the vehicle.
                       assGroup  

  Vehicle/VehMakeMo 1  VehicleMa Contains information related to the
  del                  keModelGr vehicle model.
                       oup       

  Vehicle/PictureUR 1  String    Imagen del vehiculo.
  L                              

  @Vehicle/Passenge 1  String    Máx number of passengers permitted for
  rQuantity                      this car.

  @Vehicle/BaggageQ 1  String    Trunk capacity to transport luggage.
  uantity                        

  @Vehicle/VendorCa 1  String    Code of the vehicle in the provider's
  rType                          format.

  VehAvail/VehAvail 1  VehicleRe Contains information of the allowed
  Core/RentalRate      ntalRate  distance, the selected rate, and the
                                 associated charges.

  VehicleRentalRate 1  VehicleRa Information about the permitted distance
  /RateDistance        teDistanc for this rate.
                       eGroup    

  @VehicleRentalRat 1  Boolean   Indicates if the permitted distance is
  e/RateDistance/Un              unlimited.
  limited                        

  VehicleRentalRate 1  String    Indicates the quantity of permitted
  /RateDistance/Qua              distance.
  ntity                          

  VehicleRentalRate 1  eDistance Indicates the unit in which the quantity
  /RateDistance/Dis    UnitType  of distance is represented.
  tUnitName                      

  VehicleRentalRate 1  RateQuali Information about the rate.
  /RateQualifier       fier      

  VehicleRentalRate 1  String    OTA Classification Code.
  /RateQualifier/Ra              
  teCategory                     

  VehicleRentalRate 1  String    This is the vendor specific code used to
  /RateQualifier/Co              identify a special rate associated with a
  rpDiscountNmbr                 specific organization.

  VehicleRentalRate 1  String    This is the vendor specific code for rate
  /RateQualifier/Ra              codes (e.g. WES, 2A, DLY00).
  teQualifier                    

  VehicleRentalRate 1  List of   Charges associated to this rate.
  /VehicleCharges      VehicleCh 
                       argePurpo 
                       se        

  VehicleCharges/Ve 1. VehicleCh Charge associated to this rate.
  hicleCharge       .n argePurpo 
                       se        

  @VehicleChargePur 1  Decimal   Cost of the charge.
  pose/Amount                    

  @VehicleChargePur 1  String    Currency in which the amount is returned.
  pose/CurrencyCode              

  @VehicleChargePur 1  Boolean   Indicates if the taxes are already applied
  pose/TaxInclusive              to the amount.

  @VehicleChargePur 1  Boolean   Indicates if the amount of this charge has
  pose/IncludedInRa              been added to the total cost of the
  te                             rental.

  VehicleChargePurp 1  Descripti Text returned by the provider that
  ose/Description      on        describes the charge.

  Description/Text  1  String    Descriptive Text.

  @VehicleChargePur 1  eVehicleC Indicates the type of the charge.
  pose/Purpose         hargePurp 
                       oseType   

  VehAvail/VehAvail 1  List of   List of equipments for the vehicle.
  Core/PricedEquips    VehicleEq 
                       uipmentPr 
                       iced      

  VehAvail/VehAvail 1. VehicleEq Equipment for the vehicle.
  Core/PricedEquips .n uipmentPr 
  /PricedEquip         iced      

  @VehicleEquipment 1  Boolean   Indicates if the equipment is required.
  Priced/Required                

  VehicleEquipmentP 1  VehicleEq The included equipment associated to this
  riced/Equipment      uipment   VehicleEquipmentPriced.

  VehicleEquipment/ 1  eEquipmen Type of the equipment.
  EquipType            tType     

  VehicleEquipment/ 1  String    Quantity included.
  Quantity                       

  VehicleEquipment/ 1  Descripti Description of the equipment.
  Description          on        

  VehicleEquipmentP 1  VehicleCh Charge associated to this
  riced/Charge         argeType  VehicleEquipmentPriced.

  @VehicleChargeTyp 1  Decimal   Cost of the charge.
  e/Amount                       

  @VehicleChargeTyp 1  String    Currency in which the amount is returned.
  e/CurrencyCode                 

  @VehicleChargeTyp 1  Boolean   Indicates if the taxes are already applied
  e/TaxInclusive                 to the amount.

  @VehicleChargeTyp 1  String    Indicates if the amount of this charge has
  e/IncludedInRate               been added to the total cost of the
                                 rental.

  VehicleChargeType 1  Descripti Text returned by the provider that
  /Description         on        describes the charge.

  VehAvail/VehAvail 1  VehicleTo Total cost of the rental.
  Core/TotalCharge     talCharge 
                       Group     

  @VehicleTotalChar 1  Decimal   Total cost of the rental.
  geGroup/RateTotal              
  Amount                         

  @VehicleTotalChar 1  String    Currency in which the amount is returned.
  geGroup/CurrencyC              
  ode                            

  VehAvail/VehAvail 1  List of   List of fees related to this rental.
  Core/Fees            VehicleCh 
                       argePurpo 
                       se        

  VehAvail/VehAvail 1. VehicleCh Fee related to this rental.
  Core/Fees/Fee     .n argePurpo 
                       se        

  VehAvail/VehAvail 1  CompanyNa Company that provides this option.
  Core/Vendor          me        

  @CompanyName/Code 1  String    Identifies the company that offers the
                                 option.

  VehAvail/VehAvail 1. List of   Location where the vehicle is picked up.
  Core/VendorLocati .n VendorLoc 
  on                   ation     

  @VendorLocation/L 1  String    Code that represents the location of the
  ocationCode                    search.

  @VendorLocation/C 1  eLocation Indicates the type of code. The possible
  odeContext           CodeConte values are IATA, OFFICE and CITY.
                       xtType    

  @VendorLocation/E 1  String    Contains information about the Location
  xtendedLocationCo              where the vehicle will be picked up or
  de                             returned.

  @VendorLocation/N 1  String    Indicates the name of the location.
  ame                            

  VehAvail/VehAvail 1. List of   Location where the vehicle is returned.
  Core/DropOffLocat .n VendorLoc 
  ion                  ation     

  VehAvail/VehAvail 1  TPAExtens Contains an Atributos object.
  Core/TPAExtension    ions      
  s                              

  VehAvail/VehAvail 1  Atributos List of atributo, This is a Key-Value
  Core/TPA\_Extensi              structure used to configure specific
  ons/Atributos                  information for each integration or to
                                 save certain information for subsequent
                                 calls.

  VehAvail/VehAvail 1. Atributo  This is a Key-Value structure used to
  Core/TPA\_Extensi .n           configure specific information for each
  ons/Atributos/Atr              integration or to save certain information
  ibuto                          for subsequent calls.

  @Atributo/key     1  String    Unique key that identifies the value.

  @Atributo/value   1  String    Value of the Atributo.
  -------------------------------------------------------------------------

|
