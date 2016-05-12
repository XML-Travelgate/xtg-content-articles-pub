---
title: 'Book (Booking)'
...

|

Method Goals
============

This method aims to book the selected options.

|

BookRQ Example
==============

:

    <BookRQ>
        <timeoutMilliseconds>60000</timeoutMilliseconds>
        <source>
            <agencyCode>test</agencyCode>
            <languageCode>es</languageCode>
        </source>
        <filterAuditData>
            <registerTransactions>true</registerTransactions>
        </filterAuditData>
        <Configuration codeProvider = "XXX">
            <Credentials user = "XXX" password = "XXX">
                <UrlGeneric>XXX</UrlGeneric>
                <UrlIdentification xsi:nil = "true"/>
                <UrlAvailability xsi:nil = "true"/>
                <UrlRateRule xsi:nil = "true"/>
                <UrlBook xsi:nil = "true"/>
                <UrlsSpecific xsi:nil = "true"/>
            </Credentials>
            <Attributes>

            </Attributes>
        </Configuration>
        <Locator id = "XXX" type = "CLIENT"/>
        <SelectedRates>
            <SelectedRate id = "0" rateType = "OW">
                <SelectedOptions>
                    <SelectedOption status = "NEW" id = "0">
                        <Transfers>
                            <Transfer id = "0">
                                <Info type = "BUS" code = "XXX" typeVeh = "XXX"/>
                                <LocOrigin type = "ARP" code = "PMI" date = "2014-09-19T00:00:00"/>
                                <LocDestination type = "HOT" code = "XXX" date = "2014-09-19T00:00:00"/>
                            </Transfer>
                        </Transfers>
                        <Parameters></Parameters>
                    </SelectedOption>
                </SelectedOptions>
                <TotalRate currency = "EUR" amount = "5.350" priceType = "NET" commission = "0.640"/>
            </SelectedRate>
            <SelectedRate id = "0" rateType = "OW">
                <SelectedOptions>
                    <SelectedOption status = "NEW" id = "0">
                        <Transfers>
                            <Transfer id = "0">
                                <Info type = "BUS" code = "XXX" typeVeh = "XXX"/>
                                <LocOrigin type = "ARP" code = "PMI" date = "2014-09-19T00:00:00"/>
                                <LocDestination type = "HOT" code = "XXX" date = "2014-09-19T00:00:00"/>
                            </Transfer>
                        </Transfers>
                        <Parameters></Parameters>
                    </SelectedOption>
                </SelectedOptions>
                <TotalRate currency = "EUR" amount = "5.350" priceType = "NET" commission = "0.640"/>
            </SelectedRate>
        </SelectedRates>
        <PassengersConfirm>
            <PassengerConfirm>
                <InfoPassenger id = "0" age = "30">
                    <RefSegments>
                        <RefSegment refSegment = "0" bags = "0"/>
                        <RefSegment refSegment = "1" bags = "0"/>
                    </RefSegments>
                </InfoPassenger>
                <DataPassenger name = "xxx" surname = "XXXX" holder = "true"/>
            </PassengerConfirm>
        </PassengersConfirm>
        <Customer name = "xxx" surname = "XXXX" age = "30" phone = "+34665246787"/>
    </BookRQ>

|

BookRQ Description
==================

The request format works the same way as the RateRule request. The main
difference is that the passengers also include name and surname
information and indicate which of them is the customer of the
reservation. This request also contains a locator that identifies the
reservation in the client system (the types of this locator must be
always CLIENT).

  -------------------------------------------------------------------------
  Element       Num Type   Description
                ber        
  ------------- --- ------ ------------------------------------------------
  BookRQ        1          Root Node

  BookRQ/Locato 1   Locato Contains the locator that will identify the
  r                 r      reservation in the agency's system.

  BookRQ/Locato 1   String Indicates the locator value.
  r/id                     

  BookRQ/Locato 1   eLocat Indicates the type of the locator. The possible
  r/type            orType values are: **CLIENT**.

  BookRQ/Select 1   Select Contains a list of the selectedRates to be
  edRates           edRate booked.
                    s      

  BookRQ/Passen 1   Passen Contains a list of passengers with their
  gersConfirm       gersCo information.
                    nfirm  

  BookRQ/Passen 1.. Passen Contains a list of PassengerConfirm.
  gersConfirm/P n   gerCon 
  assengerConfi     firm   
  rm                       

  @PassengerCon 1   Passen Contains information related to the passenger
  firm/Passenge     ger    (the id that identifies the passenger, his age
  r                        and the references of the segments where he
                           wants to be transfered).

  @PassengerCon 1   DataPa Indicates the name of the passenger and contains
  firm/DataPass     ssenge a boolean that represents if this passenger is
  enger             r      the customer of the reservation.

  @DataPassenge 1   String Contains the name of the passenger.
  r/name                   

  @DataPassenge 1   String Contains the surname of the passenger.
  r/surname                

  @DataPassenge 1   Boolea Indicates if this passenger is the holder of the
  r/holder          n      reservation.

  BookRQ/Custom 1   Custom Contains Contact information of the customer.
  er                er     

  BookRQ/Custom 1   String Contains the name of the customer.
  er/name                  

  BookRQ/Custom 1   String Contains the surname of the customer.
  er/surname               

  BookRQ/Custom 1   Intege Contains the age of the customer.
  er/age            r      

  BookRQ/Custom 1   String Contains the contact phone number of the
  er/phone                 customer.
  -------------------------------------------------------------------------

|

BookRS Example
==============

:

    <BookRS>   
        <auditData>
            <transactions>
                <timeStamp>2014-09-19T13:44:18.716787+01:00</timeStamp>
                <RQ></RQ>
                <RS></RS>
            </transactions>
            <timeStamp>2014-09-19T13:44:17.2162683+01:00</timeStamp>
            <processTimeMilliseconds>0</processTimeMilliseconds>
        </auditData>
        <operationImplemented>true</operationImplemented>
        <Warnings>
            <Warning Code="XXXX">
                xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx.
            </Warning>
            <Warning Code="XXXX">
                xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx.
            </Warning>
        </Warnings>
        <Locators>
            <Locator id = "123456" type = "PROVIDER"/>
            <Locator id = "XXX" type = "CLIENT"/>
        </Locators>
        <TotalPrice currency = "EUR" amount = "5.350" priceType = "NET" commission = "0.640"/>
        <ReservationStatus>RESERVED</ReservationStatus>
    </BookRS>

|

BookRS Description
==================

The result returns a list of Locator (booking codes) the pricing of the
reservation and the reservation status, Also we added important but not
critical information, in format Warning, returned in the provider's
response.

  -------------------------------------------------------------------------
  Ele N Typ Description
  men u e   
  t   m     
      b     
      e     
      r     
  --- - --- ---------------------------------------------------------------
  Boo 1     Root Node
  kRS       

  Boo 1 Loc Contains a list of locators.
  kRS   ato 
  /Lo   rs  
  cat       
  ors       

  Boo 1 Loc Contains a list of Locator.
  kRS . ato 
  /Lo . r   
  cat n     
  ors       
  /Lo       
  cat       
  or        

  @Lo 1 Str Indicates the locator value.
  cat   ing 
  or/       
  id        

  @Lo 1 eLo Indicates the type of the locator. The possible values are:
  cat   cat **CLIENT** (This locator is from the agency's system. This is
  or/   orT the type of locator that the agency sends in the BookRQ. If the
  typ   ype provider accepts that locator, the BookRS will contain the same
  e         locator with this type); **PROVIDER** (This locator is from the
            provider's system); **OTHER** (This locator is not from the
            agency nor the provider, this locator belongs to a third party
            member involved in the reservation).

  Boo 1 Pri Contains information about the pricing of the reservation.
  kRS   ce  
  /To       
  tal       
  Pri       
  ce        

  Boo 1 eTr Indicates the status of the reservation. The possible values
  kRS   ans are: **UNSUCCESSFUL**(There has been an error in the
  /Re   act reservation process, Normaly the error is identified in node
  ser   ion Errors); **REQUESTED**( The reservation is pending);
  vat   Sta **RESERVED**; **CANCELLED**.
  ion   tus 
  Sta   Typ 
  tus   e   
  -------------------------------------------------------------------------

|
