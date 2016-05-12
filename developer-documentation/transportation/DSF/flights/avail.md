---
title: Avail
keywords: transportation, data structure, flights, avail
sidebar: mydoc_sidebar
permalink: /developer-documentation/transportation/DSF/flights/avail
---

|

Method Goals
============

This method aims to return all the available options for a given date
and itinerary. It does not filter different classes, times or fares. It
will always return all of the results returned by the provider.

|

Request Format
==============

The common part of an availability request is very straight forward. It
only requires the destination/s, the travelling dates, the paxes and the
indication of the trip type: one way trip or a round trip.

|

Response Format
===============

The response format will always be delivered in the node Transportation,
which will be organized by two main nodes:

-   Segments:

A list with all of the Segments including details, returned by the
supplier, such as dates, number, etc.

|

-   Fares:

A list with all of the prices returned for each Segment in the above
list. Each Fare has a referenced SegmentReference inside the node
Option, to identify the Segment. A Fare will have one or more Segments
associated and every Segment will refer to at least one Option.

There will always be one PaxBreakdown per passenger type.

The price returned is "all inclusive". All fares, taxes and discounts
are already included in the total price.

|

Remarks
=======

This method **must** be called **before** the Valuation method.

The maximum time that our systems permits before closing the connexion
is of **25000** milliseconds.

|

AvailabilityRQ Example
======================

:

    <AvailabilityRQ travelType = "RT">
        <timeoutMilliseconds>999900</timeoutMilliseconds>
        <source>
            <agencyCode>logitravel</agencyCode>
            <languageCode>es</languageCode>
        </source>
        <filterAuditData/>
        <Configuration>
            <Credentials user="XXX"/>
            <Attributes>
                <Attribute key="test" value="true"/>
                <Attribute key="AgencyName" value="XXX"/>
            </Attributes>
        </Configuration>
        <ClientConfiguration currencyCode="EUR"/>
        <Journeys>
            <Journey id = "0" departureDate = "23/03/2014" departureTime = "">
                <OriginLoc code = "XXX" cityCode = "false"/>
                <DestinationLoc code = "YYY" cityCode = "false"/>
            </Journey>
            <Journey id = "1" departureDate = "25/03/2014" departureTime = "">
                <OriginLoc code = "XXX" cityCode = "false"/>
                <DestinationLoc code = "YYY" cityCode = "false"/>
            </Journey>
        </Journeys>
        <Passengers>
            <Passenger id = "0" age = "30">
                <Bonuses resident = "N" largeFamily = "N"/>
            </Passenger>
        </Passengers>        
        <Preferences cabinClass="N">
            <ConnexionCompanies>
                <ConnexionCompany carrier="IB" mode="INCLUDED" />
            </ConnexionCompanies>
        </Preferences>
    </AvailabilityRQ> 

|

AvailabilityRQ Description
==========================

  -------------------------------------------------------------------------
  Element                Num Typ Description
                         ber e   
  ---------------------- --- --- ------------------------------------------
  AvailabilityRQ         1       Root node.

  <*@travelType>\*       1   Str Indicates the travel type: one way (OW),
                             ing round trip (RT), open jaw (OJ) and circle
                                 trip.

  Journeys               1       Contains a list of Journeys.

  Journeys/Journey       1..     Contains the information about the
                         n       requested Journey in the availability.

  <*@id>\*               1   Int Unique identifier of the Journey.
                             ege 
                             r   

  <*@departureDate>\*    1   Str Departure date.
                             ing 

  <*@departureTime>\*    1   Str Departure time.
                             ing 

  Journeys/Journey/Origi 1       Origin location.
  nLoc                           

  <*@code>\*             1   Str Location code.
                             ing 

  <*@cityCode>\*         1   Boo If true, the field code indicates a city
                             lea code, if false, it will indicate an
                             n   airport code.

  Journeys/Journey/Desti 1       Destination location.
  nationLoc                      

  <*@code>\*             1   Str Location code.
                             ing 

  <*@cityCode>\*         1   Boo If true, the field code indicates a city
                             lea code, if false, it will indicate an
                             n   airport code.

  Passengers             1       Contains a list of Passengers.

  Passengers/Passenger   1..     Contains information of the Passenger
                         n       

  <*@id>\*               1   Int Unique identifier of the Passenger.
                             ege 
                             r   

  <*@age>\*              1   Int Age of the Passenger.
                             ege 
                             r   

  Passengers/Passenger/B 0..     Possible discount or bonuses.
  onuses                 1       

  <*@resident>\*         1   Str Resident discount.
                             ing 

  <*@largeFamily>\*      1   Str Family discount.
                             ing 

  Preferences            1       Availability Preferences

  <*@cabinClass>\*       1   Str Preferred cabin class. N don't aply
                             ing (default), F first, C Business, Y Economy

  ConnexionCompanies     1       List of preferred companies

  ConnexionCompany       1       Preferred company

  <*@carrier>\*          1   Str Airline code
                             ing 

  <*@mode>\*             1   Str Mode. INCLUDED include preferred company
                             ing and exclude all the others. EXCLUDED
                                 exclude only preferred company.
  -------------------------------------------------------------------------

|

AvailabilityRS Example
======================

:

    <AvailabilityRS>
        <Transportation>
            <Segments>
                <Segment  id = "0" transportationId = "0B104" transportationType = "A" operatingCarrier = "0B" marketingCarrier = "0B" departureTerminal = "T1" arrivalTerminal = "T2" departureDate = "2014-03-23T10:20:00" arrivalDate = "2014-03-23T15:15:00" segmentDuration = "0" planeType = "734" segmentStatus = "HK" hasTechnicalStop = "false">
                    <OriginLoc type = "A" code = "MAD" cityCode = "false"/>
                    <DestinationLoc type = "A" code = "OTP" cityCode = "false"/>
                    <TechnicalStops totalTechnicalStops="1">
                        <TechnicalStop location="BCN" stopDate="2014-10-21T08:20:00" departureDate="2014-10-21T08:30:00"/>
                    </TechnicalStops>
                </Segment>
                <Segment id = "1" transportationId = "0B103" transportationType = "A" operatingCarrier = "0B" marketingCarrier = "0B" departureTerminal = "T1" arrivalTerminal = "T2" departureDate = "2014-03-25T15:30:00" arrivalDate = "2014-03-25T18:35:00" segmentDuration = "0" planeType = "734" segmentStatus = "HK" hasTechnicalStop = "false">
                    <OriginLoc type = "A" code = "OTP" cityCode = "false"/>
                    <DestinationLoc type = "A" code = "MAD" cityCode = "false"/>
                </Segment>
            </Segments>            
            <Fares>
                <Fare id = "0" providerCode = "BLU" fareType = "OW" familyFare="FAMILY1">
                    <Options>
                        <Option id ="0" availJourneyRef = "0" numStopOver = "0" carrier = "UX">
                            <SegmentReferences>
                                <SegmentReference segmentRef = "0">
                                    <SegmentClasses>
                                        <SegmentClass cabinClass = "Y" class = "K" paxRef = "0" fareBasis = "WEB14" fareType = "PUB" avail="9" />
                                    </SegmentClasses>
                                    <ReservationTokens>
                                        <Attribute key = "FareSequence" value = "88"/>
                                        <Attribute key = "RuleNumber" value = "0001"/>
                                    </ReservationTokens>
                                </SegmentReference>
                            </SegmentReferences>
                        </Option>
                    </Options>
                    <AmountBreakdown currency = "EUR" totalAmount = "109.9000" notCommissionableAmount = "0" commission = "-1">
                        <ChargeBreakdowns/>
                        <PaxBreakdowns>
                            <PaxBreakdown paxType = "ADT" amount = "109.9000" taxes = "0" tasaDU = "0"/>
                        </PaxBreakdowns>
                    </AmountBreakdown>
                    <PaxConfigurations>
                        <PaxConfiguration id = "0" paxRef = "0" age = "30" paxType = "ADT">
                            <AppliedBonuses resident = "N" largeFamily = "N" discountCard = "N"/>
                        </PaxConfiguration>
                    </PaxConfigurations>
                    <HasObFees>false</HasObFees>
                </Fare>
            </Fares>     
        </Transportation>
    </AvailabilityRS>

|

AvailabilityRS Description
==========================

  -------------------------------------------------------------------------
  Element                      Nu Typ Description
                               mb e   
                               er     
  ---------------------------- -- --- -------------------------------------
  AvailabilityRS               1      Root node.

  Transportation               1      Contains all of the Segments and
                                      Fares.

  <*@totalFares>\*             1  Int Total number of Fares.
                                  ege 
                                  r   

  Transportation/Segments      1      Contains a list of the Segments.

  Transportation/Segments/Segm 1.     Contains the information of the
  ent                          .n     segment.

  <*@id>\*                     1  Int Unique identifier of the segment.
                                  ege 
                                  r   

  <*@transportationId>\*       1  Str Unique Id of the transportation.
                                  ing 

  <*@transportationType>\*     1  Str Transport type: A ( Flight ), T (
                                  ing Train ), B ( Bus ) & F ( Ferry ).

  <*@operatingCarrier>\*       1  Str Company which operates the
                                  ing transportation.

  <*@marketingCarrier>\*       1  Str Company which commercializes the
                                  ing transportation.

  <*@departureTerminal>\*      1  Str Departure terminal.
                                  ing 

  <*@arrivalTerminal>\*        1  Str Arrival terminal.
                                  ing 

  <*@departureDate>\*          1  Dat Departure date.
                                  e   

  <*@arrivalDate>\*            1  Dat Arrival date.
                                  e   

  <*@segmentDuration>\*        1  Int Transport duration ( in minutes ).
                                  ege 
                                  r   

  <*@planeType>\*              1  Str Plane type. Flights parameter.
                                  ing 

  <*@maxCheckinDate>\*         1  Str Maximum date to make the check-in.
                                  ing 

  <*@segmentStatus>\*          1  Str Segment status: HK (OK), TK (Change
                                  ing of programming), UC (Unconfirmed),
                                      UN( Unable), NO (No action taken) &
                                      UD (Undefined)

  <*@hasTechnicalStop>\*       1  Boo If true, the segment has a technical
                                  lea stop.
                                  n   

  <*@electronicTicket>\*       1  Boo If true, the segment uses a
                                  lea electronic ticket.
                                  n   

  <*@secureFlight>\*           0. Boo If true, the provider requires extra
                               .1 lea information of the passengers.
                                  n   Flights parameter.

  Transportation/Segments/Segm 1      Origin location.
  ent/OriginLoc                       

  <*@type>\*                   1  Str Type of station of the location
                                  ing indicated with A ( AirPort ), T (
                                      Train Station ) & P ( Port ).

  <*@code>\*                   1  Str Location code.
                                  ing 

  <*@cityCode>\*               1  Boo If true, the field code indicates a
                                  lea city code, if false, it will indicate
                                  n   an airport code.

  Transportation/Segments/Segm 1      Destination location.
  ent/DestinationLoc                  

  <*@type>\*                   1  Str Type of station of the location
                                  ing indicated with A ( AirPort ), T (
                                      Train Station ) & P ( Port ).

  <*@code>\*                   1  Str Location code.
                                  ing 

  <*@cityCode>\*               1  Boo If true, the field code indicates a
                                  lea city code, if false, it will indicate
                                  n   an airport code.

  Transportation/Segments/Segm 0.     Contains a list of TechnicalStops.
  ent/TechnicalStops           .1     

  <*@totalTechnicalStops>\*    1  Int Total number of TechnicalStops.
                                  ege 
                                  r   

  Transportation/Segments/Segm 1.     Contains the details of the
  ent/TechnicalStops/Technical .n     TechnicalStop.
  Stop                                

  <*@location>\*               1  Str TechnicalStop location.
                                  ing 

  <*@stopDate>\*               1  Dat Approx. stop date and time.
                                  e   

  <*@departureDate>\*          1  Dat Approx. departure date and time.
                                  e   

  Fares                        1      Contains a list of Fares.

  Fares/Fare                   1.     Contains details of Fare.
                               .n     

  <*@id>\*                     1  Int Unique identifier of the Fare.
                                  ege 
                                  r   

  <*@providerCode>\*           1  Str Provider code.
                                  ing 

  <*@fareType>\*               1  Str Fare type: OW ( one way ), RT ( round
                                  ing trip ), OJ ( Open jaw ) & CT ( Circle
                                      trip ).

  <*@familyFare>\*             0. Str Optional family fare ( the same name
                               .1 ing of the petition ). Flights parameter.

  Fares/Fare/Options           1      Contains a list of Fare Options.

  Fares/Fare/Options/Option    1.     Contains details of the Fare Options.
                               .n     

  <*@id>\*                     1  Int Deprecated attribute.
                                  ege 
                                  r   

  <*@availJourneyRef>\*        1  Int Reference number of the availability
                                  ege Journey.
                                  r   

  <*@numStopOver>\*            1  Int Number of StopOvers. If -1, then we
                                  ege cannot know how many StopOvers via
                                  r   XML.

  <*@carrier>\*                1  Str Validating carrier.
                                  ing 

  Fares/Fare/Options/Option/Se 1      Contains a list of SegmentReferences.
  gmentReferences                     

  Fares/Fare/Options/Option/Se 1.     Contains details of the
  gmentReferences/SegmentRefer .n     SegmentReference of each option.
  ence                                

  <*@segmentRef>\*             1  Int Reference of the Segment.
                                  ege 
                                  r   

  Fares/Fare/Options/Option/Se 1      Contains a list of SegmentClasses.
  gmentReferences/SegmentRefer        
  ence/SegmentClasses                 

  Fares/Fare/Options/Option/Se 1      Contains details of the SegmentClass.
  gmentReferences/SegmentRefer ..     
  ence/SegmentClasses/SegmentC n      
  lass                                

  <*@cabinClass>\*             1  Str Cabin class of the seat: N (Not
                                  ing specified), Y (Tourist), C
                                      (Business), F (First), CA (Cabin,
                                      only for ferries), YP (Tourist Plus)

  <*@class>\*                  1  Str Fare class.
                                  ing 

  <*@paxRef>\*                 1  Int Passenger reference.
                                  ege 
                                  r   

  <*@fareBasis>\*              1  Str Identifier of the fare.
                                  ing 

  <*@fareType>\*               1  Str Fare type: PUB ( Public ), PRI (
                                  ing Private ), NEGO ( Negotiated ) and
                                      CORP ( Corporate ).

  <*@avail>\*                  1  Int Available seats remaining for this
                                  ege class (In flights, the maximum is 9)
                                  r   

  Fares/Fare/Options/Option/Se 0.     Specific attribute used for each
  gmentReferences/SegmentRefer .1     provider.
  ence/ReservationTokens              

  Fares/Fare/Options/Option/Se 0.     Type of attribute.
  gmentReferences/SegmentRefer .n     
  ence/ReservationTokens/Attri        
  bute                                

  <*@key>\*                    1  Str Contains the keyword/ Id to identify
                                  ing a parameter.

  <*@value>\*                  1  Str Contains the value of the parameter.
                                  ing 

  Fares/Fare/Options/Option/Ba 0.     Contains a list of BaggageTypes.
  ggageTypes                   .1     

  Fares/Fare/Options/Option/Ba 1.     Contains details of BaggageType.
  ggageTypes/BaggageType       .n     

  Fares/Fare/Options/Option/Ba 1      Specific attribute used for each
  ggageTypes/BaggageType/Bagga        provider.
  ge                                  

  <*@checkingType>\*           1  Str Specifies the checkin type: OnLine
                                  ing and Airport.

  <*@appliesSegments>\*        1  Str Type applied to the segment:
                                  ing Departure and Return.

  <*@id>\*                     1  Str Unique identifier of the Baggage.
                                  ing 

  <*@type>\*                   1  Str Type of baggage: Bag, Bike,
                                  ing Wheelchair, Skis and BabyTrolley.

  <*@quantity>\*               1  Int Baggage quantity
                                  ege 
                                  r   

  <*@maxWeightPerUnit>\*       1  Int Maximum weight of the baggage.
                                  ege 
                                  r   

  <*@maxTotalWeight>\*         1  Int Maximum weight of ALL the baggage.
                                  ege 
                                  r   

  <*@paymentInAirpot>\*        1  Boo Determines whether the pay is in
                                  lea station.
                                  n   

  <*@code>\*                   1  Str Code of the Baggage.
                                  ing 

  <*@carrier>\*                1  Str Carrier.
                                  ing 

  <*@needToken>\*              1  Boo Reserve token mandatory.
                                  lea 
                                  n   

  Fares/Fare/AmountBreakdown   1      Breakdown of the fare amount.

  <*@currency>\*               1  Str Currency code of the fare.
                                  ing 

  <*@totalAmount>\*            1  Dec Total amount. with taxes and other
                                  ima charges included.
                                  l   

  <*@notCommissionableAmount>\ 1  Dec Total amount that can not be
  *                               ima commissioned.
                                  l   

  <*@commission>\*             1  Dec Commission.
                                  ima 
                                  l   

  Fares/Fare/AmountBreakdown/C 0.     Contains a list of breakdown amounts
  hargeBreakdowns              .1     ( taxes, mandatory charges.. ).

  Fares/Fare/AmountBreakdown/C 1.     Contains details of the
  hargeBreakdowns/ChargeBreakd .n     BreakdownAmount.
  own                                 

  <*@type>\*                   1  Str Charge type.
                                  ing 

  <*@amount>\*                 1      Charge amount.

  Fares/Fare/AmountBreakdown/C 0.     Contains a list of breakdown amounts
  hargeBreakdowns/ChargeBreakd .1     ( taxes, mandatory charges.. ).
  own/Concept                         

  <*@id>\*                     1  Str Indicates if the conditions are of
                                  ing one way ( with a 0 ) or round trip (
                                      with a 1 ). Ferries parameter.

  <*@language>\*               1  Str Language.
                                  ing 

  Fares/Fare/AmountBreakdown/C 1  Str Remarks.
  hargeBreakDowns/ChargeBreakd    ing 
  own/Concept/Text                    

  Fares/Fare/AmountBreakdown/P 0.     Contains a list of breakdown amounts
  axBreakdown                  .1     for each passenger ( ADT amount, etc.
                                      ).

  Fares/Fare/AmountBreakdown/P 0.     Contains details of breakdown amounts
  axBreakdowns/PaxBreakdown    .n     for each passenger.

  <*@paxType>\*                1  Str Passenger type: ADT ( Adult ), CHD (
                                  ing Child ) & INF ( Infant ).

  <*@amount>\*                 1  Dec Total amount, with taxes included,
                                  ima associated to the passenger.
                                  l   

  <*@taxes>\*                  1  Int If they exist, taxes are applied for
                                  ege this passenger type.
                                  r   

  <*@tasaDU>\*                 1  Int Deprecated
                                  ege 
                                  r   

  Fares/Fare/PaxConfigurations 1      Contains a list of PaxConfiguration.

  Fares/Fare/PaxConfigurations 1.     Contains details of PaxConfiguration.
  /PaxConfiguration            .n     

  <*@id>\*                     1  Int Unique identifier of the
                                  ege PaxConfiguration.
                                  r   

  <*@paxRef>\*                 1  Int Reference to the passenger Id from
                                  ege the request.
                                  r   

  <*@age>\*                    1  Int Age of the passenger.
                                  ege 
                                  r   

  <*@paxType>\*                1  Str Passenger type based on the age of
                                  ing the passenger: ADT (Adult), CHD
                                      (Child), INF (Infant), YOU (Young)
                                      and SEN (Senior).

  Fares/Fare/PaxConfigurations 0.     Applied discounts.
  /PaxConfiguration/AppliedBon .1     
  uses                                

  <*@resident>\*               1  Str Resident discount type: N(None),
                                  ing BP(Balearic Islands resident flying
                                      to mainland), BI(Balearic Islands
                                      resident flying to another balearic
                                      island), DC(Canarian Islands resident
                                      flying to another Canarian Island),
                                      RC(Canarian Islands resident flying
                                      to mainland),RM(Ceuta/Melilla
                                      resident), STR(Italian resident
                                      discount), ELB(Italian resident
                                      Elba), SDG(Italian resident
                                      Sardegna), SCL(Italian resident
                                      Sicily)

  <*@largeFamily>\*            1  Str Family discount type: N(None),
                                  ing F1(Large family), F2 (Special large
                                      family).

  <*@discountCard>\*           1  Str Discount card type (for more details,
                                  ing see information below).

  Fares/Fare/PaxConfigurations 0.     Contains a list of PaxTypeCodes.
  /PaxConfiguration/AppliedBon .1     
  uses/PaxTypeCodes                   

  Fares/Fare/PaxConfigurations 0.     Contains details of the PTC.
  /PaxConfiguration/AppliedBon .n     
  uses/PaxTypeCodes/PaxTypeCod        
  e                                   

  <*@code>\*                   1  Str String with the PTC code.
                                  ing 

  Fares/Fare/HasObFees         1  Boo If true then there is an extra fee
                                  lea for using credit card.
                                  n   
  -------------------------------------------------------------------------

|

Detailed description
====================

**Total amount breakdown:**

The totalAmount from AmountBreakdown can be calculated by simply adding
the prices of each amount attribute from every PaxBreakdown.

Please note, that the amount as already had in consideration the taxes,
therefore, if the total price marks a 100€, and the taxes are 10€, then
the base price is 90€, like so:

>   Pax Breakdown                               
>   ---------------------- -------------------- -----------------
>   Adult                  Amount: 100€         tax: 10€
>
Total amount: 100€ Tax: 10€ Pax amount: 100€ - 10€ = 90€

|

**How to calculate a breakdown:**

Lets say for example we want to calculate the breakdown of the paxes,
then the amount will be the sum of all of the paxes price multiplied by
the number paxes.

For example, if the prices for each pax type are:

>   Paxes breakdown:                             
>   ----------------------- -------------------- -----------------
>   Adult                   Amount: 100€         tax: 10€
>   Child                   Amount: 50€          tax: 10€
>   Infant                  Amount: 10€          tax: 10€
>
And we want to do a booking for two adults, two kids and one baby, the
configuration of the paxes will be:

>   Paxes configuration:                        
>   ---------------------------- -------------- -------------------
>   Adult                        Attribute      Bonus
>   Adult                        Attribute      Bonus
>   Child                        Attribute      Bonus
>   Child                        Attribute      Bonus
>   Infant                       Attribute      Bonus
>
Therefore the total price will be:

>   ------------------------------------------------------------------------
>   Amount       
>   breakdown    
>   ------------ -----------------------------------------------------------
>   Total        Amount: (DesgloseADT \* numADT) + (DesgloseCHD \* numCHD) +
>                (DesgloseINF \* numINF) = **310€**
>   ------------------------------------------------------------------------
>
|
