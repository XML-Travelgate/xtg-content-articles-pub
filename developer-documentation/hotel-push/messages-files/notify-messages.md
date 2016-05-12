---
title: Notify Messages
keywords: hotel-push, messages, messages files, notify messages
sidebar: mydoc_sidebar
permalink: /developer-documentation/hotel-push/messages-files/notify-messages
---

Providers sends data to Sellers (Negotiation is started by Providers).

|

HotelRatePlanNotif
==================

Provider will send an HotelRatePlanNotifRQ message to push Rates to
seller. XTG will process data and response with error code if needed.

|

HotelRatePlanNotifRQ
====================

**Example for RatePlan**

:

    <HotelRatePlanNotif>
      <request>
        <POS>
          <Source>
            <RequestorID ID = "Provider1"/>
            <BookingChannel>
              <CompanyName Code = "ClientTravelAgency1"/>
            </BookingChannel>
          </Source>
        </POS>
        <RatePlans HotelCode = "HOT123">
          <RatePlan RatePlanCode = "TAR321" CurrencyCode = "EUR" RatePlanStatusType = "Active">
            <Rates>
              <Rate Start = "2007-04-01" End = "2007-12-31">
                <BaseByGuestAmts>
                  <BaseByGuestAmt NumberOfGuests = "1" AmountAfterTax = "100.00"/>
                  <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax = "130.00"/>
                  <BaseByGuestAmt NumberOfGuests = "3" AmountAfterTax = "195.00"/>
                </BaseByGuestAmts>
                <AdditionalGuestAmounts>
                  <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "40.00" AgeQualifyingCode = "8"/>
                  <AdditionalGuestAmount MaxAdditionalGuests = "2" Amount = "20.00" AgeQualifyingCode = "8"/>
                </AdditionalGuestAmounts>
              </Rate>
            </Rates>
            <SellableProducts>
              <SellableProduct InvCode = "43" InvType = "ROOM"/>
            </SellableProducts>
            <Supplements>
              <Supplement Start = "2007-04-01" End = "2007-12-31" AgeQualifyingCode = "10" Amount = "20.00" InvCode = "1" SupplementType = "Board"/>
              <Supplement Start = "2007-04-01" End = "2007-12-31" AgeQualifyingCode = "8" Amount = "10.00" InvCode = "1" SupplementType = "Board"/>
            </Supplements>
          </RatePlan>
          <RatePlan RatePlanCode = "TAR333" CurrencyCode = "EUR" SuplementsNotifTypeSpecified = "true" SuplementsNotifType = "Overlay" RatePlanStatusType = "Deactivated">
            <Rates>
              <Rate Start = "2013-04-01" End = "2013-12-31">
                <BaseByGuestAmts>
                  <BaseByGuestAmt Type = "25" AmountAfterTax = "150.00"/>
                </BaseByGuestAmts>
              </Rate>
            </Rates>
            <SellableProducts>
              <SellableProduct InvCode = "43" InvType = "ROOM"/>
            </SellableProducts>
            <Supplements>
              <Supplement Start = "2013-04-01" End = "2013-12-31" AgeQualifyingCode = "10" Amount = "20.00" InvCode = "1" SupplementType = "Board"/>
              <Supplement Start = "2013-04-01" End = "2013-12-31" AgeQualifyingCode = "8" Amount = "10.00" InvCode = "1" SupplementType = "Board"/>
            </Supplements>
          </RatePlan>
          <RatePlan RatePlanCode = "TAR333" CurrencyCode = "EUR" SuplementsNotifTypeSpecified = "true" SuplementsNotifType = "Overlay" RatePlanStatusType = "Deactivated">
            <Rates>
              <Rate Start = "2013-04-01" End = "2013-12-31">
                <BaseByGuestAmts>
                  <BaseByGuestAmt Type = "14" Code = "2-0-0" AmountAfterTax = "150.00"/>
                  <BaseByGuestAmt Type = "14" Code = "3-0-0" AmountAfterTax = "180.00"/>
                </BaseByGuestAmts>
              </Rate>
            </Rates>
            <SellableProducts>
              <SellableProduct InvCode = "43" InvType = "ROOM"/>
            </SellableProducts>
            <Supplements>
              <Supplement Start = "2013-04-01" End = "2013-12-31" Amount = "20.00" InvCode = "1" SupplementType = "Board" ChargeTypeCode = "2-0-0"/>
              <Supplement Start = "2013-04-01" End = "2013-12-31" Amount = "30.00" InvCode = "1" SupplementType = "Board" ChargeTypeCode = "3-0-0"/>
            </Supplements>
          </RatePlan>
        </RatePlans>
      </request>
    </HotelRatePlanNotif>

**Example for Derived RatePlan**

:

    <HotelRatePlanNotif>
      <request Version = "0">
        <POS>
          <Source>
            <RequestorID ID = "Provider1"></RequestorID>
            <BookingChannel>
              <CompanyName Code = "ClientTravelAgency1"></CompanyName>
            </BookingChannel>
          </Source>
        </POS>
        <RatePlan RatePlanCode = "DRV" BaseRatePlanCode = "SRATE" RatePlanStatusType = "Active">
          <Rates>
            <Rate Start = "2014-07-01" End = "2014-07-31" AdjustedPercentage = "10" AdjustUpIndicator = "0"></Rate>
          </Rates>
        </RatePlan>
        <RatePlan RatePlanCode = "DRV" BaseRatePlanCode = "SRATE" RatePlanStatusType = "Deactivated">
          <Rates>
            <Rate Start = "2014-08-01" End = "2014-08-31" AdjustedPercentage = "10" AdjustUpIndicator = "0"></Rate>
          </Rates>
        </RatePlan>
      </request>
    </HotelRatePlanNotif>

  ------------------------------------------------------------------------
  Element      N T Description
               u y 
               m p 
               b e 
               e   
               r   
  ------------ - - -------------------------------------------------------
  HotelRatePla 1   Root Node
  nNotif/reque     
  st               

  RatePlans    1   

  <*@HotelCode 1 S Hotel code whose information is provided by the method
  >\*            t 
                 r 
                 i 
                 n 
                 g 

  RatePlans/Ra 1   Present if rate exists
  tePlan       .   
               .   
               n   

  <*@RatePlanC 1 S Rate code
  ode>\*         t 
                 r 
                 i 
                 n 
                 g 

  <*@RatePlanS 0 S Active or Deactivated (You can save prices with initial
  tatusType>\* . t status deactivated if you want.) If this attribute is
               . r missing, the price will be saved as active.
               1 i 
                 n 
                 g 

  <*@BaseRateP 0 S Rate code of the base RatePlan. Only used for derived
  lanCode>\*   . t rates
               . r 
               1 i 
                 n 
                 g 

  <*@CurrencyC 0 S ISO Currency (EUR). Not used for derived rates
  ode>\*       . t 
               . r 
               1 i 
                 n 
                 g 

  \_@Suplement 0 B Rate code. Not used for derived rates
  sNotifTypeSp . o 
  ecified      . o 
               1 l 
                 e 
                 a 
                 n 

  \_@Suplement 0 S Possible values are Overlay or Delta. If not specified
  sNotifType   . t or Delta, Supplements will not be overwritten. If
               . r Overlay supplements will be overwritten. Not used for
               1 i derived rates
                 n 
                 g 

  RatePlans/Ra 1   
  tePlan/Rates     
  /Rate            

  <*@Start>\*  1 D Start date of rate
                 a 
                 t 
                 e 

  <*@End>\*    1 D Start date of rate
                 a 
                 t 
                 e 

  <*@AdjustedP 0 D The percentage off the base rate plan amount used to
  ercentage>\* . e determine the price of this derived rate plan. Only
               . c used for derived rates
               1 i 
                 m 
                 a 
                 l 

  <*@AdjustedA 0 D The amount which should be added to the base rate plan
  mount>\*     . e to determine the price of this derived rate plan. Only
               . c used for derived rates
               1 i 
                 m 
                 a 
                 l 

  <*@AdjustUpI 0 B When true, the adjusted amount or adjusted percentage
  ndicator>\*  . o is added to the amount specified for the base rate plan
               . o to determine the derived rate amount. When false, the
               1 l adjusted amount or adjusted percentage is subtracted
                 e from the amount specified for the base rate plan to
                 a determine the derived rate amount. Only used for
                 n derived rates

  RatePlans/Ra 0   
  tePlan/Rates .   
  /Rate/BaseBy .   
  GuestAmts    1   

  RatePlans/Ra 1   
  tePlan/Rates .   
  /Rate/BaseBy .   
  GuestAmts/Ba n   
  seByGuestAmt     

  <*@AmountAft 1 D Total amount for @NumberOfGuests by day indicated
  erTax>\*       e 
                 c 
                 i 
                 m 
                 a 
                 l 

  <*@NumberOfG 0 I How many adults are the @AmountAfterTax for day
  uests>\*     . n indicated. If @NumberOfGuests is not informed then
               . t @Type must be informed. The maximum @NumberOfGuests is
               1 e the standard occupancy of the room
                 g 
                 e 
                 r 

  <*@Type>\*   0 I Amounts are per Room or per Occupancy instead of per
               . n Pax. If @Type=25, price is per room, 1 BaseByGuestAmt
               . t is allowed and @NumberOfGuests and
               1 e AdditionalGuestAmounts are not allowed. If @Type=14,
                 g price is per occupancy, @Code is mandatory and
                 e @NumberOfGuests and AdditionalGuestAmounts are not
                 r allowed.

  <*@Code>\*   0 S Mandatory if @Type=14. The occupancy code is defined by
               . t AdultNumber-ChildNumber-InfantNumber. @Code for an
               . r occupancy of 2 adults, 1 child and 0 babies would be
               1 i "2-1-0".
                 n 
                 g 

  RatePlans/Ra 0   Not used for derived rates
  tePlan/Rates .   
  /Rate/Additi .   
  onalGuestAmo 1   
  unts             

  RatePlans/Ra 1   Price and information about the additional pax
  tePlan/Rates .   (children, infants or extra adults)
  /Rate/Additi .   
  onalGuestAmo n   
  unts/Additio     
  nalGuestAmou     
  nt               

  <*@MaxAdditi 1 I Number of additional pax, one node for each additional
  onalGuests>\   n pax, int the above example has one for first child, and
  *              t one for second.
                 e 
                 g 
                 e 
                 r 

  <*@Type>\*   0 S OTA AmountDeterminationType. If not specified then the
               . t price is a supplement, if @Type is Exclusive then the
               . r the price is absolute.
               1 i 
                 n 
                 g 

  <*@AgeQualif 1 I (10 - Adult,8 - Child,7 - Infant)
  yingCode>\*    n 
                 t 
                 e 
                 g 
                 e 
                 r 

  <*@Amount>\* 1 D Price for each additional pax
                 e 
                 c 
                 i 
                 m 
                 a 
                 l 

  RatePlans/Su 0   Present if supplements by board exists. Not used for
  pplements    .   derived rates
               .   
               1   

  RatePlans/Su 1   
  pplements/Su .   
  pplement     .   
               n   

  <*@Start>\*  1 D Start date of this supplement
                 a 
                 t 
                 e 

  <*@End>\*    1 D End date of this supplement
                 a 
                 t 
                 e 

  <*@AgeQualif 0 I Age qualifyingCode which affects this supplement (10 -
  yingCode>\*  . n Adult,8 - Child,7 - Infant). Not allowed if charging
               . t board supplement by occupancy.
               1 e 
                 g 
                 e 
                 r 

  <*@ChargeTyp 0 S Indicates the board supplement occupancy. Only allowed
  eCode>\*     . t if charging board supplement by occupancy. The
               . r occupancy code is defined by
               1 i AdultNumber-ChildNumber-InfantNumber. @ChargeTypeCode
                 n for an occupancy of 2 adults, 1 child and 0 babies
                 g would be "2-1-0".

  <*@Amount>\* 1 D Amount of supplement
                 e 
                 c 
                 i 
                 m 
                 a 
                 l 

  <*@Supplemen 1 S (Board)
  tType>\*       t 
                 r 
                 i 
                 n 
                 g 

  <*@InvCode>\ 1 S OTA MPT Code if @SupplementType is Board
  *              t 
                 r 
                 i 
                 n 
                 g 

  RatePlans/Ra 0   List of sellable products. Null for derived rates.
  tePlan/Sella .   
  bleProducts  .   
               1   

  RatePlans/Se 1   
  llableProduc .   
  ts/SellableP .   
  roduct       n   

  <*@InvCode>\ 1 I Sellable Product Code
  *              n 
                 t 
                 e 
                 g 
                 e 
                 r 

  <*@InvType>\ 1 I Sellable product type (ROOM)
  *              n 
                 t 
                 e 
                 g 
                 e 
                 r 
  ------------------------------------------------------------------------

**Important information:**

-   The prices under the standard occupancy are ALWAYS loaded with
    BaseByGuestAmts.
-   Children and babies are not allowed in BaseByGuestAmts. Children and
    babies must be always defined in AdditionalGuestAmounts.
-   The possible Type values in the AdditionalGuestAmount tag are
    Exclusive and not specified.

    > -   If there's no value specified then the price is a relative.
    >     And it's added to the price of the current pax.
    > -   If the value is "Exclusive" then the price is absolute. And
    >     it's the total price of the current pax.

-   If NumberOfGuests is not specified in tag BaseByGuestAmt then
    Type="25" (price per room) or Type="14" (price per occupancy) must
    be specified. If Type="25" only one tag BaseByGuestAmt is allowed.
-   If the price is per room then all AdditionalGuestAmount must be
    relative.

\* If the price is per occupancy then Type should be 14 and Code should
be specified. The occupancy code is defined by
AdultNumber-ChildNumber-InfantNumber, for an occupancy of 2 adults, 1
child and 0 babies should be "2-1-0".

-   In samples room uses are specified using = AdultNumber -
    ChildNumber - InfantNumber.

**Notify amounts by Guests:**

Case 1:

Standard occupancy = 2.

Room uses = 1-0-0, 2-0-0.

We only load the price for standard occupancy.

:

    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>  

There is no price for one adult, so it wont be available.

The price of two adults will be 100 = 2\*(100/2).

|

Case 2:

Standard occupancy = 2.

Room uses = 1-0-0, 2-0-0.

We load the price for standard occupancy and the price for 1 Adult.

:

    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "1" AmountAfterTax="100.00"/>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="130.00"/>
    </BaseByGuestAmts>

The price of one Adult (Also known as Double Single Use) will be 100 =
100.

The price of two adults will be 130 = 2\*(130/2).

|

Case 3:

Standard occupancy = 2.

Room uses = 1-0-0, 2-0-0, 3-0-0.

We load the price for standard occupancy and the price for 1 additional
Adult Type default.

:

    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "40.00" AgeQualifyingCode = "10"/>
    </AdditionalGuestAmounts>

There is no price for one adult, so it wont be available.

The price of two Adult will be 100 = 2\*(100/2).

The price of three Adults will be 190 = (100/2) + (100/2) + ((100/2) +
(40).

|

Case 4:

Standard occupancy = 2

Room uses = 1-0-0, 2-0-0, 3-0-0

We load the price for standard occupancy and the price for 1 additional
Adult Type Exclusive.

:

    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "40.00" AgeQualifyingCode = "10" Type="Exclusive"/>
    </AdditionalGuestAmounts>

There is no price for one adult, so it wont be available.

The price of two Adult will be 100 = 2\*(100/2).

The price of three Adults will be 140 = (100/2) + (100/2) + 40.

|

Case 5:

Standard occupancy = 2.

Room uses = 1-0-0, 2-0-0, 1-1-0.

We load price for standard occupancy and the price for 1 additional
Child (AgeQualifyingCode = "8") Type default.

:

    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "40.00" AgeQualifyingCode = "8" />
    </AdditionalGuestAmounts>

There is no price for one adult, so it wont be available.

The price of two Adult will be 100 = 2\*(100/2).

The price of one Adult and one Child will be 100 = 2\*(100/2). All pax
under standard occupancy are considered as adults.

|

Case 5.1:

standard occupancy = 2.

room uses = 1-0-0, 2-0-0, 1-0-1.

NOTE: The same samples with children are valid for babies specifying
AgeQualifyingCode = "7".

We load price for standard occupancy and the price for 1 additional Baby
(AgeQualifyingCode = "7") Type default.

:

    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "40.00" AgeQualifyingCode = "7" />
    </AdditionalGuestAmounts>

There is no price for one adult, so it wont be available.

The price of two Adult will be 100 = 2\*(100/2).

The price of one Adult and one Child will be 100 = 2\*(100/2). All pax
under standard occupancy are considered as adults.

|

Case 6:

Standard occupancy = 2.

Room uses = 1-0-0, 2-0-0, 2-1-0.

We load price for standard occupancy and the price for 1 additional
Child Type default negative price

:

    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "-40.00" AgeQualifyingCode = "8" />
    </AdditionalGuestAmounts>

There is no price for one adult, so it wont be available.

The price of two Adults will be 100 = 2\*(100/2)

The price of one Adult and one Child will be 60 = 2\*(100/2) +
((100/2) -40).

|

Case 7:

Standard occupancy = 2.

Room uses = 1-0-0, 2-0-0, 3-0-0, 4-0-0.

We load the price of standard occupancy and the price for 1 additional
adult and the price for 2 additional adults.

:

    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "10.00" AgeQualifyingCode = "10" />
        <AdditionalGuestAmount MaxAdditionalGuests = "2" Amount = "-15.00" AgeQualifyingCode = "10" />
    </AdditionalGuestAmounts>

There is no price for one adult, so it wont be available.

The price of two Adults will be 100 = 2\*(100/2).

The price of three Adults will be 160 = (100/2) + (100/2) + ((100/2) +
10).

The price of four Adults will be 195 = (100/2) + (100/2) + ((100/2) +
10) + ((100/2) - 15).

|

Case 8:

Standard occupancy = 2.

Room uses = 1-0-0, 2-0-0, 3-0-0, 4-0-0.

We load the price of standard occupancy and the price for each
additional adult (Without specifying MaxAdditionalGuests).

:

    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "-10.00" AgeQualifyingCode = "10" />
    </AdditionalGuestAmounts>

There is no price for one adult, so it wont be available.

The price of two Adults will be 100 = 2\*(100/2).

The price of three Adults will be 140 = (100/2) + (100/2) +
((100/2) -10).

The price of four Adults will be 180 = (100/2) + (100/2) +
((100/2) -10) + ((100/2) - 10).

|

Case 9:

Standard occupancy = 3.

Room uses = 1-0-0, 2-0-0, 3-0-0, 4-0-0, 5-0-0.

We load the price of standard occupancy and the price for 1 additional
adult and the price for 2 additional adults.

:

    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "3" AmountAfterTax="150.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "-10.00" AgeQualifyingCode = "10" />
        <AdditionalGuestAmount MaxAdditionalGuests = "2" Amount = "15.00" AgeQualifyingCode = "10" />
    </AdditionalGuestAmounts>

There is no price for one adult, so it wont be available.

There is no price for two adults, so it wont be available.

The price of three Adults will be 150 = 3\*(150/3).

The price of four Adults will be 190 = (150/3) + (150/3) + (150/3) +
((150/3) - 10).

The price of five Adults will be 255 = (150/3) + (150/3) + (150/3) +
((150/3) - 10) + ((150/3) + 15).

|

**Notify amounts with price per room and additional guests**

Case 1:

Standard occupancy = 2.

Room uses = 1-0-0, 2-0-0, 1-1-0.

We load the price per room Type="25".

:

    <BaseByGuestAmts>
        <BaseByGuestAmt Type = "25" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>

The price of one Adult will be 100.

The price of two Adults will be 100.

The price of one Adult and one Child will be 100.

|

Case 2:

Standard occupancy = 2.

Room uses = 1-0-0, 2-0-0, 3-0-0, 1-1-0, 3-1-0.

We load the price per room but also the price for 1 additional adult and
the price for 1 additional child.

NOTE: the AdditionalGuestAmount Type in price per room has to be
default. Exclusive type not allowed.

:

    <BaseByGuestAmts>
        <BaseByGuestAmt Type = "25" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "20.00" AgeQualifyingCode = "10" />
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "10.00" AgeQualifyingCode = "8" />
    </AdditionalGuestAmounts>

The price of one Adult will be 100.

The price of two Adults will be 100.

The price of three Adults will be 120 = 100 + 20.

The price of one Adult and one Child will be 110 = 100 + 10.

The price of three Adults and one Child will be 130 = 100 + 20 + 10.

|

Case 3:

Standard occupancy = 3.

Room uses = 1-0-0, 2-0-0, 3-0-0, 4-0-0.

We load the price per room but also the price for 1 additional adult.

:

    <BaseByGuestAmts>
        <BaseByGuestAmt Type = "25" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "20.00" AgeQualifyingCode = "10" />
    </AdditionalGuestAmounts>

The price of one Adult will be 100.

The price of two Adults will be 100.

The price of three Adults will be 100.

The price of four Adults will be 120 = 100 + 20.

|

**Notify amounts by Occupancy:**

Case 1:

Room uses = 1-0-0, 2-0-0, 3-0-0.

We only load price occupancy = 2 adults, 0 child and 0 baby.

:

    <BaseByGuestAmts>
        <BaseByGuestAmt Type = "14" AmountAfterTax="100.00" Code = "2-0-0"/>
    </BaseByGuestAmts>  

Room will not be available for 1 or 3 adults.

The price of 2 adults, 0 child and 0 baby will be 100.

|

Case 2:

Room uses = 2-1-0, 2-0-1.

We load price occupancy = 2 adults, 1 child and 0 baby; and for
occupancy = 2 adults, 0 child and 1 baby.

:

    <BaseByGuestAmts>
        <BaseByGuestAmt Type = "14" AmountAfterTax="95.00" Code = "2-1-0"/>
        <BaseByGuestAmt Type = "14" AmountAfterTax="80.00" Code = "2-0-1"/>
    </BaseByGuestAmts>  

The price of 2 adults, 1 child and 0 baby will be 95.

The price of 2 adults, 0 child and 1 baby will be 80.

|

HotelRatePlanNotifRS
====================

Success Response

:

    <HotelRatePlanNotifResponse xmlns="http://schemas.xmltravelgate.com/hubpush/provider/2012/10">
             <HotelRatePlanNotifResult>
                <Success xmlns="http://www.opentravel.org/OTA/2003/05"/>
             </HotelRatePlanNotifResult>
    </HotelRatePlanNotifResponse>

|

Error Response

:

    <HotelRatePlanNotifResponse xmlns="http://schemas.xmltravelgate.com/hubpush/provider/2012/10">
         <HotelRatePlanNotifResult>
            <Errors xmlns="http://www.opentravel.org/OTA/2003/05">
               <Error ShortText="Incomplete AdditionalGuestAmount values" Code="7"/>
            </Errors>
         </HotelRatePlanNotifResult>
      </HotelRatePlanNotifResponse>

|

HotelAvailNotif
===============

Provider will send an HotelAvailNotifRQ message to push availabilities
to seller. XTG will process data and response with error code if needed.

|

HotelAvailNotifRQ
=================

**Example for RatePlan**

:

    <HotelAvailNotif>
      <request>
        <POS>
          <Source>
            <RequestorID ID = "Provider1"></RequestorID>
            <BookingChannel>
              <CompanyName Code = "ClientTravelAgency1"></CompanyName>
            </BookingChannel>
          </Source>
        </POS>
        <AvailStatusMessages HotelCode = "12">
          <AvailStatusMessage BookingLimit = "9">
            <StatusApplicationControl Start = "2013-12-20" End = "2013-12-25" RatePlanCode = "BAR" InvCode = "APT" InvType = "ROOM" Mon = "true" Tue = "true" Weds = "true" Thur = "false" Fri = "true" Sat = "true" Sun = "true"/>
            <LengthsOfStay ArrivalDateBased = "true">
              <LengthOfStay Time = "2" TimeUnit = "Day" MinMaxMessageType = "MinLOS"/>
              <LengthOfStay Time = "8" TimeUnit = "Day" MinMaxMessageType = "MaxLOS"/>
            </LengthsOfStay>
            <RestrictionStatus Status = "Open" SellThroughOpenIndicator = "false" MinAdvancedBookingOffset = "5"/>
          </AvailStatusMessage>
          <AvailStatusMessage BookingLimit = "12">
            <StatusApplicationControl Start = "2013-12-20" End = "2013-12-21" RatePlanCode = "LOWCOST" InvCode = "JUN_1" InvType = "ROOM" Mon = "false" Tue = "false" Weds = "false" Thur = "false" Fri = "true" Sat = "true" Sun = "false"/>
            <RestrictionStatus Restriction = "Master" Status = "Close"/>
          </AvailStatusMessage>
          <AvailStatusMessage BookingLimit = "12">
            <StatusApplicationControl Start = "2013-12-22" End = "2013-12-25" RatePlanCode = "LOWCOST" InvCode = "JUN_1" InvType = "ROOM" Mon = "true" Tue = "true" Weds = "true" Thur = "false" Fri = "false" Sat = "false" Sun = "true"/>
            <RestrictionStatus Status = "Close" Restriction = "Arrival"/>
          </AvailStatusMessage>
          <AvailStatusMessage BookingLimit = "7">
            <StatusApplicationControl Start = "2013-12-20" End = "2013-12-25" RatePlanCode = "LOWCOST" InvCode = "STD1" InvType = "ROOM" Mon = "true" Tue = "true" Weds = "true" Thur = "false" Fri = "true" Sat = "true" Sun = "true"/>
            <LengthsOfStay ArrivalDateBased = "true">
              <LengthOfStay Time = "3" TimeUnit = "Day" MinMaxMessageType = "MinLOS"/>
              <LengthOfStay Time = "9" TimeUnit = "Day" MinMaxMessageType = "MaxLOS"/>
            </LengthsOfStay>
            <RestrictionStatus SellThroughOpenIndicator = "true" MinAdvancedBookingOffset = "6"/>
          </AvailStatusMessage>
          <AvailStatusMessage BookingLimit = "5">
            <StatusApplicationControl Start = "2013-12-26" End = "2013-12-27" InvCode = "STD1" InvType = "ROOM" Mon = "true" Tue = "true" Weds = "true" Thur = "false" Fri = "true" Sat = "true" Sun = "true"/>
          </AvailStatusMessage>
        </AvailStatusMessages>
      </request>
    </HotelAvailNotif>

|

**Example for Derived RatePlan**

:

    <HotelAvailNotif xmlns = "http://schemas.xmltravelgate.com/hubpush/provider/2012/10">
      <request Version = "0">
        <POS xmlns = "http://www.opentravel.org/OTA/2003/05">
          <Source>
            <RequestorID ID = "Provider1"></RequestorID>
            <BookingChannel>
              <CompanyName Code = "ClientTravelAgency1"></CompanyName>
            </BookingChannel>
          </Source>
        </POS>
        <AvailStatusMessages HotelCode = "1" xmlns = "http://www.opentravel.org/OTA/2003/05">
          <AvailStatusMessage>
            <StatusApplicationControl Sun = "true" Sat = "true" Fri = "true" Thur = "true" Weds = "true" Tue = "true" Mon = "true" RatePlanCode = "DRV" Start = "2014-07-01" End = "2014-07-31"/>
            <LengthsOfStay ArrivalDateBased = "false">
              <LengthOfStay Time = "3" TimeUnit = "Day" MinMaxMessageType = "MinLOS"/>
              <LengthOfStay Time = "3" TimeUnit = "Day" MinMaxMessageType = "MaxLOS"/>
            </LengthsOfStay>
            <RestrictionStatus MinAdvancedBookingOffset = "5"/>
          </AvailStatusMessage>
        </AvailStatusMessages>
      </request>
    </HotelAvailNotif>

  -------------------------------------------------------------------------
  Element     N T Description
              u y 
              m p 
              b e 
              e   
              r   
  ----------- - - ---------------------------------------------------------
  HotelAvailN 1   Root Node
  otif/reques     
  t               

  AvailStatus 1   
  Messages        

  <*@HotelCod 1 S Hotel code whose information is provided by the method
  e>\*          t 
                r 
                i 
                n 
                g 

  AvailStatus 1   
  Messages/Av .   
  ailStatusMe .   
  ssage       n   

  <*@BookingL 0 I Identifies the number of available rooms per Room &
  imit>\*     . n RatePlan for the indicated dates. Not mandatory when the
              . t @Status is Close. Not used for derived rates
              1 e 
                g 
                e 
                r 

  AvailStatus 1   
  Messages/Av     
  ailStatusMe     
  ssage/Statu     
  sApplicatio     
  nControl        

  <*@Start>\* 1 D Start date
                a 
                t 
                e 

  <*@End>\*   1 D End date
                a 
                t 
                e 

  <*@RatePlan 0 S Rate Plan Code. If not specified then all rates
  Code>\*     . t containing @InvCode Room will be updated
              . r 
              1 i 
                n 
                g 

  <*@InvCode> 0 S Room Code. Not used for derived rates
  \*          . t 
              . r 
              1 i 
                n 
                g 

  <*@InvType> 0 S Product type (ROOM). Not used for derived rates
  \*          . t 
              . r 
              1 i 
                n 
                g 

  <*@Mon>\*   1 B Indicates whether the AvailStatusMessage data applies to
                o Mondays
                o 
                l 
                e 
                a 
                n 

  <*@Tue>\*   1 B Indicates whether the AvailStatusMessage data applies to
                o Tuesdays
                o 
                l 
                e 
                a 
                n 

  <*@Weds>\*  1 B Indicates whether the AvailStatusMessage data applies to
                o Wednesdays
                o 
                l 
                e 
                a 
                n 

  <*@Thur>\*  1 B Indicates whether the AvailStatusMessage data applies to
                o Thursdays
                o 
                l 
                e 
                a 
                n 

  <*@Fri>\*   1 B Indicates whether the AvailStatusMessage data applies to
                o Fridays
                o 
                l 
                e 
                a 
                n 

  <*@Sat>\*   1 B Indicates whether the AvailStatusMessage data applies to
                o Saturdays
                o 
                l 
                e 
                a 
                n 

  <*@Sun>\*   1 B Indicates whether the AvailStatusMessage data applies to
                o Sundays
                o 
                l 
                e 
                a 
                n 

  AvailStatus 0   
  Messages/Av .   
  ailStatusMe .   
  ssage/Lengt 1   
  hsOfStay        

  AvailStatus 1   
  Messages/Av .   
  ailStatusMe .   
  ssage/Lengt 2   
  hsOfStay/Le     
  ngthOfStay      

  <*@ArrivalD 0 B When its true, the minimum and maximum stay is checked
  ateBased>\* . o ONLY the first day of the availability, when false or not
              . o indicated, the minimum and maximum stay is checked all
              1 l the availability days. If both values are needed two
                e AvailStatusMessage must be send.
                a 
                n 

  <*@Time>\*  1 I Indicates the number of @TimeUnit for this stay
                n 
                t 
                e 
                g 
                e 
                r 

  <*@TimeUnit 1 S Day
  >\*           t 
                r 
                i 
                n 
                g 

  <*@MinMaxMe 1 S (MinLOS, MaxLOS) Indicates the minimum or maximum stay
  ssageType>\   t for his AvailStatusMessage.
  *             r 
                i 
                n 
                g 

  AvailStatus 0   
  Messages/Av .   
  ailStatusMe .   
  ssage/Restr 1   
  ictionStatu     
  s               

  <*@Status>\ 0 S (Open, Close). Not used for derived rates
  *           . t 
              . r 
              1 i 
                n 
                g 

  <*@Restrict 0 S Master. This is the master availability. If master
  ion>\*      . t availability is ‘Closed’, the product is not bookable if
              . r any of the stay dates includes one of the dates specified
              1 i by the Application Control element. If master
                n availability is ‘Open’, additional restrictions on
                g arrival and departure may be placed (Master, Arrival,
                  Departure). Not used for derived rates

  <*@MinAdvan 0 I Minimum number of days before the check-in date after
  cedBookingO . n which the product is not available to be booked. This
  ffset>\*    . t restriction is usually used to offer discounts on early
              1 e bookings
                g 
                e 
                r 

  <*@MaxAdvan 0 I Maximum number of days before the check-in date after
  cedBookingO . n which the product is not available to be booked. This
  ffset>\*    . t restriction is usually used to offer last minute
              1 e discounts on unsold inventory.
                g 
                e 
                r 

  <*@SellThro 0 B When @Status is open, in this element you can indicate
  ughOpenIndi . o this room or room/ratePlan can be sold without limit
  cator>\*    . o (like BookingLimit=MaxInteger). Not used for derived
              1 l rates
                e 
                a 
                n 
  -------------------------------------------------------------------------

|

HotelAvailNotifRS
=================

Success Response

:

    <HotelAvailNotifResponse xmlns="http://schemas.xmltravelgate.com/hubpush/provider/2012/10">
      <HotelAvailNotifResult>
        <Success xmlns="http://www.opentravel.org/OTA/2003/05"/>
      </HotelAvailNotifResult>
    </HotelAvailNotifResponse>

|

Error Response

:

    <HotelAvailNotifResponse xmlns="http://schemas.xmltravelgate.com/hubpush/provider/2012/10">
      <HotelAvailNotifResult>
        <Errors xmlns="http://www.opentravel.org/OTA/2003/05">
          <Error ShortText="AvailStatusMessages not found" Code="2"/>
        </Errors>
      </HotelAvailNotifResult>
    </HotelAvailNotifResponse>

|

Error Codes
===========

  ------------------------------------------------------------------------
  Error Code    Error Description
  ------------- ----------------------------------------------------------
  -1            Validation error

  1             POS credentials not found

  2             HotelCode or RatePlanList not found

  3             Rates not found

  4             Incomplete Rate values

  6             Incomplete AvailStatusMessage StatusApplicationControl
                Values

  7             Incomplete AdditionalGuestAmount values

  8             SellableProduct not found

  9             Room not found in SellableProduct
  ------------------------------------------------------------------------

|
