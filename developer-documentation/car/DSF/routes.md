---
title: Routes (Offices)
keywords: transfers, data structure, routes, offices
sidebar: mydoc_sidebar
permalink: /developer-documentation/car/DSF/routes
---

|

Method Goals
============

This method aims to return all the available offices for the selected
carrier.

|

Remarks
=======

This method should be cached internally and only called once a week and
in most cases once a month.

|

OTA VehLocSearchRQ Example
==========================

:

    <OTA_VehLocSearchRQ>
        <timeoutMilliseconds>999999</timeoutMilliseconds>
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
            <Source ISOCountry = "ESP">
                <RequestorID Type = "LAN" ID = "es"/>
            </Source>
        </POS>
    </OTA_VehLocSearchRQ>

|

OTA VehLocSearchRQ Description
==============================

The request requires a POS object. This method also accepts an office
code in order to retrieve the specific information related to this
office if the provider allows it.

  ------------------------------------------------------------------------
  Element         Num Type                   Description
                  ber                        
  --------------- --- ---------------------- -----------------------------
  OTA\_VehLocSear 1                          Root Node
  chRQ                                       

  OTA\_VehLocSear 1   Pos                    Contains information of the
  chRQ/POS                                   Point Of Sale.

  OTA\_VehLocSear 1   ItemSearchCriterionTyp Contains the coordinates of
  chRQ/VehLocSear     e                      the office and a reference
  chCriterion                                point to locate the office.

  ItemSearchCrite 1   Position               Object that contains the
  rionType/Positi                            coordinates of the office.
  on                                         

  Position/Latitu 1   Latitude of the        
  de                  position of the        
                      office.                

  Position/Longit 1   Longitude of the       
  ude                 position of the        
                      office.                

  ItemSearchCrite 1   This string contains a 
  rionType/RefPoi     reference point to     
  nt                  locate the office.     

  OTA\_VehLocSear 1   CompanyName            Identifies the provider who
  chRQ/Vendor                                owns that office.
  ------------------------------------------------------------------------

|

OTA VehLocSearchRS Example
==========================

:

    <OTA_VehLocSearchRS>
        <auditData>
            <timeStamp>2012-07-19T12:33:07.6131251+02:00</timeStamp>
            <processTimeMilliseconds>0</processTimeMilliseconds>
        </auditData>
        <operationImplemented>true</operationImplemented>
        <VehMatchedLocs>
            <VehMatchedLoc>
                <LocationDetail Code = "A06" Name = "Newcastle">
                    <Address>
                        <AddressLine>23 Paterson Road  Cnr Paterson And Alyff Street</AddressLine>
                        <CityName>Newcastle</CityName>
                        <PostalCode>2940</PostalCode>
                        <CountryName Code = "ZA0">SOUTH AFRICA: SOUTH AFRICA (AL</CountryName>
                    </Address>
                    <Telephone PhoneTechType = "VOICE" PhoneNumber = "27 34 312 6452"/>
                    <AdditionalInfo>
                        <ParkLocation Location = "CITY_CENTERDOWNTOWN"/>
                        <OperationSchedules>
                            <OperationSchedule Start = "2012-07- 19T12:33:11.9453729+02:00" End = "2017-07-19T12:33:11.9453729+02:00">
                                <OperationTimes>
                                    <OperationTime
                                        Start = "08:00"
                                        End = "17:30"
                                        Mon = "true"
                                        Tue = "true"
                                        Weds = "true"
                                        Thur = "true"
                                        Fri = "true"
                                        Sat = "true"
                                        Sun = "true"/>
                                </OperationTimes>
                            </OperationSchedule>
                        </OperationSchedules>
                    </AdditionalInfo>
                </LocationDetail>
                <VehLocSearchCriterion>
                    <Position Latitude = "-27.7298999946" Longitude = "29.96030000359"/>
                </VehLocSearchCriterion>
            </VehMatchedLoc>
            <VehMatchedLoc>
                <LocationDetail Code = "A0G" Name = "Pune Airport">
                    <Address>
                        <AddressLine>Gera 77  Plot No. 1 S 206 /1 Fp 88</AddressLine>
                        <CityName>Office No 10</CityName>
                        <PostalCode>411 011</PostalCode>
                        <CountryName Code = "IN0">INDIA</CountryName>
                    </Address>
                    <Telephone PhoneTechType = "VOICE" PhoneNumber = "00912026615303"/>
                    <Telephone PhoneTechType = "FAX" PhoneNumber = "00919766587083"/>
                    <AdditionalInfo>
                        <ParkLocation Location = "CITY_CENTERDOWNTOWN"/>
                        <OperationSchedules>
                            <OperationSchedule Start = "2012-07- 19T12:33:11.9453729+02:00" End = "2017-07-19T12:33:11.9453729+02:00">
                                <OperationTimes>
                                    <OperationTime
                                        Start = "00:00"
                                        End = "23:59"
                                        Mon = "true"
                                        Tue = "true"
                                        Weds = "true"
                                        Thur = "true"
                                        Fri = "true"
                                        Sat = "true"
                                        Sun = "true"/>
                                </OperationTimes>
                            </OperationSchedule>
                        </OperationSchedules>
                    </AdditionalInfo>
                </LocationDetail>
                <VehLocSearchCriterion>
                    <Position Latitude = "0" Longitude = "0"/>
                </VehLocSearchCriterion>
            </VehMatchedLoc>
        </VehMatchedLocs>
    </OTA_VehLocSearchRS>

|

OTA VehLocSearchRS Description
==============================

The result returns a list of VehMatchedLoc with the corresponding
information.

  --------------------------------------------------------------------------
  Element          Num Type              Description
                   ber                   
  ---------------- --- ----------------- -----------------------------------
  OTA\_VehLocSearc 1                     Root Node
  hRS                                    

  OTA\_VehLocSearc 1   List of           List of offices.
  hRS/VehMatchedLo     VehicleMatchedLoc 
  cs                   ation             

  VehicleMatchedLo 1   VehicleLocationDe Containts details of the location
  c/LocationDetail     tails             of the office.

  @VehicleLocation 1   String            Code that identifies the office in
  Details/Code                           the provider's system. This code
                                         should be used on
                                         OTA\_VehAvailRateRQ.

  @VehicleLocation 1   String            Name of the office.
  Details/Name                           

  @VehicleLocation Str Code that         
  Details/Extended ing identifies the    
  LocationCode         office in the     
                       provider's        
                       system.           

  @VehicleLocation Str Associated        
  Details/AssocAir ing airport to this   
  portLocList          office.           

  VehicleLocationD 1   AddressInfo       Indicates the address of the
  etails/Address                         office.

  AddressInfo/Addr 1   List of String    A list that contains 1 or more
  essLine                                addresses of the customer.

  AddressInfo/City 1   String            The name of the city where the
  Name                                   customer lives.

  AddressInfo/Post 1   String            The postal code of the customer's
  alCode                                 address.

  AddressInfo/Coun 1   CountryName       This object contains the code of
  tryName                                the country of the customer.

  VehicleLocationD 1   TelephoneInfoGrou Indicates the telephone number of
  etails/Telephone     p                 the office.

  TelephoneInfoGro 1   ePhoneTechnologyT Type of technology used by the
  up/PhoneTechType     ype               phone. Possible values: VOICE,
                                         DATA, FAX, PAGER ,MOBILE ,TTY
                                         ,TELEX ,VOICE*OVER*IP.

  TelephoneInfoGro 1   String            Number of the phone.
  up/PhoneNumber                         

  VehicleLocationD 1   VehicleLocationAd Contains the hours of the office
  etails/Additiona     ditionalDetails   and the type of location.
  lInfo                                  

  VehicleLocationA 1   VehicleWhereAtFac Informs the type of location where
  dditionalDetails     ilityType         the office is located.
  /ParkLocation                          

  VehicleWhereAtFa 1   eVecinityCode     Informs the type of location where
  cilityType/Locat                       the office is located.
  ion                                    

  VehicleLocationA 1   OperationSchedule Informs the office hours.
  dditionalDetails     s                 
  /OperationSchedu                       
  les                                    

  OperationSchedul 1.. OperationSchedule Informs the office hours.
  es/OperationSche n                     
  dule                                   

  OperationSchedul 1   DateTime          Date in which this operationTimes
  e/Start                                become valid.

  OperationSchedul 1   Date in which     
  e/End                this              
                       operationTimes    
                       are no longer     
                       valid.            

  OperationSchedul 1   List of           List of operationTime.
  e/OperationTimes     operationTime     

  OperationTimes/O 1.. OperationTime     Each OperationTime indicate the
  perationTime     n                     office hours and the days of the
                                         week subject to these hours.

  @OperationTime/S 1   String            Opening time of the office in hh:mm
  tart                                   format.

  @OperationTime/E 1   String            Closing time of the office in hh:mm
  nd                                     format.

  @OperationTime/M 1   Boolean           Boolean that indicates if this
  on                                     hours correspond to Mondays.

  @OperationTime/T 1   Boolean           Boolean that indicates if this
  ue                                     hours correspond to Tuesdays.

  @OperationTime/W 1   Boolean           Boolean that indicates if this
  eds                                    hours correspond to Wednesday.

  @OperationTime/T 1   Boolean           Boolean that indicates if this
  hur                                    hours correspond to Thursdays.

  @OperationTime/F 1   Boolean           Boolean that indicates if this
  ri                                     hours correspond to Fridays.

  @OperationTime/S 1   Boolean           Boolean that indicates if this
  at                                     hours correspond to Saturdays.

  @OperationTime/S 1   Boolean           Boolean that indicates if this
  un                                     hours correspond to Sundays.

  VehicleMatchedLo 1   VehicleLocationDe Containts details of the location
  cation/VehLocSea     tails             of the office.
  rchCriterion                           
  --------------------------------------------------------------------------

|
