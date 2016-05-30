---
title: Avail
keywords: hotel, data structure, avail
sidebar: mydoc_sidebar
permalink: /docs/hotel/DSF/Avail
---


### Method Goals


This method aims to return all the available options for a given date
and itinerary. It does not filter different classes, times or fares. It
will always return all results returned by the provider.


### Request Format


The availability request is very straight forward. It only requires
destination, travel dates and the number of pax in each room.


### Response Format


Results are organized in this hierarchy:

-   *Hotel* :

A list with all the hotels, including hotel name and code, *mealplans*
list, etc. returned by the provider.

-   *Mealplans* :

A list of all MealPlans returned by the provider, every *mealplan* and
its code. Every *mealplan* also contains a list of *options* for this
availability.

-   *Options* :

A list with all the *options* returned for each mealplan, every *option*
includes the total price, the conditions and the description of each
room.

The price returned should be "all inclusive". All fares, taxes and
discounts are included in the total price.



### Remarks


This method **must** be called **before** the *Valuation* method.

Our system allows for a max **25000** milliseconds before the connection
is closed.



### AvailRQ Example


~~~xml
    <AvailRQ>
        <CancellationPolicies>false</CancellationPolicies>
        <OnRequest>false</OnRequest>
        <BusinessRules>CheaperAmount</BusinessRules>
        <AvailDestinations> lista de "Destination"
            <Destination type = "CTY" code = "5"/>
        </AvailDestinations>
        <StartDate>28/01/2014</StartDate>
        <EndDate>29/01/2014</EndDate>
        <Currency>EUR</Currency>
        <Nationality>ES</Nationality>
        <Markets>
            <Market>SP</Market>
            <Market>EN</Market>
        </Markets>
        <RoomCandidates>
            <RoomCandidate id = "1">
                <Paxes>
                    <Pax age = "30" id = "1"/>
                    <Pax age = "30" id = "2"/>
                </Paxes>
            </RoomCandidate>
        </RoomCandidates>
    </AvailRQ>
~~~


### AvailRQ Description



| **Element**				| **Number**	| **Type**	| **Description**						|
| ------------------------------------- | ------------- | ------------- | ------------------------------------------------------------- |
| AvailRQ               		| 1            	|		| Root node.							|
| CancellationPolicies 			| 1     	| Boolean	| Indicates if you want to receive the cancellation policies in AvailRS, as long as the provider returns it in this call (see StaticConfiguration).	|
| OnRequest            			| 1     	| Boolean	| Indicates if you want to receive the onrequest options in AvailRS, as long as the provider returns it in this call (see StaticConfiguration).		|
| BusinessRules        			| 1            	|		| Indicates the business rules the client wants to apply in availability, as long as the provider returns it in this call (see StaticConfiguration).	|
| AvailDestinations/Destination		| 1..n         	|		| Contains the list of destinations filters (hotels or cities or zones or geocodes).	|
| @type           			| 1     	| String	| Destination type (HOT, CTY, ZON, GEO). Clarification: ZONs contains CTYs. ZONs are higher nodes and CTY are lower nodes.  |
| @code           			| 1     	| String	| Native destination code as returned by provider in *HotelList* or *AvailDestinationTree*.	|
| StartDate            			| 1     	| String	| 'Search from' date.						|
| EndDate              			| 1     	| String	| 'Search til' date.						|
| Currency             			| 0..1  	| String	| Currency requested, if supported by provider. If not, this value will be ignored.	|
| Nationality          			| 0..1  	| String	| Nationality of the guest (use ISO3166_1_alfa_2). This informations will be mandatory depending on the provider, as long as the provider returns it in this call (see StaticConfiguration).	|
| Markets              			| 0..1         	|		| List of Market requested.					|
| Markets/Market       			| 0..n  	| String	| The targeted zone/ country/ Point of sale.			|
| RoomCandidates/RoomCandidate 		| 1..n         	|		| Room required.						|
| @id             			| 1     	| Integer	| Id of the requested room (starting at 1).			|
| RoomCandidates/RoomCandidate /Paxes/Pax | 1..n        |		|  Pax required.  						|
| @age            			| 1     	| Integer	| Pax age.							|
| @id             			| 1     	| Integer	| Pax id (starts at 1).						|



### AvailRS Example


~~~xml
    <AvailRS xmlns:xsd = "http://www.w3.org/2001/XMLSchema" xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance">
      <Hotels>
        <Hotel code = "10" name = "LEO">
          <MealPlans>
            <MealPlan code = "D">
              <Options>
                <Option type = "Hotel" paymentType = "MerchantPay" status = "OK">
                  <Rooms>
                    <Room id = "4145" roomCandidateRefId = "1" code = "DBL#STAND" description = "Doble Standard" nonRefundable = "false" numberOfUnits = "5" >
                      <Price currency = "EUR" amount = "36.20" binding = "false" commission = "-1"/>
                      <Beds sharedBed = "false">
                        <Bed numberOfBeds = "1" type = "Doble"/>
                      </Beds>
                      <DailyPrices>
                        <DailyPrice effectiveDate = "28/01/2014" expireDate = "29/01/2014">
                          <Price
                            currency = "EUR"
                            amount = "36.20"
                            binding = "false"
                            commission = "-1"/>
                        </DailyPrice>
                      </DailyPrices>
                      <DailyRatePlans>
                        <DailyRatePlan
                            effectiveDate = "28/01/2014"
                            expireDate = "29/01/2014"
                            code = "XAD"/>
                      </DailyRatePlans>
                    </Room>
                  </Rooms>
                  <Price currency = "EUR" amount = "36.20" binding = "false" commission = "-1"/>
                  <Offers>
                    <Offer code = "EBI" name = "Early booking"/>
                  </Offers>
                </Option>
              </Options>
            </MealPlan>
            <MealPlan code = "M">
              <Options>
                <Option type = "Hotel" paymentType = "MerchantPay" status = "OK">
                  <Rooms>
                    <Room id = "4146" roomCandidateRefId = "1" code = "TWN#STAND" description = "Twin Standard" nonRefundable = "false" numberOfUnits = "5">
                      <Price currency = "EUR" amount = "42.90" binding = "false" commission = "-1"/>
                    <Beds sharedBed = "false">
                        <Bed numberOfBeds = "2" type = "Twin"/>
                    </Beds>
                    <DailyPrices>
                        <DailyPrice effectiveDate = "28/01/2014" expireDate = "29/01/2014">
                            <Price
                                currency = "EUR"
                                amount = "42.90"
                                binding = "false"
                                commission = "-1"/>
                        </DailyPrice>
                    </DailyPrices>
                    <DailyRatePlans>
                        <DailyRatePlan
                            effectiveDate = "28/01/2014"
                            expireDate = "29/01/2014"
                            code = "XAT"/>
                    </DailyRatePlans>
                    </Room>
                  </Rooms>
                  <Price currency = "EUR" amount = "42.90" binding = "false" commission = "-1"/>
                </Option>
              </Options>
              ...
            </MealPlan>
            <MealPlan code = "MP">
              <Options>
                <Option type = "HotelSkiPass" paymentType = "MerchantPay" status = "OK">
                  <Rooms>
                    <Room id = "4145" roomCandidateRefId = "1" code = "DBL#STAND" description = "Doble Standard" nonRefundable = "false">
                      <Price currency = "EUR" amount = "636.80" binding = "false" commission = "-1"/>
                    </Room>
                  </Rooms>
                  <Detail>
                    <POIs>
                      <POI code = "8A" Description = "Andorra">
                        <Services>
                          <Service type = "SkiPass" code = "F1" description = "Forfait" durationType = "Range" quantity = "0" unit = "Day">
                            <RangeDates startDate = "28/01/2014" endDate = "29/01/2014"/>
                          </Service>
                        </Services>
                      </POI>
                    </POIs>
                  </Detail>
                  <Price currency = "EUR" amount = "636.80" binding = "false" commission = "-1"/>
                  <Parameters>
                    <Parameter key = "sesion" value = "888de014"/>
                  </Parameters>
                </Option>
                <Option type = "HotelSkiPass" paymentType = "MerchantPay" status = "OK">
                  <Rooms>
                    <Room id = "4145" roomCandidateRefId = "1" code = "DBL#STAND" description = "Doble Standard" nonRefundable = "false">
                      <Price currency = "EUR" amount = "636.80" binding = "false" commission = "-1"/>
                    </Room>
                  </Rooms>
                  <Detail>
                    <POIs>
                      <POI code = "8A" Description = "Andorra">
                        <Services>
                          <Service type = "SkiPass" code = "F1" description = "Forfait" durationType = "libre" quantity = "5" unit = "Hour"></Service>
                        </Services>
                      </POI>
                    </POIs>
                  </Detail>
                  <Price currency = "EUR" amount = "636.80" binding = "false" commission = "-1"/>
                  <Parameters>
                    <Parameter key = "sesion" value = "888de014"/>
                  </Parameters>
                  <RateRules>
                    <Rules>
                      <Rule type = "NonRefundable"/>
                    </Rules>
                  </RateRules>
                </Option>
                <Option type = "HotelSkiPass" paymentType = "MerchantPay" status = "OK">
                  <Rooms>
                    <Room id = "4145" roomCandidateRefId = "1" code = "DBL#STAND" description = "Doble Standard" nonRefundable = "false">
                      <Price currency = "EUR" amount = "636.80" binding = "false" commission = "-1"/>
                    </Room>
                  </Rooms>
                  <Detail>
                    <POIs>
                      <POI code = "8A" Description = "Andorra">
                        <Services>
                          <Service type = "SkiPass" code = "F1" description = "Forfait" durationType = "libre" quantity = "2" unit = "Day"></Service>
                        </Services>
                      </POI>
                    </POIs>
                  </Detail>
                  <Price currency = "EUR" amount = "636.80" binding = "false" commission = "-1"/>
                  <Parameters>
                    <Parameter key = "sesion" value = "888de014"/>
                  </Parameters>
                  <CancelPenalties nonRefundable = "false">
                    <CancelPenalty>
                      <HoursBefore>24</HoursBefore>
                      <Penalty type = "Importe" currency = "EUR">20</Penalty>
                    </CancelPenalty>
                  </CancelPenalties>
                </Option>
              </Options>
            </MealPlan>
            ...
          </MealPlans>
        </Hotel>
        ...
      </Hotels>
    </AvailRS>
~~~


### Detailed description


**BusinessRules:**

BusinessRules uses *optionsQuota*, go to *Common-Elements* for more
information.

This tag will only be used for suppliers availability responses
returning a very large number of options, about 20.000+ in same
response.

Currently, the client can configure the following BusinessRules:

* *CheaperAmount*:

  The cheapest options will be returned without exceeding the
  *optionsQuota* limit.

* *RoomType*: 

  The options will be filtered by a limited combination of
  rooms types. First, we will group same room types so you will receive
  options with the same type/classificatory (For example:
  Standar-Standar-Standar-Standar, Junior-Junior-Junior-Junior...). Then
  we will combine the cheapest rooms with the remaining rooms, always
  checking for duplicates and without execeeding the *optionsQuota* limit.

  If the client sets BusinessRules value, then these will be applied
  when number of options returned exceeds *optionsQuota*. If the client
  does not set any BusinessRules values, then the *CheaperAmount*
  BusinessRule is applied by default.



### AvailRS Description



| **Element**				| **Number**	| **Type**	| **Description**						|
| ------------------------------------- | ------------- | ------------- | ------------------------------------------------------------- |
| AvailRS/Hotels/Hotel 			| 0..n 		| 		| Root node.							|
| @code 				| 1 		| String 	| Hotel code.							|
| @name 				| 0..1 		| String 	| Hotel name.							|
| MealPlans 				| 1 		| 		| Meal plans of this hotel.					|
| MealPlans/MealPlan 			| 1..n 		| 		| List of meal type classification.				|
| @code 				| 1 		| String 	| MealPlan code.						|
| MealPlans/MealPlan/Options 		| 1 		| 		| Options (list option).					|
| MealPlans/MealPlan /Options/Option 	| 1..n 		| 		| Detail of option.						|
| @type 				| 1 		| String 	| Indicates the type of option (only hotel, hotel with ski pass, hotel with entrance...).	|
| @paymentType 				| 1 		| String 	| Indicates the typology of payment (Merchant, Direct ...) .	|
| @status 				| 1 		| String 	| Status option (OK = available, RQ = on request).		|
| MealPlans/MealPlan/Options /Option/Parameters | 0..1 	| 		| Additional parameters that must be reported on the ValuationRQ. Parameters, if this option is required.	  |
| MealPlans/MealPlan/Options /Option/Parameters/Parameter | 0..n | 	| Additional parameter that requires integration.		|
| @key 					| 1 		| String 	| Contains the keyword/Id to identify a parameter.		|
| @value 				| 1 		| String 	| Contains the value of the parameter.				|
| MealPlans/MealPlan/Options /Option/CancelPenalties /CancelPenalty | 0..1|  | Listing cancellation penalties.				|
| MealPlans/MealPlan/Options /Option/CancelPenalties /CancelPenalty/HoursBefore| 1 | String | Number of hours prior to arrival day in which this Cancellation policy applies. | 
| MealPlans/MealPlan/Options /Option/CancelPenalties /CancelPenalty | 1..n| | Contains the value to apply.				|
| @type 				| 1 		| String 	| Type of penalty Possible values: "Noches" (nights), "Porcentaje" (percentage), "Importe" (price value).  |
| @currency 				| 1 		| String 	| Currency code.						|
| MealPlans/MealPlan/Options /Option/RateRules | 0..1 	| 		| Restrictions of this option.					|
| MealPlans/MealPlan/Options /Option/RateRules/Rules | 0..n | 		| Rules.							|
| MealPlans/MealPlan/Options /Option/RateRules/Rules /Rule | 1 | 	| Rule.								|
| @type 				| 1 		| String 	| Values that can take (NonRefundable, Older55, Package,...).	|
| MealPlans/MealPlan/Options /Option/Rooms | 1 		| 		| Rooms of this option (room list).				|
| MealPlans/MealPlan/Options /Option/Rooms/Room | 1..n 	| 		| Details of room.						|
| @id 					| 1 		| String 	| Identifier of the room.					|
| @roomCandidateRefId 			| 1 		| Integer 	| Identifier of room candidate.					|
| @code 				| 1 		| String 	| Room code.							|
| @description 				| 1 		| String 	| Room description.						|
| @nonRefundable 			| 0..1 		| String 	| Identifies if the room is refundable or not.			|
| @numberOfUnits 			| 0..1 		| Integer 	| Number of rooms available with the same type (see StaticConfiguration).	|
| MealPlans/MealPlan/Options /Option/Rooms/Room/Beds | 0..1 | 		| Detail of beds.						|
| @sharedBed 				| 0..1 		| Boolean 	| Specifies if the beds in the room are shared.			|
| MealPlans/MealPlan/Options /Option/Rooms/Room /Beds/Bed | 0..n | 	| Identifies types of beds.					|
| @numberOfBeds 			| 0..1 		| String 	| Indicates number of beds in the room.				|
| @type 				| 0..1 		| String 	| Indicates the type of bed.					|
| MealPlans/MealPlan/Options /Option/Rooms/Room /DailyPrices | 0..1 | 	| Specifies the daily price, as long as the provider returns it in this call (see StaticConfiguration).	| 
| MealPlans/MealPlan/Options /Option/Rooms/Room /DailyPrices/DailyPrice | 1..n | | Specifies the price for each day.			|
| @effectiveDate 			| 1 		| String 	| Start date in which the price becomes effective.		|
| @expireDate 				| 1 		| String 	| Expiry date of price.						|
| MealPlans/MealPlan/Options /Option/Rooms/Room /DailyPrices/DailyPrice /Price| 1 | | Day price.					|
| @currency 				| 1 		| String 	| Currency code.						|
| @amount 				| 1 		| Decimal 	| Day Amount.							|
| @binding 				| 1 		| Boolean 	| Identifies if is the price is binding (When true the sale price returned **must** not be less than the price informed. |
| @commission 				| 1 		| Decimal 	| Commission: -1 = not specified (will come indicated with the provider contract ), 0 = net price, X = % of the commission that applies to the amount. |
| MealPlans/MealPlan/Options /Option/Rooms/Room /DailyRatePlans | 0..1 | | Specifies the daily rate, as long as the provider returns it in this call (see StaticConfiguration).  |
| MealPlans/MealPlan/Options /Option/Rooms/Room /DailyRatePlans/DailyRatePlan | 1..n | | Specifies the rates for each day.		|
| @effectiveDate 			| 1 		| String 	| Start date in which the rate becomes effective.		|
| @expireDate 				| 1 		| String 	| End date in which the rate becomes expire.			|
| @code 				| 1 		| String 	| Indicates the provider's rate code. This code specifies the rate that applies to those days.	|
| MealPlans/MealPlan/Options /Option/Rooms/Room /Price | 1 | 		| Room price.							|
| @currency 				| 1 		| String 	| Currency code.						|
| @amount 				| 1 		| Decimal 	| Room Amount.							|
| @binding 				| 1 		| Boolean 	| Identifies if is the price is binding (When true the sale price returned **must** not be less than the price informed).|
| @commission 				| 1 		| Decimal 	| Commission ( -1 = not specified (will come indicated with the provider contract ), 0 = net price, X = % of the commission that applies to the amount.   |
| MealPlans/MealPLan/Options /Option/InfoTipoOpcion | 	| 		| Deprecated node.						|
| @TipoDuracion 			| 		| 		|								|
| @Cantidad 				| 		| 		|								|
| @Unidad 				| 		| 		|								|
| MealPlans/MealPlan/Options /Option/Detail/PDI | 	| 		|								|
| @Codigo 				| 		| 		|								|
| @Descripcion 				| 		| 		|								|
| MealPlans/MealPlan/Options /Option/InfoTipoOpcion /RangoFechas | | 	|								|
| @startDate 				| 		| 		|								|
| @endDate 				| 		| 		|								|
| MealPlans/MealPlan/Options /Option/Price | 1 		| 		| Option price ( it is the total price of option).		|
| @currency 				| 1 		| String 	| Currency code.						|
| @amount 				| 1 		| Decimal 	| Option Amount.						|
| @binding 				| 1 		| Boolean 	| Identifies if is the price is binding (When true the sale price returned **must** not be less than the price informed.|
| @commission 				| 1 		| Decimal 	| Commission ( -1 = not specified (will come indicated with the provider contract ), 0 = net price, X = % of the commission that applies to the amount.	|
| MealPlans/MealPlan/Options /Option/Detail | 0..1 	| 		| Detail of option (it is indicated if the option is different from the type\<\> Hotel).  |
| MealPlans/MealPlan/Options /Option/Detail/POIs | 1 	| 		| Points of interest.						|
| MealPlans/MealPlan/Options /Option/Detail/POIs/POI | 1..n | 		| Point of interest.						|
| @code 				| 1 		| String 	| POI code.							|
| @description 				| 1 		| String 	| POI description.						|
| MealPlans/MealPlan/Options /Option/Detail/POIs/POI /Services | 1 | 	| Services that contains this POI.				|
| MealPlans/MealPlan/Options /Option/Detail/POIs/POI	/Services/Service | 1..n | | Service detail.					|
| @type 				| 1 		| String 	| Service typification (SkiPass, Lessons, Meals, Equipment, Ticket, Transfers or Gala).	|
| @code 				| 1 		| String 	| Service code.							|
| @description 				| 1 		| String 	| Service description.						|
| @durationType 			| 1 		| String 	| Type of duration (Range= date range specified will come "RangeDates" element, Open= indicates a duration not restricted by date, quantity and typology of the elements are indicated in "quantity" and "unit").|
| @quantity 				| 1 		| Integer 	| Indicate the quantity of field in the element "unit".		|
| @unit 				| 0..1 		| String 	| Day or Hour.							|
| MealPlans/MealPlan/Options /Option/Detail/POIs/POI /Services/Service/RangeDates| 0..1 | | Service date range (Only specified if durationType=Range).	|
| @startDate 				| 1 		| String 	| Start date to service.					|
| @endDate 				| 1 		| String 	| End date to service.						|
| MealPlans/MealPlan/Options /Option/Remarks | 0..1 	| 		| List of remarks.						|
| MealPlans/MealPlan/Options /Option/Remarks/Remark | 1..n | 		| Remark.							|
| MealPlans/MealPlan/Options /Option/Offers | 0..1 	| 		| The provider returns in response which offer is applicable for each option.	|
| MealPlans/MealPlan/Options /Option/Offers/Offer | 1..n | 		| List of offers.						|
| @code 				| 1 		| String 	| Contains the code to identify a offer.			|
| @name 				| 1 		| String 	| Contains the name of the offer.				|



### Detailed description


**Price, binding price and commission:**

Every option has a price and every price indicates the currency, the
amount, if it is binding and the commission.

-   *Binding:*

If binding is set as true, then the client can't sell the product for a
lower price then the one set by the supplier. If it set as as false, the
client can sell the product for a lower price.

-   *Commission:*

   > -   Commission = 0: the price returned is a net price.
   > -   Commission = -1: the provider has not supplied the sale price
   >     nor the commission. This information is obtained by signing a
   >     contract with the provider.
   > -   Commission is greater than 0: X = % of the commission that is
   >     applied to the amount

*Below are 4 possible scenarios:*

~~~xml
    <Price currency = "EUR" amount = "200" binding = "false" commission = "-1"/>
~~~

We have no way of knowing if the price is PVP or a net price, given that
the commission is not sent to us via XML. The commission is established
by contract.

~~~xml
    <Price currency = "EUR" amount = "300" binding = "true" commission = "-1"/>
~~~

The price is PVP, the commission is not sent to us via XML. The
commission is established by contract.

~~~xml
    <Price currency = "EUR" amount = "150" binding = "true/false" commission = "20"/>
~~~

The price is PVP with a commission of 20%. The binding in this case can
be true or false.

~~~xml
    <Price currency = "EUR" amount = "100" binding = "false" commission = "0"/>
~~~

The price is net.



**Currency:**

The currency node indicates which currency you want to use in your
request.

This field will be sent to the supplier provided that the the supplier
allows for it in the request, otherwise it won't be sent.

If the provider allows for the field currency to be used, we can't
guarantee that the response will be in the currency you requested, as we
always work with the native code of the provider. For example if you
requested EUR but the provider only works with GBP, the provider will
return in GBP, and we will pass it on to you in GBP



**PAX ages:**

The range of what is considered an adult, infant or baby is particular
to each provider.

We don't have a standardization of the paxs ages, we adapt to what the
providers wants. For one provider a child age might range from 1 to 15
years old, for others, a 13 years old is considered an adult. We will
always use the provider´s definition. If the providers requires it, we
will convert the age of a pax to a pax type (for example, convert a 30
year old pax to an adult ) or send directly the age of the pax. This
depends on the provider's request.   



**Note:** *Once the age as been established for each pax then it must not be
modified for the rest of the petitions, like for example the valuation process.*   



**Cancellation policies:**

The cancellation policies or penalizations may be displayed in the
response, provided that the parameter <CancellationPolicies> is set as
true in the request and that the provider supplies this information in
the availability call.



**On Request:**

The on request option may be displayed in the response provided that the
parameter <OnRequest> is set as true in the request. In case that the
parameter <OnRequest> is set as false, the integration will filter
this option in AvailRS only if the supplier provides us this information
in the availability call.



**PaymentOptions:**

-   **MerchantPay:** The payment is managed by the provider.

-   **LaterPay:** The payment is managed by the hotel. The customer will
    use a credit-card as a guarantee for the hotel and the payment will
    be done at check in.
-   **CardBookinPay:** The payment is managed by the provider. The
    payment is effectuated at the time of booking.
-   **CardChekinPay:** The payment is managed by the provider. The
    payment is effectuated during check in at the hotel.



**Rate conditions:**

-   The extra fee for a **nonRefundable** cancellation is a 100% from
    the moment the reservation is created.
-   The provider can return options for pax: older than 55 years old,
    i.e. options that can only be sold to people who are 55 and older.
    In this case we will return the condition: rate 55 years old.
-   In the case of pax older than **60 years** and **65 years** the same
    process applies.
-   The rate **package** means that the product can't be sold separately
    from another product attached to it, such as a flight.
-   The rate **CanaryResident** is applicable to Canary Islands
    residents only.
-   The rate **BalearicResident** is applicable to Balearic Islands
    residents only.
-   The rate **largeFamily** is applied to large families and is
    determined by each provider.Check *remarks* for more details.
-   The rate **honeymoon** is applied to those who just got married and
    is determined by each provider. Check *remarks* for more details.



**Status options:**

The possible values of the status in the response is OK or RQ:

~~~xml
    <Option type = "Hotel" paymentType = "MerchantPay" status = "OK">
~~~

In the case that the client doesn't want to display the options in a
status RQ, we can filter the options given that the provider typifies
this status when the AvailRQ specifies the <OnRequest> tag. In the
case the provider doesn't facilitates this information, wich will be
informed into the StaticConfiguration call, then this will have to be
treated on a commercial level.



**Room quantity:**

~~~xml
	<RoomCandidate "cantidad=“1” id=“1"\>
~~~

The quantity ( or "cantidad" ) has to be one. This quantity is
deprecated.

-   **HoursBefore:** Number of hours which are in between the
    reservation date and the checking date.
-   **Type:** There are three values that can be inside types:

> -   *Noches:* Which will indicate the number of nights which will be
>     penalized.
> -   *Porcentaje:* Which indicates the percentage to pay based on the
>     option price.
> -   *Importe:* That indicates the exact amount that it is necessary to
>     pay.

-   **Currency:** Money currency of the import.



**POI cases explanation:**

Case 1:

~~~xml
    <POIs>
      <POI code = "8A" Description = "Andorra">
        <Services>
          <Service type = "SkiPass" code = "F1"
          description = "Forfait" durationType = "Range"
          quantity = "0" unit = "Day">
            <RangeDates startDate = "28/01/2014"
            endDate = "29/01/2014"/>
          </Service>
        </Services>
      </POI>
    </POIs>
~~~

Specifying the quantity makes no difference and it won't send anything
because it already specifies the start and end dates.



Case 2:

~~~xml
    <POIs>
      <POI code = "8A" Description = "Andorra">
        <Services>
          <Service type = "SkiPass" code = "F1"
          description = "Forfait" durationType = "libre"
          quantity = "5" unit = "Hour">
          </Service>
        </Services>
      </POI>
    </POIs>
~~~

In this case, quantity is applicable in all the stay, i.e., the client
can enjoy until 5 hours of forfait in any day of the stay.



Case 3:

~~~xml
    <POIs>
      <POI code = "8A" Description = "Andorra">
        <Services>
          <Service type = "SkiPass" code = "F1"
          description = "Forfait" durationType = "libre"
          quantity = "2" unit = "Day">
          </Service>
        </Services>
      </POI>
    </POIs>
~~~

In this case, quantity is applicable in all the stay, i.e., the client
can enjoy until 2 days of forfait in between the check in and the check
out of the stay of the reservation/option.



**Note:** *Keep the parameters in the avail response to include them in the valuation request.*

~~~xml
    <Parameters>
       <Parameter key = "sesion" value = "888de014"/>
    </Parameters>
~~~


