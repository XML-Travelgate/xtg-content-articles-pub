---
title: Pre-Booking (Rate Rule)
keywords: transfers, data structure, pre booking, rate rule
sidebar: mydoc_sidebar
permalink: /developer-documentation/car/DSF/rate-rule
---

|

Method Goals
============

This method aims to return the total price of the selected VehAvail
(option). This VehAvail option **must** be selected in the previous step
( OTA VehAvailRate).

This message allows the partners to know the applied conditions on the
chosen car and also shows the breakdown of the applied charges and fees
including the final price.

|

Remarks Some suppliers do not provide this method. If this is the case
all the info **must** be returned in OTA VehAvailRate and this method
will do a OTA VehAvailRate again filtered by the selected option.

|

OTA VehRateRule RQ Example
==========================

:

    <OTA_VehRateRuleRQ xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <timeoutMilliseconds>60000</timeoutMilliseconds>
      <filterAuditData>
        <registerTransactions>false</registerTransactions>
      </filterAuditData>
      <Configuration ProviderCode="CT">
        <Credentials user="1234" password="">
          <genericURL>https://otatest.cartrawler.com:20000/cartrawlerota</genericURL>
          <identificationURL xsi:nil="true" />
          <availRateURL xsi:nil="true" />
          <rateRuleURL xsi:nil="true" />
          <vehResURL xsi:nil="true" />
          <specificURLs>
            <Attribute key="URL_OFICINAS" value="https://ota.cartrawler.com/cartrawlerota/files/static/ctlocation.EN.xml" />
          </specificURLs>
        </Credentials>
        <Attributes>
          <Attribute key="ISOCurrency" value="EUR" />
          <Attribute key="ConsumerIP" value="95.39.27.98" />
        </Attributes>
      </Configuration>
      <ClientConfiguration agency="agencyName" SellCurrency="EUR" />
      <POS>
        <Source ISOCountry="ESP">
          <RequestorID Type="LAN" ID="es" />
        </Source>
      </POS>
      <RentalInfo Status="Available">
        <VehRentalCore PickUpDateTime="2014-02-25T09:30:00Z" ReturnDateTime="2014-02-27T17:00:00Z">
          <PickUpLocation LocationCode="71" CodeContext="IATA" />
          <ReturnLocation LocationCode="71" CodeContext="IATA" />
        </VehRentalCore>
        <VehicleInfo AirConditionInd="True" TransmissionType="MANUAL" VendorCarType="EDMR">
          <VehType VehicleCategory="1" doorCount="5" />
          <VehClass Size="3" />
          <VehMakeModel Name="Peugeot 207 or similar" Code="EDMR" />
        </VehicleInfo>
        <RateQualifier RateCategory="3" RateQualifier="PREPAID-IN" />
        <TPA_Extensions>
          <Atributos></Atributos>
        </TPA_Extensions>
      </RentalInfo>
    </OTA_VehRateRuleRQ>

|

OTA VehRateRuleRQ Description
=============================

The VehRateRule request requires the following information:

-   Pick up location and return location with its corresponding dates.
-   The selected vehicle information. This refers to the make model, the
    vehicle type, transmission type and also if it has air condition or
    not.
-   The selected rate for the chosen option.

  -------------------------------------------------------------------------
  Element         Numb Type      Description
                  er             
  --------------- ---- --------- ------------------------------------------
  OTA\_VehRateRul 1              Root Node
  eRQ                            

  OTA\_VehRateRul 1    Pos       Contains information of the Point Of Sale.
  eRQ/POS                        

  OTA\_VehRateRul 1    RentalInf Contains the info related to the rental.
  eRQ/RentalInfo       o         

  RentalInfo/VehR 1    VehRental Contains the dates and locations of the
  entalCore            Core      rental.

  RentalInfo/Vehi 1    VehiclePr Contains a list of VehiclePref. A
  cleInfo              ef        vehiclePref has information related to the
                                 vehicle model.

  RentalInfo/Rate 1    RateQuali This is the vendor specific code for rate
  Qualifier            fier      codes (e.g. WES, 2A, DLY00).

  RentalInfo/TPAE 1    TPAExtens Contains an Atributos object.
  xtensions            ions      

  RentalInfo/Stat 1    eInventor Status of the option. It's possible values
  us                   yStatus   are Available, OnRequest and All.
  -------------------------------------------------------------------------

|

OTA VehRateRuleRS Example
=========================

:

    <?xml version="1.0"?>
    <OTA_VehRateRuleRS xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <auditData>
        <timeStamp>0001-01-01T00:00:00</timeStamp>
        <processTimeMilliseconds>0</processTimeMilliseconds>
      </auditData>
      <operationImplemented>true</operationImplemented>
      <VehRentalCore PickUpDateTime="2014-02-25T09:30:00Z" ReturnDateTime="2014-02-27T17:00:00Z">
        <PickUpLocation LocationCode="71" CodeContext="IATA" />
        <ReturnLocation LocationCode="71" CodeContext="IATA" />
      </VehRentalCore>
      <Vehicle AirConditionInd="True" TransmissionType="MANUAL" PassengerQuantity="5" BaggageQuantity="3" VendorCarType="EDMR">
        <VehType VehicleCategory="1" doorCount="5" />
        <VehClass Size="3" />
        <VehMakeModel Name="Peugeot 207 or similar" Code="EDMR" />
        <PictureURL>https://cdn.cartrawler.com/otaimages/peugeot/207_nologo.jpg</PictureURL>
      </Vehicle>
      <RentalRate Status="All">
        <RateDistance Unlimited="true" DistUnitName="kilometer" />
        <RateQualifier RateCategory="3" RateQualifier="PREPAID-IN" />
        <VehicleCharges>
          <VehicleCharge Amount="0" CurrencyCode="EUR" TaxInclusive="true" IncludedInRate="true" Purpose="ADJUSTMENT">
            <Description>Breakdown assistance</Description>
          </VehicleCharge>
          <VehicleCharge Amount="0" CurrencyCode="EUR" TaxInclusive="true" IncludedInRate="true" Purpose="ADJUSTMENT">
            <Description>Airport fee</Description>
          </VehicleCharge>
          <VehicleCharge Amount="0" CurrencyCode="EUR" TaxInclusive="true" IncludedInRate="true" Purpose="ADJUSTMENT">
            <Description>Road tax</Description>
          </VehicleCharge>
          <VehicleCharge Amount="5.54" CurrencyCode="EUR" TaxInclusive="true" IncludedInRate="false" Purpose="ADJUSTMENT">
            <Description>Tolls</Description>
          </VehicleCharge>
          <VehicleCharge Amount="0" CurrencyCode="EUR" TaxInclusive="false" IncludedInRate="true" Purpose="ADJUSTMENT">
            <Description>Tax</Description>
          </VehicleCharge>
          <VehicleCharge Amount="0" CurrencyCode="EUR" TaxInclusive="true" IncludedInRate="true" Purpose="ADJUSTMENT">
            <Description>Unlimited mileage</Description>
          </VehicleCharge>
          <VehicleCharge Amount="36.96" CurrencyCode="EUR" TaxInclusive="true" IncludedInRate="true" Purpose="VEHICLE_RENTAL">
            <Description>Importe Alquiler</Description>
          </VehicleCharge>
        </VehicleCharges>
      </RentalRate>
      <TotalCharge RateTotalAmount="36.96" CurrencyCode="EUR" />
      <PricedEquips>
        <PricedEquip Required="false">
          <Equipment EquipType="OTHER">
            <Description>Booster seat</Description>
          </Equipment>
          <Charge Amount="15.00" CurrencyCode="EUR" TaxInclusive="false" IncludedInRate="false">
            <Description />
          </Charge>
        </PricedEquip>
        <PricedEquip Required="false">
          <Equipment EquipType="OTHER">
            <Description>Child toddler seat</Description>
          </Equipment>
          <Charge Amount="25.50" CurrencyCode="EUR" TaxInclusive="false" IncludedInRate="false">
            <Description />
          </Charge>
        </PricedEquip>
        <PricedEquip Required="false">
          <Equipment EquipType="OTHER">
            <Description>Infant child seat</Description>
          </Equipment>
          <Charge Amount="24.00" CurrencyCode="EUR" TaxInclusive="false" IncludedInRate="false">
            <Description />
          </Charge>
        </PricedEquip>
        <PricedEquip Required="false">
          <Equipment EquipType="OTHER">
            <Description>GPS - Satellite Navigational System</Description>
          </Equipment>
          <Charge Amount="18.00" CurrencyCode="EUR" TaxInclusive="false" IncludedInRate="false">
            <Description />
          </Charge>
        </PricedEquip>
        <PricedEquip Required="false">
          <Equipment EquipType="OTHER">
            <Description>Toll payment tag/pass</Description>
          </Equipment>
          <Charge Amount="4.50" CurrencyCode="EUR" TaxInclusive="false" IncludedInRate="false">
            <Description />
          </Charge>
        </PricedEquip>
        <PricedEquip Required="false">
          <Equipment EquipType="OTHER">
            <Description>Additional Driver</Description>
          </Equipment>
          <Charge Amount="13.50" CurrencyCode="EUR" TaxInclusive="false" IncludedInRate="false">
            <Description />
          </Charge>
        </PricedEquip>
      </PricedEquips>
      <Fees>
        <Fee Amount="36.96" CurrencyCode="EUR" TaxInclusive="false" IncludedInRate="false" Purpose="PREPAY_AMOUNT">
          <Description />
        </Fee>
        <Fee Amount="0.00" CurrencyCode="EUR" TaxInclusive="false" IncludedInRate="false" Purpose="PAY_ON_ARRIVAL_AMOUNT">
          <Description />
        </Fee>
        <Fee Amount="0.00" CurrencyCode="EUR" TaxInclusive="false" IncludedInRate="false" Purpose="FEE">
          <Description />
        </Fee>
      </Fees>
      <PricedCoverages>
        <PricedCoverage>
          <Coverage CoverageType="6" Code="Collision damage waiver (CDW)">
            <Details>Collision damage waiver (CDW)</Details>
          </Coverage>
          <Charge Amount="0" CurrencyCode="ISOCurrency" TaxInclusive="false" IncludedInRate="true">
            <Description>Collision damage waiver (CDW)</Description>
          </Charge>
        </PricedCoverage>
        <PricedCoverage>
          <Coverage CoverageType="47" Code="Theft waiver (TW)">
            <Details>Theft waiver (TW)</Details>
          </Coverage>
          <Charge Amount="0" CurrencyCode="ISOCurrency" TaxInclusive="false" IncludedInRate="true">
            <Description>Theft waiver (TW)</Description>
          </Charge>
        </PricedCoverage>
        <PricedCoverage>
          <Coverage CoverageType="50" Code="Third party liability protection (TP)">
            <Details>Third party liability protection (TP)</Details>
          </Coverage>
          <Charge Amount="0" CurrencyCode="ISOCurrency" TaxInclusive="true" IncludedInRate="true">
            <Description>Third party liability protection (TP)</Description>
          </Charge>
        </PricedCoverage>
      </PricedCoverages>
      <VendorMessages />
      <TPA_Extensions>
        <Atributos></Atributos>
      </TPA_Extensions>
    </OTA_VehRateRuleRS>

|

OTA VehRateRuleRS Description
=============================

The returned XML is similar to the result of the OTA VehAvailRate call.
The main difference is that only one option is returned (the selected
one). The total price is definitive. Sometimes this method will fail
since the selected option at OTA VehAvailRate time will not be available
in this stage. In this case the integration returns an error code 204
(ERROR NO RESULTS)( link missing ).

  -------------------------------------------------------------------------
  Element                 Num Type          Description
                          ber               
  ----------------------- --- ------------- -------------------------------
  OTA\_VehRateRuleRS      1                 Root Node

  OTA\_VehRateRuleRS/VehR 1   VehRentalCore Contains the dates and
  entalCore                                 locations of the rental.

  OTA\_VehRateRuleRS/Vehi 1   Vehicle       Includes information about the
  cle                                       vehicle model.

  OTAVehRateRuleRS/Rental 1   OTAVehRateRul Contains information of the
  Rate                        eRS\_VehicleR allowed distance, the selected
                              entalRate     rate, and the associated
                                            charges.

  @OTA*VehRateRuleRS*Vehi 1   eInventorySta Status of the option. It's
  cleRentalRate/Status        tus           possible values are Available,
                                            OnRequest and All.

  OTA*VehRateRuleRS*Vehic 1   VehicleRateDi Information about the permitted
  leRentalRate/RateDistan     stanceGroup   distance for this rate.
  ce                                        

  OTA*VehRateRuleRS*Vehic 1   RateQualifier Information about the rate.
  leRentalRate/RateQualif                   
  ier                                       

  OTA*VehRateRuleRS*Vehic 1   List of       Charges associated to this
  leRentalRate/VehicleCha     VehicleCharge rate.
  rges                        Purpose       

  OTA*VehRateRuleRS*Vehic 1.. VehicleCharge Charge associated to this rate.
  leRentalRate/VehicleCha n   Purpose       
  rges/VehicleCharge                        

  OTA\_VehRateRuleRS/Tota 1   VehicleTotalC Total cost of the rental.
  lCharge                     hargeGroup    

  OTA\_VehRateRuleRS/Pric 1   List of       List of equipments for the
  edEquips                    VehicleEquipm vehicle.
                              entPriced     

  OTA\_VehRateRuleRS/Pric 1.. VehicleEquipm List of equipments for the
  edEquips/PricedEquip    n   entPriced     vehicle.

  OTA\_VehRateRuleRS/Fees 1   List of       List of fees related to this
                              VehicleCharge rental.
                              Purpose       

  OTA\_VehRateRuleRS/Fees 1.. VehicleCharge Fee related to this rental.
  /Fee                    n   Purpose       

  OTA\_VehRateRuleRS/Pric 1   PricedCoverag Contains information of the
  edCoverages                 es            coverages offered by the
                                            provider.

  PricedCoverages/PricedC 1.. PricedCoverag List that contains the offered
  overage                 n   e             accident coverages.

  PricedCoverage/Coverage 1   Coverage      Accident coverage offered by
                                            the provider.

  @Coverage/CoverageType  1   String        Provider's type of coverage.

  @Coverage/Code          1   String        Provider's code of the
                                            coverage.

  @Coverage/Details       1   Details       Details of the coverage
                                            returned by the provider.

  Details/Text            1   String        Details.

  PricedCoverage/Charge   1   VehicleCharge Cost of the coverage.
                              Type          

  OTA\_VehRateRuleRS/Vend 1   VendorMessage Messages received in the
  orMessages                  s             provider's response.

  OTA\_VehRateRuleRS/Vend 1.. VendorMessage List of messages received in
  orMessages/VendorMessag n                 the provider's response.
  e                                         

  @VendorMessage/InfoType 1   eInformationT Indicates the type of
                              ype           information shown in the
                                            message.

  VendorMessage/Tittle    1   String        Tittle of the message.

  VendorMessage/Language  1   eLanguageType Indicates the language in which
                                            the message is written.

  VendorMessage/SubSectio 1   list of       Contains a list of texts that
  n                           FormattedText compound the message.
                              SubSection    

  FormattedTextSubSection 1   String        Tittle of the Paragraph.
  /SubTitle                                 

  FormattedTextSubSection 1.. Paragraph     Contains a list of paragraphs
  /Paragraph              n                 that compound the message.

  FormattedTextSubSection 1.. FormattedText Contains messages recieved in
  /Paragraph/ListItem     n   Text          the providers response and it's
                                            format (plain text or HTML).

  FormattedTextText/TextF 1   eTextFormat   Indicates the format of the
  ormat                                     text. If it is plain text or
                                            HTML.

  FormattedTextText/text  1   String        Contains the text.

  OTA*VehRateRuleRS/TPA*E 1   TPA\_Extensio Contains an Atributos object.
  xtensions                   ns            
  -------------------------------------------------------------------------

|
