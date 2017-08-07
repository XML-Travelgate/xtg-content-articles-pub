---
title: Notify Messages
keywords: hotel-push, messages, messages files, notify messages
search: Hotel-Push - MessagesFiles - Notify Messages
sidebar: mydoc_sidebar
permalink: /docs/hotel-push/messages-files/notify-messages
---

Providers sends data to Sellers (Negotiation is started by Providers).


### HotelRatePlanInventoryNotif


Provider will send an HotelRatePlanInventoryNotifRQ message to push the Hotel set up information to
seller. XTG will process data and response with error code if needed.


### HotelRatePlanInventoryNotifRQ
~~~xml
<HotelRatePlanInventoryNotif xmlns = "http://schemas.xmltravelgate.com/hubpush/provider/2012/10">
    <request PrimaryLangID = "ES" Version = "0">
        <RatePlans HotelCode = "1" xmlns = "http://www.opentravel.org/OTA/2003/05">
            <RatePlan Duration = "0" CurrencyCode = "EUR" RatePlanCode = "BAR" RatePlanStatusType = "Active">
                <Rates>
                    <Rate>
                        <AdditionalGuestAmounts>
                            <AdditionalGuestAmount AgeQualifyingCode = "8" MaxAge = "12"/>
                            <AdditionalGuestAmount AgeQualifyingCode = "7" MaxAge = "2"/>
                        </AdditionalGuestAmounts>
                        <PaymentPolicies>
                            <GuaranteePayment PaymentCode = "MerchantPayment"/>
                        </PaymentPolicies>
                        <MealsIncluded MealPlanCodes = "14"/>
                    </Rate>
                </Rates>
                <SellableProducts>
                    <SellableProduct InvCode = "STD" InvType = "ROOM" InvStatusType = "Active">
                        <GuestRoom>
                            <Quantities StandardNumBeds = "2"/>
                            <Occupancy MinOccupancy = "2" MaxOccupancy = "2" AgeQualifyingCode = "10"/>
                            <Room RoomTypeCode = "STD" RoomID = "1"/>
                            <Description>
                                <Text>Standard</Text>
                            </Description>
                        </GuestRoom>
                    </SellableProduct>
                    <SellableProduct InvCode = "STD" InvType = "ROOM" InvStatusType = "Active">
                        <GuestRoom>
                            <Quantities StandardNumBeds = "2"/>
                            <Occupancy MinOccupancy = "2" MaxOccupancy = "2" AgeQualifyingCode = "10"/>
                            <Occupancy MinOccupancy = "1" MaxOccupancy = "1" AgeQualifyingCode = "7"/>
                            <Room RoomTypeCode = "STD" RoomID = "1"/>
                            <Description>
                                <Text>Standard</Text>
                            </Description>
                        </GuestRoom>
                    </SellableProduct>
                    <SellableProduct InvCode = "STD" InvType = "ROOM" InvStatusType = "Active">
                        <GuestRoom>
                            <Quantities StandardNumBeds = "2"/>
                            <Occupancy MinOccupancy = "1" MaxOccupancy = "1" AgeQualifyingCode = "10"/>
                            <Occupancy MinOccupancy = "1" MaxOccupancy = "1" AgeQualifyingCode = "8"/>
                            <Occupancy MinOccupancy = "1" MaxOccupancy = "1" AgeQualifyingCode = "7"/>
                            <Room RoomTypeCode = "STD" RoomID = "1"/>
                            <Description>
                                <Text>Standard</Text>
                            </Description>
                        </GuestRoom>
                    </SellableProduct>
                    <SellableProduct InvCode = "JSUIT" InvType = "ROOM" InvStatusType = "Active">
                        <GuestRoom>
                            <Quantities StandardNumBeds = "2"/>
                            <Occupancy MinOccupancy = "1" MaxOccupancy = "1" AgeQualifyingCode = "10"/>
                            <Room RoomTypeCode = "JSUIT" RoomID = "8"/>
                            <Description>
                                <Text>Junior Suite</Text>
                            </Description>
                        </GuestRoom>
                    </SellableProduct>
                    <SellableProduct InvCode = "JSUIT" InvType = "ROOM" InvStatusType = "Active">
                        <GuestRoom>
                            <Quantities StandardNumBeds = "2"/>
                            <Occupancy MinOccupancy = "2" MaxOccupancy = "2" AgeQualifyingCode = "10"/>
                            <Room RoomTypeCode = "JSUIT" RoomID = "8"/>
                            <Description>
                                <Text>Junior Suite</Text>
                            </Description>
                        </GuestRoom>
                    </SellableProduct>
                    <SellableProduct InvCode = "JSUIT" InvType = "ROOM" InvStatusType = "Active">
                        <GuestRoom>
                            <Quantities StandardNumBeds = "2"/>
                            <Occupancy MinOccupancy = "3" MaxOccupancy = "3" AgeQualifyingCode = "10"/>
                            <Room RoomTypeCode = "JSUIT" RoomID = "8"/>
                            <Description>
                                <Text>Junior Suite</Text>
                            </Description>
                        </GuestRoom>
                    </SellableProduct>
                </SellableProducts>
                <Description>
                    <Text>bb</Text>
                </Description>
            </RatePlan>
        </RatePlans>
        <TPA_Extensions xmlns = "http://www.opentravel.org/OTA/2003/05">
            <Attribute key = "HotelNotifType" value = "New"/>
        </TPA_Extensions>
    </request>
</HotelRatePlanInventoryNotif>

~~~

| **Element**				| **Number** | **Type**	| **Description**					|
| ------------------------------------- | ---------- | -------- | ----------------------------------------------------- |
| HotelRatePlanInventoryNotif/request		| 1 	     |		| Root Node.						|
| RatePlans			   	| 1   	     |		|							|
| @HotelCode				| 1	     | String	| Hotel code whose information is provided by the method. |
| RatePlans/RatePlan			| 0..n	     |		| Present if rate exists.				|
| @RatePlanCode				| 1	     | String	| Rate code.						|
| @RatePlanNotifType			| 0..1	     | String	| New, Delta or Remove |
| @RatePlanStatusType			    | 1		 | String   | Active or Deactivated.				|
| @CurrencyCode				| 0..1	     | String	| ISO Currency (EUR). Not used for derived rates.	|
| RatePlans/BookingRules		    | 0..1       |	    | Present if exists booking rules for the given RatePlan.|
| BookingRules/BookingRule		    | 1..n       |	    | Booking rules.					|
| @Code       				    | 0..1	 | String   | Code of the booking rule (empty if are viewships conditions). |
| BookingRule/CancelPenalties		    | 1          | 	    | Cancel penalties of the current booking rule.	|
| CancelPenalties/CancelPenalty		    | 1..n       |	    | Cancel penalty.					|
| @NonRefundable			    | 1 	 | Boolean  | Indicates if the rateplan is refundable or not. 	|
| CancelPenalty/Deadline 		    | 1          |	    | Contains information about the the deadline of the cancel penalty. |
| @OffsetTimeUnit			    | 1 	 | String   | Indicates the units of time that apply to the deadline.|
| @OffsetUnitMultiplier			    | 1 	 | Integer  | The number of units of DeadlineTimeUnit.  	|
| @OffsetDropTime			    | 1 	 | String   | Indicating when the deadline drop time goes into effect. |
| CancelPenalty/AmountPercent		    | 1          |	    | Contains information about the the deadline of the cancel penalty. |
| @NmbrOfNights				    | 0..1	 | Integer  | Number of nights that will be charged in case of cancellation applying the current cancel penalty. NmbrOfNights, Percent or Amount must be present. |
| @Percent    				    | 0..1	 | Decimal  | Percent of the total amount that will be charged in case of cancellation applying the current cancel penalty. NmbrOfNights, Percent or Amount must be present. |
| @Amount     				    | 0..1	 | Decimal  | Amount that will be charged in case of cancellation applying the current cancel penalty. NmbrOfNights, Percent or Amount must be present. |
| @CurrencyCode				    | 0..1	 | String   | Currency code of the amount. Must be present if amount is present. |
| RatePlans/RatePlan/Rates		| 1	     |		|							|
| RatePlans/RatePlan/Rates/Rate		| 1..n	     |		|							|
| RatePlans/RatePlan/Rates/AdditionalGuestAmounts		| 1	     |		|							|
| AdditionalGuestAmounts/AdditionalGuestAmount		| 1..2	     |		|							|
| @AgeQualifyingCode		| 1	     |	Integer	|	Qualifying code of the additional guest.	8 - Child, 7 - Infant					|
| @MaxAge		| 1	     |	Integer	|		Max age not inclusive of the additional guest. Not inclusive.					|
| RatePlans/RatePlan/Rates/Rate/PaymentPolicies			   | 1     	 |	    | Node that contains the accepted payments information. |
| PaymentPolicies/GuaranteePayment	   | 1..n    	 |	    | Node that contains information about an accepted payment. |
| @PaymentCode				   | 1     	 |	    | Contains the payment method accepted by the rate. See Payment Type Codes list in section 7.6.3. |
| GuaranteePayment/AcceptedPayments	   | 0..1    	 |	    | Node that contains the accepted payments information. Only present if PaymentCode is not "MerchantPayment". |
| AcceptedPayments/AcceptedPayment	   | 1..n    	 |	    | Node that contains the credit card accepted.	|
| AcceptedPayment/PaymentCard		   | 1..n    	 |	    | Node that contains the credit card accepted.	|
| @CardCode        			   | 1     	 | String   | Contains the credit card code. See Credit Card Codes list in section 7.6.4. |
| RatePlans/RatePlan/Rates/Rate/MealsIncluded | 0..1	 |	    | Present if board is included with this rate.	|
| @MealPlanCodes			   | 1 		 | Integer  | OTA MPT Code. 					|				|
| RatePlans/RatePlan/SellableProducts	   | 0..1    	 |	    | List of sellable products. In derived rates, if it is not present it applies to all rooms. In other cases, it informs the rooms that applies. |
| SellableProducts/SellableProduct | 0..n |	    | Present if rooms associed with this rate.		|
| @InvCode    				   | 1 		 | Integer  | Sellable Product Code.				|
| @InvType    				   | 1 		 | Integer  | Sellable product type (ROOM).			|
| @InvStatusType			   | 1 	 	 | String   | Active or Deactivated.				|
| RatePlans/RatePlan/SellableProduct/GuestRoom | 1..n	 |	    |							|
| RatePlans/RatePlan/SellableProduct/GuestRoom/Quantities | 1 |	    |     						|
| @StandardNumBeds			   | 1 		 | Integer  | Standard occupation of room. 			|
| RatePlans/RatePlan/SellableProduct/GuestRoom/Occupancy | 1 |	    |     						|
| @MinOccupancy				   | 1 		 | Integer  | Min occupation.					|
| @MaxOccupancy				   | 1 		 | Integer  | Max occupation.  					|
| @AgeQualifyingCode			   | 1 		 | Integer  | (10 - Adult,8 - Child,7 - Infant).		|
| RatePlans/RatePlan/SellableProduct/GuestRoom/Room | 1 |  | 			|
| @RoomTypeCode    				   | 1 		 | String  | Room Code.				|
| @RoomID    				   | 1 		 | Integer  | Room Id.				|
| RatePlans/RatePlan/SellableProduct/GuestRoom/Description/Text | 1 | String | Room description.			|
| TPA_Extensions			   	| 0..1    	|		| Optional, only added when create or delete an hotel. |
| TPA_Extensions/Attribute            		| 1       	|		|							|
| @key        			| 1  		| String	| HotelNotifType.						|
| @value      			| 1  		| String	| New - You will create an hotel. Remove - You will remove all the hotel setup. |




### HotelRatePlanNotif


Provider will send an HotelRatePlanNotifRQ message to push Rates to
seller. XTG will process data and response with error code if needed.



### HotelRatePlanNotifRQ


**Example for RatePlan**


~~~xml
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
~~~


**Example for Derived RatePlan**


~~~xml
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
~~~


| **Element**				| **Number** | **Type**	| **Description**					|
| ------------------------------------- | ---------- | -------- | ----------------------------------------------------- |
| HotelRatePlanNotif/request		| 1 	     |		| Root Node.						|
| RatePlans			   	| 1   	     |		|							|
| @HotelCode				| 1	     | String	| Hotel code whose information is provided by the method. |
| RatePlans/RatePlan			| 1..n	     |		| Present if rate exists.				|
| @RatePlanCode				| 1	     | String	| Rate code.						|
| @RatePlanStatusType			| 0..1	     | String	| Active or Deactivated (You can save prices with initial status deactivated if you want). If this attribute is missing, the price will be saved as active. |
| @BaseRatePlanCode			| 0..1	     | String	| Rate code of the base RatePlan. Only used for derived rates. |
| @CurrencyCode				| 0..1	     | String	| ISO Currency (EUR). Not used for derived rates.	|
| _@SuplementsNotifTypeSpecified	| 0..1	     | Boolean	| Rate code. Not used for derived rates.		|
| _@SuplementsNotifType			| 0..1	     | String	| Possible values are Overlay or Delta. If not specified or Delta, Supplements will not be overwritten. If Overlay supplements will be overwritten. Not used for derived rates. |
| RatePlans/RatePlan/Rates/Rate		| 1	     |		|							|
| @Start 				| 1	     | Date	| Start date of rate.					|
| @End   				| 1	     | Date	| End date of rate.					|
| @AdjustedPercentage			| 0..1	     | Decimal	| The percentage off the base rate plan amount used to determine the price of this derived rate plan. Only used for derived rates. |
| @AdjustedAmount			| 0..1	     | Decimal	| The amount which should be added to the base rate plan to determine the price of this derived rate plan. Only used for derived rates. |
| @AdjustUpIndicator			| 0..1	     | Boolean	| When true, the adjusted amount or adjusted percentage is added to the amount specified for the base rate plan to determine the derived rate amount. When false, the adjusted amount or adjusted percentage is subtracted from the amount specified for the base rate plan to determine the derived rate amount. Only used for derived rates. |
| RatePlans/RatePlan/Rates/Rate/BaseByGuestAmts | 0..1 |	|							|
| RatePlans/RatePlan/Rates/Rate/BaseByGuestAmts/BaseByGuestAmt | 1..n |	|						|
| @AmountAfterTax			| 1	     | Decimal	| Total amount for @NumberOfGuests by day indicated.	|
| @NumberOfGuests			| 0..1	     | Integer	| How many adults are the @AmountAfterTax for day indicated. If @NumberOfGuests is not informed then @Type must be informed. The maximum @NumberOfGuests is the standard occupancy of the room. |
| @Type  				| 0..1	     | Integer	| Amounts are per Room or per Occupancy instead of per Pax. If @Type=25, price is per room, 1 BaseByGuestAmt is allowed and @NumberOfGuests and AdditionalGuestAmounts are not allowed. If @Type=14, price is per occupancy, @Code is mandatory and @NumberOfGuests and AdditionalGuestAmounts are not allowed. |
| @Code  				| 0..1	     | String	| Mandatory if @Type=14. The occupancy code is defined by AdultNumber-ChildNumber-InfantNumber. @Code for an occupancy of 2 adults, 1 child and 0 babies would be "2-1-0". |
| RatePlans/RatePlan/Rates/Rate/AdditionalGuestAmounts	| 0..1 | | Not used for derived rates.				|
| RatePlans/RatePlan/Rates/Rate/AdditionalGuestAmounts/AdditionalGuestAmount | 1..n | | Price and information about the additional pax (children, infants or extra adults). |
| @MaxAdditionalGuests			| 1	    | Integer	| Number of additional pax, one node for each additional pax, int the above example has one for first child, and one for second. |
| @Type  				| 0..1	    | String	| OTA AmountDeterminationType. If not specified then the price is a supplement, if @Type is Exclusive then the the price is absolute. |
| @AgeQualifyingCode			| 1	    | Integer	| (10 - Adult,8 - Child,7 - Infant).			|
| @Amount				| 1	    | Decimal	| Price for each additional pax.			|
| RatePlans/Supplements			| 0..1	    | 		|  Present if supplements by board exists. Not used for derived rates. |
| RatePlans/Supplements/Supplement	| 1..n	    |		|							|
| @Start 				| 1	    | Date	| Start date of this supplement.			|
| @End   				| 1	    | Date	| End date of this supplement.				|
| @AgeQualifyingCode			| 0..1	    | Integer	| Age qualifyingCode which affects this supplement (10 - Adult,8 - Child,7 - Infant). Not allowed if charging board supplement by occupancy. |
| @ChargeTypeCode			| 0..1	    | String	| Indicates the board supplement occupancy. Only allowed if charging board supplement by occupancy. The occupancy code is defined by AdultNumber-ChildNumber-InfantNumber. @ChargeTypeCode for an occupancy of 2 adults, 1 child and 0 babies would be "2-1-0". |
| @Amount				| 1	    | Decimal	| Amount of supplement.					|
| @SupplementType			| 1	    | String	| (Board).						|
| @InvCode				| 1	    | String	| OTA MPT Code if @SupplementType is Board. 		|
| RatePlans/RatePlan/SellableProducts	| 0..1	    |		| List of sellable products. Null for derived rates. 	|
| RatePlans/SellableProducts/SellableProduct | 1..n |		|							|
| @InvCode				| 1	    | Integer	| Sellable Product Code.				|
| @InvType				| 1	    | Integer	| Sellable product type (ROOM).				|



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

- If the price is per occupancy then Type should be 14 and Code should
be specified. 

The occupancy code is defined by
AdultNumber-ChildNumber-InfantNumber, for an occupancy of 2 adults, 1
child and 0 babies should be "2-1-0".

-   In samples room uses are specified using = AdultNumber -
    ChildNumber - InfantNumber.



**Notify amounts by Guests:**

Case 1:

Standard occupancy = 2.

Room uses = 1-0-0, 2-0-0.

We only load the price for standard occupancy.


~~~xml
    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>  
~~~


There is no price for one adult, so it wont be available.

The price of two adults will be 100 = 2\*(100/2).



Case 2:

Standard occupancy = 2.

Room uses = 1-0-0, 2-0-0.

We load the price for standard occupancy and the price for 1 Adult.


~~~xml
    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "1" AmountAfterTax="100.00"/>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="130.00"/>
    </BaseByGuestAmts>
~~~

The price of one Adult (Also known as Double Single Use) will be 100 =
100.

The price of two adults will be 130 = 2\*(130/2).



Case 3:

Standard occupancy = 2.

Room uses = 1-0-0, 2-0-0, 3-0-0.

We load the price for standard occupancy and the price for 1 additional
Adult Type default.


~~~xml
    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "40.00" AgeQualifyingCode = "10"/>
    </AdditionalGuestAmounts>
~~~


There is no price for one adult, so it wont be available.

The price of two Adult will be 100 = 2\*(100/2).

The price of three Adults will be 190 = (100/2) + (100/2) + ((100/2) +
(40).



Case 4:

Standard occupancy = 2

Room uses = 1-0-0, 2-0-0, 3-0-0

We load the price for standard occupancy and the price for 1 additional
Adult Type Exclusive.


~~~xml
    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "40.00" AgeQualifyingCode = "10" Type="Exclusive"/>
    </AdditionalGuestAmounts>
~~~


There is no price for one adult, so it wont be available.

The price of two Adult will be 100 = 2*(100/2).

The price of three Adults will be 140 = (100/2) + (100/2) + 40.



Case 5:

Standard occupancy = 2.

Room uses = 1-0-0, 2-0-0, 1-1-0.

We load price for standard occupancy and the price for 1 additional
Child (AgeQualifyingCode = "8") Type default.


~~~xml
    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "40.00" AgeQualifyingCode = "8" />
    </AdditionalGuestAmounts>
~~~


There is no price for one adult, so it wont be available.

The price of two Adult will be 100 = 2*(100/2).

The price of one Adult and one Child will be 100 = 2*(100/2). All pax
under standard occupancy are considered as adults.



Case 5.1:

standard occupancy = 2.

room uses = 1-0-0, 2-0-0, 1-0-1.

NOTE: The same samples with children are valid for babies specifying
AgeQualifyingCode = "7".

We load price for standard occupancy and the price for 1 additional Baby
(AgeQualifyingCode = "7") Type default.


~~~xml
    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "40.00" AgeQualifyingCode = "7" />
    </AdditionalGuestAmounts>
~~~


There is no price for one adult, so it wont be available.

The price of two Adult will be 100 = 2\*(100/2).

The price of one Adult and one Child will be 100 = 2\*(100/2). All pax
under standard occupancy are considered as adults.



Case 6:

Standard occupancy = 2.

Room uses = 1-0-0, 2-0-0, 2-1-0.

We load price for standard occupancy and the price for 1 additional
Child Type default negative price


~~~xml
    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "-40.00" AgeQualifyingCode = "8" />
    </AdditionalGuestAmounts>
~~~


There is no price for one adult, so it wont be available.

The price of two Adults will be 100 = 2*(100/2)

The price of one Adult and one Child will be 60 = 2*(100/2) +
((100/2) -40).



Case 7:

Standard occupancy = 2.

Room uses = 1-0-0, 2-0-0, 3-0-0, 4-0-0.

We load the price of standard occupancy and the price for 1 additional
adult and the price for 2 additional adults.


~~~xml
    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "10.00" AgeQualifyingCode = "10" />
        <AdditionalGuestAmount MaxAdditionalGuests = "2" Amount = "-15.00" AgeQualifyingCode = "10" />
    </AdditionalGuestAmounts>
~~~


There is no price for one adult, so it wont be available.

The price of two Adults will be 100 = 2*(100/2).

The price of three Adults will be 160 = (100/2) + (100/2) + ((100/2) +
10).

The price of four Adults will be 195 = (100/2) + (100/2) + ((100/2) +
10) + ((100/2) - 15).



Case 8:

Standard occupancy = 2.

Room uses = 1-0-0, 2-0-0, 3-0-0, 4-0-0.

We load the price of standard occupancy and the price for each
additional adult (Without specifying MaxAdditionalGuests).


~~~xml
    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "2" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "-10.00" AgeQualifyingCode = "10" />
    </AdditionalGuestAmounts>
~~~


There is no price for one adult, so it wont be available.

The price of two Adults will be 100 = 2*(100/2).

The price of three Adults will be 140 = (100/2) + (100/2) +
((100/2) -10).

The price of four Adults will be 180 = (100/2) + (100/2) +
((100/2) -10) + ((100/2) - 10).



Case 9:

Standard occupancy = 3.

Room uses = 1-0-0, 2-0-0, 3-0-0, 4-0-0, 5-0-0.

We load the price of standard occupancy and the price for 1 additional
adult and the price for 2 additional adults.


~~~xml
    <BaseByGuestAmts>
        <BaseByGuestAmt NumberOfGuests = "3" AmountAfterTax="150.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "-10.00" AgeQualifyingCode = "10" />
        <AdditionalGuestAmount MaxAdditionalGuests = "2" Amount = "15.00" AgeQualifyingCode = "10" />
    </AdditionalGuestAmounts>
~~~


There is no price for one adult, so it wont be available.

There is no price for two adults, so it wont be available.

The price of three Adults will be 150 = 3\*(150/3).

The price of four Adults will be 190 = (150/3) + (150/3) + (150/3) +
((150/3) - 10).

The price of five Adults will be 255 = (150/3) + (150/3) + (150/3) +
((150/3) - 10) + ((150/3) + 15).



**Notify amounts with price per room and additional guests**

Case 1:

Standard occupancy = 2.

Room uses = 1-0-0, 2-0-0, 1-1-0.

We load the price per room Type="25".


~~~xml
    <BaseByGuestAmts>
        <BaseByGuestAmt Type = "25" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
~~~


The price of one Adult will be 100.

The price of two Adults will be 100.

The price of one Adult and one Child will be 100.



Case 2:

Standard occupancy = 2.

Room uses = 1-0-0, 2-0-0, 3-0-0, 1-1-0, 3-1-0.

We load the price per room but also the price for 1 additional adult and
the price for 1 additional child.

NOTE: the AdditionalGuestAmount Type in price per room has to be
default. Exclusive type not allowed.


~~~xml
    <BaseByGuestAmts>
        <BaseByGuestAmt Type = "25" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "20.00" AgeQualifyingCode = "10" />
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "10.00" AgeQualifyingCode = "8" />
    </AdditionalGuestAmounts>
~~~


The price of one Adult will be 100.

The price of two Adults will be 100.

The price of three Adults will be 120 = 100 + 20.

The price of one Adult and one Child will be 110 = 100 + 10.

The price of three Adults and one Child will be 130 = 100 + 20 + 10.



Case 3:

Standard occupancy = 3.

Room uses = 1-0-0, 2-0-0, 3-0-0, 4-0-0.

We load the price per room but also the price for 1 additional adult.


~~~xml
    <BaseByGuestAmts>
        <BaseByGuestAmt Type = "25" AmountAfterTax="100.00"/>
    </BaseByGuestAmts>
    <AdditionalGuestAmounts>
        <AdditionalGuestAmount MaxAdditionalGuests = "1" Amount = "20.00" AgeQualifyingCode = "10" />
    </AdditionalGuestAmounts>
~~~


The price of one Adult will be 100.

The price of two Adults will be 100.

The price of three Adults will be 100.

The price of four Adults will be 120 = 100 + 20.



**Notify amounts by Occupancy:**

Case 1:

Room uses = 1-0-0, 2-0-0, 3-0-0.

We only load price occupancy = 2 adults, 0 child and 0 baby.


~~~xml
    <BaseByGuestAmts>
        <BaseByGuestAmt Type = "14" AmountAfterTax="100.00" Code = "2-0-0"/>
    </BaseByGuestAmts> 
~~~


Room will not be available for 1 or 3 adults.

The price of 2 adults, 0 child and 0 baby will be 100.



Case 2:

Room uses = 2-1-0, 2-0-1.

We load price occupancy = 2 adults, 1 child and 0 baby; and for
occupancy = 2 adults, 0 child and 1 baby.


~~~xml
    <BaseByGuestAmts>
        <BaseByGuestAmt Type = "14" AmountAfterTax="95.00" Code = "2-1-0"/>
        <BaseByGuestAmt Type = "14" AmountAfterTax="80.00" Code = "2-0-1"/>
    </BaseByGuestAmts>  
~~~


The price of 2 adults, 1 child and 0 baby will be 95.

The price of 2 adults, 0 child and 1 baby will be 80.



### HotelRatePlanNotifRS


Success Response


~~~xml
    <HotelRatePlanNotifResponse xmlns="http://schemas.xmltravelgate.com/hubpush/provider/2012/10">
             <HotelRatePlanNotifResult>
                <Success xmlns="http://www.opentravel.org/OTA/2003/05"/>
             </HotelRatePlanNotifResult>
    </HotelRatePlanNotifResponse>
~~~


Error Response


~~~xml
    <HotelRatePlanNotifResponse xmlns="http://schemas.xmltravelgate.com/hubpush/provider/2012/10">
         <HotelRatePlanNotifResult>
            <Errors xmlns="http://www.opentravel.org/OTA/2003/05">
               <Error ShortText="Incomplete AdditionalGuestAmount values" Code="7"/>
            </Errors>
         </HotelRatePlanNotifResult>
      </HotelRatePlanNotifResponse>
~~~


### HotelAvailNotif


Provider will send an HotelAvailNotifRQ message to push availabilities
to seller. XTG will process data and response with error code if needed.



### HotelAvailNotifRQ


**Example for RatePlan**


~~~xml
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
~~~


**Example for Derived RatePlan**


~~~xml
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
~~~


| **Element**				| **Number** | **Type**	| **Description**					|
| ------------------------------------- | ---------- | -------- | ----------------------------------------------------- |
| HotelAvailNotif/request		| 1  	     |		| Root Node.						|
| AvailStatusMessages			| 1   	     |		|							|
| @HotelCode				| 1	     | String	| Hotel code whose information is provided by the method. |
| AvailStatusMessages/AvailStatusMessage | 1..n	     |		|							|
| @BookingLimit				| 0..1	     | Integer	| Identifies the number of available rooms per Room & RatePlan for the indicated dates. Not mandatory when the @Status is Close. Not used for derived rates. |
| AvailStatusMessages/AvailStatusMessage/StatusApplicationControl | 1 |	 |						|
| @Start				| 1	     | Date	| Start date.						|
| @End  				| 1	     | Date	| End date.						|
| @RatePlanCode				| 0..1	     | String	| Rate Plan Code. If not specified then all rates containing @InvCode Room will be updated. |
| @InvCode				| 0..1	     | String	| Room Code. Not used for derived rates.		|
| @InvType				| 0..1	     | String	| Product type (ROOM). Not used for derived rates.	|
| @Mon  				| 1	     | Boolean	| Indicates whether the AvailStatusMessage data applies to Mondays. |
| @Tue  				| 1	     | Boolean	| Indicates whether the AvailStatusMessage data applies to Tuesdays. |
| @Weds 				| 1	     | Boolean	| Indicates whether the AvailStatusMessage data applies to Wednesdays. |
| @Thur 				| 1	     | Boolean	| Indicates whether the AvailStatusMessage data applies to Thursdays. |
| @Fri  				| 1	     | Boolean	| Indicates whether the AvailStatusMessage data applies to Fridays. |
| @Sat  				| 1	     | Boolean	| Indicates whether the AvailStatusMessage data applies to Saturdays. |
| @Sun  				| 1          | Boolean	| Indicates whether the AvailStatusMessage data applies to Sundays. |
| AvailStatusMessages/AvailStatusMessage/LengthsOfStay | 0..1 |	|							|
| AvailStatusMessages/AvailStatusMessage/LengthsOfStay/LengthOfStay | 1..2 | |						|
| @ArrivalDateBased			| 0..1	     | Boolean	| When its true, the minimum and maximum stay is checked ONLY the first day of the availability, when false or not indicated, the minimum and maximum stay is checked all the availability days. If both values are needed two AvailStatusMessage must be send. |
| @Time 				| 1	     | Integer	| Indicates the number of @TimeUnit for this stay.	|
| @TimeUnit				| 1	     | String	| Day.							|
| @MinMaxMessageType			| 1	     | String	| (MinLOS, MaxLOS) Indicates the minimum or maximum stay for his AvailStatusMessage. |
| AvailStatusMessages/AvailStatusMessage/RestrictionStatus | 0..1 |  |							|
| @Status				| 0..1	     | String	| (Open, Close). Not used for derived rates.		|
| @Restriction				| 0..1	     | String	| Master. This is the master availability. If master availability is ‘Closed’, the product is not bookable if any of the stay dates includes one of the dates specified by the Application Control element. If master availability is ‘Open’, additional restrictions on arrival and departure may be placed (Master, Arrival, Departure). Not used for derived rates. |
| @MinAdvancedBookingOffset		| 0..1	     | Integer	| Minimum number of days before the check-in date after which the product is not available to be booked. This restriction is usually used to offer discounts on early bookings. |
| @MaxAdvancedBookingOffset		| 0..1	     | Integer	| Maximum number of days before the check-in date after which the product is not available to be booked. This restriction is usually used to offer last minute discounts on unsold inventory. |
| @SellThroughOpenIndicator		| 0..1	     | Boolean	| When @Status is open, in this element you can indicate this room or room/ratePlan can be sold without limit(like BookingLimit=MaxInteger). Not used for derived rates. |



### HotelAvailNotifRS


Success Response


~~~xml
    <HotelAvailNotifResponse xmlns="http://schemas.xmltravelgate.com/hubpush/provider/2012/10">
      <HotelAvailNotifResult>
        <Success xmlns="http://www.opentravel.org/OTA/2003/05"/>
      </HotelAvailNotifResult>
    </HotelAvailNotifResponse>
~~~


Error Response


~~~xml
    <HotelAvailNotifResponse xmlns="http://schemas.xmltravelgate.com/hubpush/provider/2012/10">
      <HotelAvailNotifResult>
        <Errors xmlns="http://www.opentravel.org/OTA/2003/05">
          <Error ShortText="AvailStatusMessages not found" Code="2"/>
        </Errors>
      </HotelAvailNotifResult>
    </HotelAvailNotifResponse>
~~~


### Error Codes




| **Error Code**	| **Error Description**						|
| --------------------- | ------------------------------------------------------------- |
| -1           		| Validation error						|
|  1            	| POS credentials not found					|
|  2            	| HotelCode or RatePlanList not found				|
|  3            	| Rates not found						|
|  4            	| Incomplete Rate values					|
|  6            	| Incomplete AvailStatusMessage StatusApplicationControl Values	|
|  7            	| Incomplete AdditionalGuestAmount values			|
|  8            	| SellableProduct not found					|
|  9            	| Room not found in SellableProduct				|


