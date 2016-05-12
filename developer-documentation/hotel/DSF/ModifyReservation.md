---
title: ModifyReservation
keywords: hotel, data structure, modify reservation
sidebar: mydoc_sidebar
permalink: /developer-documentation/hotel/DSF/ModifyReservation
---

|

Method Goals
============

This message confirms a modification

|

Request Format
==============

The request requires the valuation returned for ModifyValuationRS

|

Response Format
===============

The XML returned contains a booking confirmation

|

Remarks
=======

The maximum time, that is permitted in our system, before the connection
is closed, is of **180000** milliseconds.

|

ModifyReservationRQ Example
===========================

    <ModifyReservationRQ>
        <OnRequest>false</OnRequest>
        <Nationality>ES</Nationality>
        <Reservation>
            <Locators>
                <Client>5356342</Client>
                <Provider>MGNZ12345</Provider>
            </Locators>
            <Currency>EUR</Currency>
            <StartDate>28/01/2014</StartDate>
            <EndDate>29/01/2014</EndDate>
            <CreationDate>17/01/2014</CreationDate>
        </Reservation>
        <Modifications>
            <ModifyMealPlan></ModifyMealPlan>
            <ModifyStartDateAddDays>
                <StartDate>29/01/2014</StartDate>
            </ModifyStartDateAddDays>
            <ModifyEndDateAddDays>
                <EndDate>30/01/2014</EndDate>
            </ModifyEndDateAddDays>
             <ModifyHolder>
                <Holder name = "Test11Modify" surname = "TestSur11Modify"/>
            </ModifyHolder>
            <ModifyRoomsAddRooms>
                <Rooms>
                    <Room code = "506">
                        <PaxGuests>
                            <PaxGuest age = "30">
                                <GivenName>name1</GivenName>
                                <SurName>surname1</SurName>
                            </PaxGuest>
                            <PaxGuest age = "30">
                                <GivenName>name2</GivenName>
                                <SurName>surname2</SurName>
                            </PaxGuest>
                        </PaxGuests>
                    </Room>
                </Rooms>
            </ModifyRoomsAddRooms>
            <ModifyRoomsRemoveRooms>
                <Rooms>
                    <Room code = "500">
                        <Price currency = "EUR" amount = "36.20" binding = "false" commission = "-1"/>
                    </Room>
                </Rooms>
            </ModifyRoomsRemoveRooms>
        </Modifications>
        <ModifyPenalty currency = "EUR" amount = "0" binding = "false" commission = "-1"/>
        <HotelReservation>
           <Price currency = "EUR" amount = "86.20" binding = "false" commission = "-1"/>
        </HotelReservation>
            <CardInfo>
            <CardCode>XX</CardCode>
            <Number>XXXXXXXXXX</Number>
            <Holder>XXXX</Holder>
            <ValidityDate>
                <Month>XX</Month>
                <Year>XX</Year>
            </ValidityDate>
            <CVC>XXX</CVC>
            </CardInfo>
        <Parameters>
            <Parameter key = "bd1" value = "43"/>
        </Parameters>
    </ModifyReservationRQ>

|

ModifyReservationRQ Description
===============================

  -------------------------------------------------------------------------
  Element               Num Typ Description
                        ber e   
  --------------------- --- --- -------------------------------------------
  ModifyReservationRQ   1       Root node.

  OnRequest             1   Boo Indicates if you want to receive the on
                            lea request options in AvailRS, as long as the
                            n   provider returns it in this call (see
                                StaticConfiguration).

  Nationality           0.. Str Nationality of the Holder (use
                        1   ing ISO3166\_1\_alfa\_2). This informations
                                will be mandatory depending on the
                                provider, as long as the provider returns
                                it in this call (see StaticConfiguration).

  Reservation           1       Reservaton data.

  Reservation/Locators  1       Information of the locators (it is
                                mandatory indicate one of two, or client or
                                provider).

  Reservation/Locators/ 0.. Str Client locator.
  Client                1   ing 

  Reservation/Locators/ 0.. Str Provider locator.
  Provider              1   ing 

  Reservation/Currency  1   Str Currency code.
                            ing 

  Reservation/StartDate 1   Str Start date of booking.
                            ing 

  Reservation/EndDate   1   Str End date of booking.
                            ing 

  Reservation/CreationD 1   Str Creation date of booking.
  ate                       ing 

  Modifications         1       Modifications.

  Modifications/ModifyS 0..     Add days of check-in.
  tartDateAddDays       1       

  Modifications/ModifyS 1   Str New check-in.
  tartDateAddDays/Start     ing 
  Date                          

  Modifications/ModifyS 0..     Substract days of check-in.
  tartDateSubtractDays  1       

  Modifications/ModifyS 1   Str New chekc-in.
  tartDateSubtractDays/     ing 
  StartDate                     

  Modifications/ModifyE 0..     Add days of check-out.
  ndDateAddDays         1       

  Modifications/ModifyE 1   Str New check-out.
  ndDateAddDays/EndDate     ing 

  Modifications/ModifyE 0..     Substract days of check-out.
  ndtDateSubtractDays   1       

  Modifications/ModifyE 1   Str New check-out.
  ndtDateSubtractDays/E     ing 
  ndDate                        

  Modifications/ModifyH 0..     Modify holder.
  older                 1       

  Modifications/ModifyH 1       New holder.
  older/Holder                  

  <*@name>\*            1   Str Holder name .
                            ing 

  <*@surname>\*         1   Str Holder surname .
                            ing 

  <*@nationality>\*     0.. Str Nationality of the Holder (use
                        1   ing ISO3166\_1\_alfa\_2). This informations
                                will be mandatory depending on the
                                provider, as long as the provider returns
                                it in this call (see StaticConfiguration).

  Modifications/ModifyR 0..     Add Rooms structure .
  oomsAddRooms          1       

  Modifications/ModifyR 1       Rooms Add.
  oomsAddRooms/Rooms            

  Modifications/ModifyR 1..     Room Add.
  oomsAddRooms/Rooms/Ro n       
  om                            

  <*@code>\*            1   Str Room code.
                            ing 

  Modifications/ModifyR 1       List of passenger.
  oomsAddRooms/Rooms/Ro         
  om/PaxGuests                  

  Modifications/ModifyR 1..     Detail of each passenger.
  oomsAddRooms/Rooms/Ro n       
  om/PaxGuests/PaxGuest         

  <*@age>\*             1   Str Age pax.
                            ing 

  Modifications/ModifyR 1   Str Given Name.
  oomsAddRooms/Rooms/Ro     ing 
  om/PaxGuests/PaxGuest         
  /GivenName                    

  Modifications/ModifyR 1   Str Surname.
  oomsAddRooms/Rooms/Ro     ing 
  om/PaxGuests/PaxGuest         
  /SurName                      

  Modifications/ModifyR 0..     Remove Rooms structure.
  oomsRemoveRooms       1       

  Modifications/ModifyR 1       Rooms Remove.
  oomsRemoveRooms/Rooms         

  Modifications/ModifyR 1..     Room Remove.
  oomsRemoveRooms/Rooms n       
  /Room                         

  <*@code>\*            1   Str Room code.
                            ing 

  Modifications/ModifyR 1       Price Room
  oomsRemoveRooms/Rooms         
  /Room/Price                   

  <*@currency>\*        1   Str Currency code.
                            ing 

  <*@amount>\*          1   Dec Room Amount.
                            ima 
                            l   

  <*@binding>\*         1   Boo Identifies if is the price is binding (
                            lea When true the sale price returned **must**
                            n   not be less than the price informed.

  <*@commission>\*      1   Dec Commission ( -1 = not specified (will come
                            ima indicated with the provider contract ), 0 =
                            l   net price, X = % of the commission that
                                applies to the amount).

  ModifyPenalty         1       Price of penalty modification. (element
                                returned in ModifyValuationRS)

  <*@currency>\*        1   Str Currency code.
                            ing 

  <*@amount>\*          1   Dec Penalty Amount.
                            ima 
                            l   

  <*@binding>\*         1   Boo Identifies if is the price is binding (
                            lea When true the sale price returned **must**
                            n   not be less than the price informed.

  <*@commission>\*      1   Dec Commission ( -1 = not specified (will come
                            ima indicated with the provider contract ), 0 =
                            l   net price, X = % of the commission that
                                applies to the amount).

  HotelReservation      1       HotelReservation. (element returned in
                                ModifyValuationRS)

  HotelReservation/Pric 1       New total reservation price.
  e                             

  <*@currency>\*        1   Str Currency code.
                            ing 

  <*@amount>\*          1   Dec Reservation Amount.
                            ima 
                            l   

  <*@binding>\*         1   Boo Identifies if is the price is binding (
                            lea When true the sale price returned **must**
                            n   not be less than the price informed.

  <*@commission>\*      1   Dec Commission ( -1 = not specified (will come
                            ima indicated with the provider contract ), 0 =
                            l   net price, X = % of the commission that
                                applies to the amount).

  PaymentType           0..     Information of the credit card.
                        1       

  PaymentType/CardInfo  1       Information of the credit card.

  PaymentType/CardCode  1       Indicates the card type.

  PaymentType/Number    1   Dec Number of the credit card.
                            ima 
                            l   

  PaymentType/Holder    1   Str Holder of the credit card.
                            ing 

  PaymentType/ValidityD 1       Validity date.
  ate                           

  PaymentType/ValidityD 1   Dec Month of the validity date.
  ate/Month                 ima 
                            l   

  PaymentType/ValidityD 1   Dec Year of the validity date.
  ate/Year                  ima 
                            l   

  PaymentType/CVC       1   Dec CVC of the credit card.
                            ima 
                            l   

  Parameters            0..     Parameters for additional information.
                        1       (element returned in ModifyValuationRS)

  Parameters/Parameter  1..     List of parameter.
                        n       

  <*@key>\*             1   Str Contains the keyword/Id to identify a
                            ing parameter.

  <*@value>\*           1   Str Contains the value of the parameter.
                            ing 
  -------------------------------------------------------------------------

|

ModifyReservationRS Example
===========================

    <ModifyReservationRS>
        <ProviderLocator>XXXXXX</ProviderLocator>
        <Price currency = "EUR" amount = "86.20" binding = "false" commission = "-1"/>
        <ResStatus>OK</ResStatus>
        <Remarks>The option has the following features: One Bed, Suite</Remarks>
        <BillingSupplierCode>Proveedor facturacion Externa</BillingSupplierCode>
        <Payable>Payment is guaranteed by: DESTINATIONS OF THE WORLD - DMCC as per final booking form reference  HTL-AE2-80989482</Payable>
    </ModifyReservationRS>

|

ModifyReservationRS Description
===============================

  ------------------------------------------------------------------------
  Element Num Type Description
          ber      
  ------- --- ---- -------------------------------------------------------
  ModifyV 1        Root node.
  aluatio          
  nRS              

  Provide 1   Stri Provider locator.
  rLocato     ng   
  r                

  ResStat 1   Stri Status of book (OK = confirmed, RQ = on request, CN =
  us          ng   cancelled, UN = unknown ).

  Price   0..      Total price of this book.
          1        

  <*@curr 1   Stri Currency code.
  ency>\*     ng   

  <*@amou 1   Deci Book Amount.
  nt>\*       mal  

  <*@bind 1   Bool Identifies if is the price is binding ( When true the
  ing>\*      ean  sale price returned **must** not be less than the price
                   informed.

  <*@comm 1   Deci Commission ( -1 = not specified (will come indicated
  ission>     mal  with the provider contract ), 0 = net price, X = % of
  \*               the commission that applies to the amount).

  Remarks 0.. Stri Remarks.
          1   ng   

  Billing 0.. Stri Indicates which typo of billing.
  Supplie 1   ng   
  rCode            

  Payable 0.. Stri Indicates which typo of payment.
          1   ng   
  ------------------------------------------------------------------------

|
