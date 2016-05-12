---
title: RetrieveReservation
keywords: transportation, data structure, ferries, retrieve reservation
sidebar: mydoc_sidebar
permalink: /developer-documentation/transportation/DSF/ferries/retrieveReservation
---

|

Method Goals
============

This method aims to retrieve a booking with its full details.

|

Request Format
==============

The request requires the booking code or locator.

|

Response Format
===============

The response contains the details of a booking.

|

RetrieveReservationRQ Example
=============================

:

    <RetrieveReservationRQ xmlns:xsd = "http://www.w3.org/2001/XMLSchema" xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance">
        <Configuration/>
        <ClientConfiguration/>
        <Locator>BFRFKVM</Locator>
    </RetrieveReservationRQ>

|

RetrieveReservationRQ Description
=================================

  ------------------------------------------------------------------------
  Element                        Nu Ty Description
                                 mb pe 
                                 er    
  ------------------------------ -- -- -----------------------------------
  RetrieveReservationRQ          1     Root node.

  Locator                        1  St Locator.
                                    ri 
                                    ng 
  ------------------------------------------------------------------------

|

RetrieveReservationRS Example
=============================

:

    <RetrieveReservationRS xmlns:xsd = "http://www.w3.org/2001/XMLSchema" xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance">
    <ResponseStatus tripType = "IDA" petitionType = "OW" status = "ok"/>
    <Passengers>
        <Passenger
            id = "0"
            passengerType = "MR"
            name = "TestName"
            surname = "TestSurname"
            birthDate = "1985-08-19T12:11:38.577517+02:00"
            documentType = "NATIONAL_ID"
            documentId = "44183932N"
            documentExpiration = "2015-08-19T12:15:33.503954+02:00"
            documentExpedition = "0001-01-01T00:00:00"
            nationality = "ESP"
            gender = "72">
            <PaxBonusDetails>
                <AppliedBonuses resident = "N" largeFamily = "N" discountCard = "N"/>
                <ResidentCityCode>070146</ResidentCityCode>
                <LargeFamilyId/>
                <LargeFamilyCityCode/>
                <ResidentCertificateId>1234567890</ResidentCertificateId>
            </PaxBonusDetails>
        </Passenger>
    </Passengers>
    <Segments>
        <Segment id = "0">
            <SegmentInfo
                id = "1"
                transportationId = "BJ1#VISEMAR ONE#FERRY"
                transportationType = "F"
                operatingCarrier = "BAL"
                marketingCarrier = "BAL"
                departureTerminal = "PAL"
                arrivalTerminal = "VAL"
                departureDate = "2015-08-27T11:30:00"
                arrivalDate = "2015-08-27T19:30:00"
                transportationName = "VISEMAR ONE"
                transportationCode = "BJ1"
                segmentStatus = "HK"
                tieneParadaTecnica = "false">
                <OriginLoc type = "P" code = "PAL" citycode = "false"/>
                <DestinationLoc type = "P" code = "VAL" citycode = "false"/>
            </SegmentInfo>
            <SegmentClasses>
                <SegmentClass cabinClass = "N" class = "CAFETERIA" paxRef = "0" fareType = "PUB">
                    <CancellationPolicies>
                        <CancellationPolicy amount = "0" currency = "EUR" amountType = "PERCENTUAL" fromDate = "2015-08-19T10:16:00" refundable = "true"/>
                        <CancellationPolicy amount = "10" currency = "EUR" amountType = "PERCENTUAL" fromDate = "2015-08-20T11:30:00" refundable = "true"/>
                        <CancellationPolicy amount = "20" currency = "EUR" amountType = "PERCENTUAL" fromDate = "2015-08-25T11:30:00" refundable = "true"/>
                        <CancellationPolicy amount = "100" currency = "EUR" amountType = "PERCENTUAL" fromDate = "2015-08-27T11:30:00" refundable = "true"/>
                    </CancellationPolicies>
                    <Modifiable modifiable = "true" amount = "0" currency = "EUR" amountType = "AMOUNT">
                        <Description>Admite cambios sin cargos</Description>
                    </Modifiable>
                </SegmentClass>
            </SegmentClasses>
        </Segment>
        <Segment id = "1">
            <SegmentInfo
                id = "2"
                transportationId = "BJ1#VISEMAR ONE#FERRY"
                transportationType = "F"
                operatingCarrier = "BAL"
                marketingCarrier = "BAL"
                departureTerminal = "VAL"
                arrivalTerminal = "PAL"
                departureDate = "2015-09-04T22:15:00"
                arrivalDate = "2015-09-05T06:00:00"
                transportationName = "VISEMAR ONE"
                transportationCode = "BJ1"
                segmentStatus = "HK"
                tieneParadaTecnica = "false">
                <OriginLoc type = "P" code = "VAL" citycode = "false"/>
                <DestinationLoc type = "P" code = "PAL" citycode = "false"/>
            </SegmentInfo>
            <SegmentClasses>
                <SegmentClass cabinClass = "N" class = "CAFETERIA" paxRef = "0" fareType = "PUB">
                    <CancellationPolicies>
                        <CancellationPolicy amount = "0" currency = "EUR" amountType = "PERCENTUAL" fromDate = "2015-08-19T10:16:00" refundable = "true"/>
                        <CancellationPolicy amount = "10" currency = "EUR" amountType = "PERCENTUAL" fromDate = "2015-08-28T22:15:00" refundable = "true"/>
                        <CancellationPolicy amount = "20" currency = "EUR" amountType = "PERCENTUAL" fromDate = "2015-09-02T22:15:00" refundable = "true"/>
                        <CancellationPolicy amount = "100" currency = "EUR" amountType = "PERCENTUAL" fromDate = "2015-09-04T22:15:00" refundable = "true"/>
                    </CancellationPolicies>
                    <Modifiable modifiable = "true" amount = "0" currency = "EUR" amountType = "AMOUNT">
                        <Description>Admite cambios sin cargos</Description>
                    </Modifiable>
                </SegmentClass>
            </SegmentClasses>
            <TokensReserva/>
        </Segment>
    </Segments>
    <Tickets>
        <Ticket id = "1" ticketNum = "030-5035415825" paxName = "" cancelled = "0" joined = "0" seatType = "UNKNOWN" type = "eTicket" status = "Confirmed"/>
        <retrieveStatus>true</retrieveStatus>
    </Tickets>
    <Itinerary/>
    <Itineraries>
        <Itinerary id = "0">
            <Conditions>
                <Condition id = "0" language = "ES">
                    <Text>CAFETERIA#CAFETERIA##RTN#TARIFA IDA Y VUELTA#F0-TRAYECTO SIN RESTRICCIONES#F0#2.09</Text>
                </Condition>
                <Condition id = "1" language = "ES">
                    <Text>CAFETERIA#CAFETERIA##RTN#TARIFA IDA Y VUELTA#F0-TRAYECTO SIN RESTRICCIONES#F0#1.87</Text>
                </Condition>
            </Conditions>
            <Journeys>
                <Journey id = "0" Duracion = "0">
                    <Segments>
                        <Segment id = "0">
                            <SegmentInfo
                                id = "1"
                                transportationId = "BJ1#VISEMAR ONE#FERRY"
                                transportationType = "F"
                                operatingCarrier = "BAL"
                                marketingCarrier = "BAL"
                                departureTerminal = "PAL"
                                arrivalTerminal = "VAL"
                                departureDate = "2015-08-27T11:30:00"
                                arrivalDate = "2015-08-27T19:30:00"
                                transportationName = "VISEMAR ONE"
                                transportationCode = "BJ1"
                                segmentStatus = "HK"
                                tieneParadaTecnica = "false">
                                <OriginLoc type = "P" code = "PAL" citycode = "false"/>
                                <DestinationLoc type = "P" code = "VAL" citycode = "false"/>
                            </SegmentInfo>
                            <SegmentClasses>
                                <SegmentClass cabinClass = "N" class = "CAFETERIA" paxRef = "0" fareType = "PUB">
                                    <CancellationPolicies>
                                        <CancellationPolicy amount = "0" currency = "EUR" amountType = "PERCENTUAL" fromDate = "2015-08-19T10:16:00" refundable = "true"/>
                                        <CancellationPolicy amount = "10" currency = "EUR" amountType = "PERCENTUAL" fromDate = "2015-08-20T11:30:00" refundable = "true"/>
                                        <CancellationPolicy amount = "20" currency = "EUR" amountType = "PERCENTUAL" fromDate = "2015-08-25T11:30:00" refundable = "true"/>
                                        <CancellationPolicy amount = "100" currency = "EUR" amountType = "PERCENTUAL" fromDate = "2015-08-27T11:30:00" refundable = "true"/>
                                    </CancellationPolicies>
                                    <Modifiable modifiable = "true" amount = "0" currency = "EUR" amountType = "AMOUNT">
                                        <Description>Admite cambios sin cargos</Description>
                                    </Modifiable>
                                </SegmentClass>
                            </SegmentClasses>
                        </Segment>
                    </Segments>
                </Journey>
                <Journey id = "0" Duracion = "0">
                    <Segments>
                        <Segment id = "0">
                            <SegmentInfo
                                id = "2"
                                transportationId = "BJ1#VISEMAR ONE#FERRY"
                                transportationType = "F"
                                operatingCarrier = "BAL"
                                marketingCarrier = "BAL"
                                departureTerminal = "VAL"
                                arrivalTerminal = "PAL"
                                departureDate = "2015-09-04T22:15:00"
                                arrivalDate = "2015-09-05T06:00:00"
                                transportationName = "VISEMAR ONE"
                                transportationCode = "BJ1"
                                segmentStatus = "HK"
                                tieneParadaTecnica = "false">
                                <OriginLoc type = "P" code = "VAL" citycode = "false"/>
                                <DestinationLoc type = "P" code = "PAL" citycode = "false"/>
                            </SegmentInfo>
                            <SegmentClasses>
                                <SegmentClass cabinClass = "N" class = "CAFETERIA" paxRef = "0" fareType = "PUB">
                                    <CancellationPolicies>
                                        <CancellationPolicy amount = "0" currency = "EUR" amountType = "PERCENTUAL" fromDate = "2015-08-19T10:16:00" refundable = "true"/>
                                        <CancellationPolicy amount = "10" currency = "EUR" amountType = "PERCENTUAL" fromDate = "2015-08-28T22:15:00" refundable = "true"/>
                                        <CancellationPolicy amount = "20" currency = "EUR" amountType = "PERCENTUAL" fromDate = "2015-09-02T22:15:00" refundable = "true"/>
                                        <CancellationPolicy amount = "100" currency = "EUR" amountType = "PERCENTUAL" fromDate = "2015-09-04T22:15:00" refundable = "true"/>
                                    </CancellationPolicies>
                                    <Modifiable modifiable = "true" amount = "0" currency = "EUR" amountType = "AMOUNT">
                                        <Description>Admite cambios sin cargos</Description>
                                    </Modifiable>
                                </SegmentClass>
                            </SegmentClasses>
                            <TokensReserva/>
                        </Segment>
                    </Segments>
                </Journey>
            </Journeys>
            <AmountBreakdown currency = "EUR" totalAmount = "420" nonCommissionableAmount = "0" commission = "0.942857142857136">
                <ChargeBreakdowns>
                    <ChargeBreakdown type = "VEHICLE" amount = "269.0" currency = "EUR">
                        <Concept id = "0" language = "ES">
                            <Texto>PRECIO VEHICULO</Texto>
                        </Concept>
                    </ChargeBreakdown>
                    <ChargeBreakdown type = "VEHICULE_FEE" amount = "11" currency = "EUR">
                        <Concept id = "1" language = "ES">
                            <Text>FEE VEHICULO</Text>
                        </Concept>
                    </ChargeBreakdown>
                </ChargeBreakdowns>
                <PaxBreakdowns>
                    <PaxBreakdown paxType = "ADT" amount = "140" taxes = "11" currency = "EUR"/>
                </PaxBreakdowns>
            </AmountBreakdown>
            <PaxConfigurations>
                <PaxConfiguration id = "0" paxRef = "0" age = "30" paxType = "ADT">
                    <AppliedBonuses resident = "N" largeFamily = "N" discountCard = "N"/>
                </PaxConfiguration>
            </PaxConfigurations>
            <VehicleConfigurations>
                <VehicleConfiguration vehicleRef = "1" height = "160" length = "350" type = "Tourism" code = "T1" name = "Turismo"/>
            </VehicleConfigurations>
        </Itinerary>
    </Itineraries>
    <PaymentMethod PaymentType = "CASH"/>
    <Locators>
        <Id>BFRFKVM</Id>
        <Type>PROVEEDOR</Type>
    </Locators>
    <commission>0</commission>

\</RetrieveReservationRS\>

|

RetrieveReservationRS Description
=================================

+--------------------------------+----+----+-------------------------------------+
| Element                        | Nu | Ty | Description                         |
|                                | mb | pe |                                     |
|                                | er |    |                                     |
+================================+====+====+=====================================+
| RetrieveReservationRS          | 1  |    | Root node.                          |
+--------------------------------+----+----+-------------------------------------+
| Passengers                     | 1  |    | Contains a list of Passengers.      |
+--------------------------------+----+----+-------------------------------------+
| Passengers/Passenger           | 1. |    | Contains information of the         |
|                                | .n |    | Passenger.                          |
+--------------------------------+----+----+-------------------------------------+
| <*@passengerType>\*            | 1  | St | Treatment: MR, MRS, CHD and INF.    |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@name>\*                     | 1  | St | Name of the Passenger.              |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@surname>\*                  | 1  | St | Surname/s of the Passenger.         |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@bithDate>\*                 | 1  | St | Date of birth.                      |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@codeDCO>\*                  | 1  | St | Document code.                      |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@documentType>\*             | 1  | St | Documentation type.                 |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@documentId>\*               | 1  | St | Unique identifier of the            |
|                                |    | ri | documentation.                      |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@documentExpiration>\*       | 1  | St | Expiration date of the              |
|                                |    | ri | documentation.                      |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@nationality>\*              | 1  | St | Nationality.                        |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| Segments                       | 1  |    | Contains a list of Segment.         |
+--------------------------------+----+----+-------------------------------------+
| Segments/Segment               | 0. |    | Contains details of the Segment.    |
|                                | .n |    |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@id>\*                       | 1  | In | Unique identifier of the            |
|                                |    | te | SegmentInfo.                        |
|                                |    | ge |                                     |
|                                |    | r  |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@transportationId>\*         | 1  | St | Unique Id of the transportation.    |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@transportationType>\*       | 1  | St | Transport type: V ( Flight ), T (   |
|                                |    | ri | Train ), B ( Bus ) & F ( Ferry ).   |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@operatinCarrier>\*          | 1  | St | Company which operates the          |
|                                |    | ri | transportation.                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@marketingCarrier>\*         | 1  | St | Company which commercializes the    |
|                                |    | ri | transportation.                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@departureTerminal>\*        | 1  | St | Departure terminal.                 |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@arrivalTerminal>\*          | 1  | St | Arrival terminal.                   |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@departureDate>\*            | 1  | Da | Departure date.                     |
|                                |    | te |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@arrivalDate>\*              | 1  | Da | Arrival date.                       |
|                                |    | te |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@segmentDuration>\*          | 1  | In | Transport duration ( in minutes ).  |
|                                |    | te |                                     |
|                                |    | ge |                                     |
|                                |    | r  |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@maxCheckinDate>\*           | 1  | St | Maximum date to make the check-in.  |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@segmentStatus>\*            | 1  | St | SegmentInfo status: HK (OK), TK     |
|                                |    | ri | (Change of programming), UC         |
|                                |    | ng | (Unconfirmed), UN( Unable), NO (No  |
|                                |    |    | action taken) & UD (Undefined)      |
+--------------------------------+----+----+-------------------------------------+
| <*@hasTechnicalStop>\*         | 1  | Bo | If true, the SegmentInfo has a      |
|                                |    | ol | technical stop.                     |
|                                |    | ea |                                     |
|                                |    | n  |                                     |
+--------------------------------+----+----+-------------------------------------+
| Segments/Segment /OriginLoc    | 1  |    | Origin location.                    |
+--------------------------------+----+----+-------------------------------------+
| <*@type>\*                     | 1  | St | Type of station of the location     |
|                                |    | ri | indicated with A ( AirPort ), T (   |
|                                |    | ng | Train Station ) & P ( Port ).       |
+--------------------------------+----+----+-------------------------------------+
| <*@code>\*                     | 1  | St | Location code.                      |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@cityCode>\*                 | 1  | Bo | If true, the field code indicates a |
|                                |    | ol | city code, if false, it will        |
|                                |    | ea | indicate an airport code.           |
|                                |    | n  |                                     |
+--------------------------------+----+----+-------------------------------------+
| Segments/Segment/DestinationLo | 1  |    | Destination location.               |
| c                              |    |    |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@type>\*                     | 1  | St | Type of station of the location     |
|                                |    | ri | indicated with A ( AirPort ), T (   |
|                                |    | ng | Train Station ) & P ( Port ).       |
+--------------------------------+----+----+-------------------------------------+
| <*@code>\*                     | 1  | St | Location code.                      |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@cityCode>\*                 | 1  | Bo | If true, the field code indicates a |
|                                |    | ol | city code, if false, it will        |
|                                |    | ea | indicate an airport code.           |
|                                |    | n  |                                     |
+--------------------------------+----+----+-------------------------------------+
| Segments/Segment/TechnicalStop | 0. |    | Contains a list of TechnicalStops.  |
| s                              | .1 |    |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@totalTechnicalStops>\*      | 1  | In | Total number of TechnicalStops.     |
|                                |    | te |                                     |
|                                |    | ge |                                     |
|                                |    | r  |                                     |
+--------------------------------+----+----+-------------------------------------+
| Segments/Segment/TechnicalStop | 1. |    | Contains the details of the         |
| s/TechnicalStop                | .n |    | TechnicalStop.                      |
+--------------------------------+----+----+-------------------------------------+
| <*@location>\*                 | 1  | St | TechnicalStop location.             |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@stopDate>\*                 | 1  | Da | Approx. stop date and time.         |
|                                |    | te |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@departureDate>\*            | 1  | Da | Approx. departure date and time.    |
|                                |    | te |                                     |
+--------------------------------+----+----+-------------------------------------+
| Segments/Segment/SegmentClasse | 0. |    | Contains a list of SegmentClasses.  |
| s                              | .1 |    |                                     |
+--------------------------------+----+----+-------------------------------------+
| Segments/Segment/SegmentClasse | 0. |    | Contains details of the             |
| s/SegmentClass                 | .n |    | SegmentClass.                       |
+--------------------------------+----+----+-------------------------------------+
| <*@cabinClass>\*               | 1  | St | Cabin class of the seat: N (Not     |
|                                |    | ri | specified), Y (Tourist), C          |
|                                |    | ng | (Business), F (First), CA (Cabin,   |
|                                |    |    | only for ferries), YP (Tourist      |
|                                |    |    | Plus)                               |
+--------------------------------+----+----+-------------------------------------+
| <*@class>\*                    | 1  | St | Fare class.                         |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@paxRef>\*                   | 1  | In | Reference for the Passenger which   |
|                                |    | te | is using this fare in the           |
|                                |    | ge | transport.                          |
|                                |    | r  |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@fareBasis>\*                | 1  | St | Fare basis.                         |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@fareType>\*                 | 1  | St | Fare type: PUB ( Public ), PRI (    |
|                                |    | ri | Private ), NEGO ( Negotiated ) &    |
|                                |    | ng | CORP ( Corporate ).                 |
+--------------------------------+----+----+-------------------------------------+
| Segments/Segment/ReservationTo | 0. |    | Contains specific attributes of     |
| ken                            | .1 |    | each provider.                      |
+--------------------------------+----+----+-------------------------------------+
| Segments/Segment/ReservationTo | 0. |    | Contains details of the attribute.  |
| ken/Attribute                  | .n |    |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@id>\*                       | 1  |    | Keyword or id to identify a         |
|                                |    |    | parameter.                          |
+--------------------------------+----+----+-------------------------------------+
| <*@value>\*                    | 1  |    | Value of the parameter.             |
+--------------------------------+----+----+-------------------------------------+
| Tickets                        | 1  |    | List of issued tickets.             |
+--------------------------------+----+----+-------------------------------------+
| Tickets/retrieveStatus         | 1  | Bo | Indicates whether or not the        |
|                                |    | ol | reservation had its tickets issued. |
|                                |    | ea |                                     |
|                                |    | n  |                                     |
+--------------------------------+----+----+-------------------------------------+
| Tickets/errorRetrieve          | 1  | St | Indicates error in the ticket       |
|                                |    | ri | retrieval.                          |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| Tickets/Ticket                 | 1. |    | Details of issued ticket.           |
|                                | .n |    |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@id>\*                       | 1  | In | Unique identifier of the ticket.    |
|                                |    | te |                                     |
|                                |    | ge |                                     |
|                                |    | r  |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@ticketNum>\*                | 1  | St | Ticket number.                      |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@paxName>\*                  | 1  | St | Name of the passenger associated to |
|                                |    | ri | the ticket.                         |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@status>\*                   | 1  | St | Current status of the ticket: OPEN, |
|                                |    | ri | CONFIRMED, VOIDED, REFUNDED         |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| Itinerary                      | 1  |    | Deprecated.                         |
+--------------------------------+----+----+-------------------------------------+
| Itineraries                    | 1  |    | List of Itineraries.                |
+--------------------------------+----+----+-------------------------------------+
| Itineraries/Itinerary          | 1. |    | Details of the Itinerary.           |
|                                | .n |    |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@id>\*                       | 1  | In | Unique identifier of the Itinerary. |
|                                |    | te |                                     |
|                                |    | ge |                                     |
|                                |    | r  |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@fareRef>\*                  | 1  | In | Reference identifier to the         |
|                                |    | te | original Fare. Flights parameter.   |
|                                |    | ge |                                     |
|                                |    | r  |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@HasObFees>\*                | 1  | Bo | If true then there is an extra fee  |
|                                |    | ol | for using credit card.              |
|                                |    | ea |                                     |
|                                |    | n  |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@carrier>\*                  | 1  | St | Validating carrier. Flights         |
|                                |    | ri | parameter.                          |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| Itineraries/Itinerary/Journeys | 0. |    | Contains a list of Journeys.        |
|                                | .1 |    |                                     |
+--------------------------------+----+----+-------------------------------------+
| Itineraries/Itinerary/Journeys | 0. |    | Contains details of the Journeys.   |
| /Journey                       | .n |    |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@id>\*                       | 1  | In | Unique identifier of the Journey in |
|                                |    | te | scope.                              |
|                                |    | ge |                                     |
|                                |    | r  |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@duration>\*                 | 1  | In | Duration of the Journey in minutes. |
|                                |    | te |                                     |
|                                |    | ge |                                     |
|                                |    | r  |                                     |
+--------------------------------+----+----+-------------------------------------+
| Itineraries/Itinerary/Journeys | 0. |    | Contains a list of Segments         |
| /Journey/Segments              | .1 |    | associated to the Journey.          |
+--------------------------------+----+----+-------------------------------------+
| > Itineraries/Itinerary/Journe | 0. |    | Contains details of the             |
| ys/Journey/Segments/Segment    | .n |    | SegmentInfo.                        |
+--------------------------------+----+----+-------------------------------------+
| <*@id>\*                       | 1  | In | Unique SegmentInfo identifier.      |
|                                |    | te |                                     |
|                                |    | ge |                                     |
|                                |    | r  |                                     |
+--------------------------------+----+----+-------------------------------------+
| Itineraries/Itinerary/Journeys | 0. |    | Contains information of the         |
| /Journey/Segments/Segment/Segm | .n |    | SegmentInfo.                        |
| entInfo                        |    |    |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@id>\*                       | 1  | In | Unique identifier of the            |
|                                |    | te | SegmentInfo.                        |
|                                |    | ge |                                     |
|                                |    | r  |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@transportationId>\*         | 1  | St | Unique Id of the transportation.    |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@transportationType>\*       | 1  | St | Transport type: F ( Flight ), T (   |
|                                |    | ri | Train ), B ( Bus ) & F ( Ferry ).   |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@operatinCarrier>\*          | 1  | St | Company which operates the          |
|                                |    | ri | transportation.                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@marketingCarrier>\*         | 1  | St | Company which commercializes the    |
|                                |    | ri | transportation.                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@departureTerminal>\*        | 1  | St | Departure terminal.                 |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@arrivalTerminal>\*          | 1  | St | Arrival terminal.                   |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@departureDate>\*            | 1  | Da | Departure date.                     |
|                                |    | te |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@arrivalDate>\*              | 1  | Da | Arrival date.                       |
|                                |    | te |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@segmentDuration>\*          | 1  | In | Transport duration ( in minutes ).  |
|                                |    | te |                                     |
|                                |    | ge |                                     |
|                                |    | r  |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@planeType>\*                | 1  | St | Plane type. Flights parameter.      |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@maxCheckinDate>\*           | 1  | St | Maximum date to make the check-in.  |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@segmentStatus>\*            | 1  | St | SegmentInfo status: HK (OK), TK     |
|                                |    | ri | (Change of programming), UC         |
|                                |    | ng | (Unconfirmed), UN( Unable), NO (No  |
|                                |    |    | action taken) & UD (Undefined)      |
+--------------------------------+----+----+-------------------------------------+
| <*@hasTechnicalStop>\*         | 1  | Bo | If true, the SegmentInfo has a      |
|                                |    | ol | technical stop.                     |
|                                |    | ea |                                     |
|                                |    | n  |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@electronicTicket>\*         | 1  | Bo | If true, the SegmentInfo uses a     |
|                                |    | ol | electronic ticket.                  |
|                                |    | ea |                                     |
|                                |    | n  |                                     |
+--------------------------------+----+----+-------------------------------------+
| Itineraries/Itinerary/Journeys | 1  |    | Origin location.                    |
| /Journey/Segments/Segment/Segm |    |    |                                     |
| entInfo/OriginLoc              |    |    |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@type>\*                     | 1  | St | Type of station of the location     |
|                                |    | ri | indicated with A ( AirPort ), T (   |
|                                |    | ng | Train Station ) & P ( Port ).       |
+--------------------------------+----+----+-------------------------------------+
| <*@code>\*                     | 1  | St | Location code.                      |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@cityCode>\*                 | 1  | Bo | If true, the field code indicates a |
|                                |    | ol | city code, if false, it will        |
|                                |    | ea | indicate an airport code.           |
|                                |    | n  |                                     |
+--------------------------------+----+----+-------------------------------------+
| Itineraries/Itinerary/Journeys | 1  |    | Destination location.               |
| /Journey/Segments/Segment/Segm |    |    |                                     |
| entInfo/DestinationLoc         |    |    |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@type>\*                     | 1  | St | Type of station of the location     |
|                                |    | ri | indicated with A ( AirPort ), T (   |
|                                |    | ng | Train Station ) & P ( Port ).       |
+--------------------------------+----+----+-------------------------------------+
| <*@code>\*                     | 1  | St | Location code.                      |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@cityCode>\*                 | 1  | Bo | If true, the field code indicates a |
|                                |    | ol | city code, if false, it will        |
|                                |    | ea | indicate an airport code.           |
|                                |    | n  |                                     |
+--------------------------------+----+----+-------------------------------------+
| Transportation/Segments/Segmen | 0. |    | Contains a list of TechnicalStops.  |
| t/TechnicalStops               | .1 |    |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@totalTechnicalStops>\*      | 1  | In | Total number of TechnicalStops.     |
|                                |    | te |                                     |
|                                |    | ge |                                     |
|                                |    | r  |                                     |
+--------------------------------+----+----+-------------------------------------+
| Transportation/Segments/Segmen | 1. |    | Contains the details of the         |
| t/TechnicalStops/TechnicalStop | .n |    | TechnicalStop.                      |
+--------------------------------+----+----+-------------------------------------+
| <*@location>\*                 | 1  | St | TechnicalStop location.             |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@stopDate>\*                 | 1  | Da | Approx. stop date and time.         |
|                                |    | te |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@departureDate>\*            | 1  | Da | Approx. departure date and time.    |
|                                |    | te |                                     |
+--------------------------------+----+----+-------------------------------------+
| Itineraries/Itinerary/Journeys | 0. |    | Contains a list of SegmentClasses.  |
| /Journey/Segments/Segment/Segm | .1 |    |                                     |
| entClasses                     |    |    |                                     |
+--------------------------------+----+----+-------------------------------------+
| Itineraries/Itinerary/Journeys | 0. |    | Contains details of the             |
| /Journey/Segments/Segment/Segm | .n |    | SegmentClass.                       |
| entClasses/SegmentClass        |    |    |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@cabinClass>\*               | 1  | St | Cabin class of the seat: N (Not     |
|                                |    | ri | specified), Y (Tourist), C          |
|                                |    | ng | (Business), F (First), CA (Cabin,   |
|                                |    |    | only for ferries), YP (Tourist      |
|                                |    |    | Plus)                               |
+--------------------------------+----+----+-------------------------------------+
| <*@class>\*                    | 1  | St | Fare class.                         |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@paxRef>\*                   | 1  | In | Reference for the Passenger which   |
|                                |    | te | is using this fare in the           |
|                                |    | ge | transport.                          |
|                                |    | r  |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@fareBasis>\*                | 1  | St | Fare basis.                         |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@fareType>\*                 | 1  | St | Fare type: PUB ( Public ), PRI (    |
|                                |    | ri | Private ), NEGO ( Negotiated ) &    |
|                                |    | ng | CORP ( Corporate ).                 |
+--------------------------------+----+----+-------------------------------------+
| Itineraries/Itinerary/Journeys | 0. |    | Contains specific attributes of     |
| /Journey/Segments/Segment/Rese | .1 |    | each provider.                      |
| rvationToken                   |    |    |                                     |
+--------------------------------+----+----+-------------------------------------+
| Itineraries/Itinerary/Journeys | 0. |    | Contains details of the attribute.  |
| /Journey/Segments/Segment/Rese | .n |    |                                     |
| rvationToken/Attribute         |    |    |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@id>\*                       | 1  |    | Keyword or id to identify a         |
|                                |    |    | parameter.                          |
+--------------------------------+----+----+-------------------------------------+
| <*@value>\*                    | 1  |    | Value of the parameter.             |
+--------------------------------+----+----+-------------------------------------+
| Itineraries/Itinerary/AmountBr | 1  |    | Contains details of the             |
| eakdown                        |    |    | AmountBreakdown.                    |
+--------------------------------+----+----+-------------------------------------+
| <*@currency>\*                 | 1  | St | Currency code of the fare.          |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@totalAmount>\*              | 1  | De | Total amount. with taxes and other  |
|                                |    | ci | charges included.                   |
|                                |    | ma |                                     |
|                                |    | l  |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@notCommissionableAmount>\*  | 1  | De | Total amount that can not be        |
|                                |    | ci | commissioned.                       |
|                                |    | ma |                                     |
|                                |    | l  |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@commission>\*               | 1  | De | Commission percentage. A -1 value   |
|                                |    | ci | will be returned if the provider    |
|                                |    | ma | doesn't return any comission        |
|                                |    | l  | information.                        |
+--------------------------------+----+----+-------------------------------------+
| Itineraries/Itinerary/AmountBr | 0. |    | Contains a list of                  |
| eakdown/ChargeBreakdowns       | .1 |    | ChargeBreakdowns.                   |
+--------------------------------+----+----+-------------------------------------+
| Itineraries/Itinerary/AmountBr | 0. |    | Contains a list of breakdown        |
| eakdown/PaxBreakdowns          | .1 |    | amounts for each Passenger ( ADT    |
|                                |    |    | amount, etc. ).                     |
+--------------------------------+----+----+-------------------------------------+
| Itineraries/Itinerary/AmountBr | 0. |    | Contains details of breakdown       |
| eakdown/PaxBreakdowns/PaxBreak | .n |    | amounts for each Passenger.         |
| down                           |    |    |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@paxType>\*                  | 1  | St | Passenger type: ADT ( Adult ), CHD  |
|                                |    | ri | ( Child ) & INF ( Infant ).         |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@amount>\*                   | 1  | De | Total amount, with taxes included,  |
|                                |    | ci | associated to the Passenger.        |
|                                |    | ma |                                     |
|                                |    | l  |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@taxes>\*                    | 1  | In | If they exist, taxes are applied    |
|                                |    | te | for this Passenger type.            |
|                                |    | ge |                                     |
|                                |    | r  |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@tasaDU>\*                   | 1  | In | Deprecated                          |
|                                |    | te |                                     |
|                                |    | ge |                                     |
|                                |    | r  |                                     |
+--------------------------------+----+----+-------------------------------------+
| Itineraries/Itinerary/PaxConfi | 1  |    | Contains a list of                  |
| gurations                      |    |    | PaxConfigurations.                  |
+--------------------------------+----+----+-------------------------------------+
| Itineraries/Itinerary/PaxConfi | 1  |    | Contains details of the             |
| gurations/PaxConfiguration     |    |    | PaxConfiguration.                   |
+--------------------------------+----+----+-------------------------------------+
| <*@id>\*                       | 1  | In | Unique identifier of the            |
|                                |    | te | PaxConfiguration.                   |
|                                |    | ge |                                     |
|                                |    | r  |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@paxRef>\*                   | 1  | In | Reference to the Passenger Id from  |
|                                |    | te | the request.                        |
|                                |    | ge |                                     |
|                                |    | r  |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@age>\*                      | 1  | In | Age of the Passenger.               |
|                                |    | te |                                     |
|                                |    | ge |                                     |
|                                |    | r  |                                     |
+--------------------------------+----+----+-------------------------------------+
| <*@paxType>\*                  | 1  | St | Passenger type based on the age of  |
|                                |    | ri | the Passenger: ADT (Adult), CHD     |
|                                |    | ng | (Child), INF (Infant), YOU (Young)  |
|                                |    |    | and SEN (Senior).                   |
+--------------------------------+----+----+-------------------------------------+
| <*@code>\*                     | 1  | St | String with the PTC code.           |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| PaymentMethod                  | 1  |    | Defines the payment method used in  |
|                                |    |    | the reservation.                    |
+--------------------------------+----+----+-------------------------------------+
| <*@paymentType>\*              | 1  | St | Payment type: CASH, CARD and EMIT.  |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| PaymentMethod/PaymentDatas     | 1  |    | List of PaymentData.                |
+--------------------------------+----+----+-------------------------------------+
| PaymentMethod/PaymentDatas/Pay | 1. |    | Contains the details of             |
| mentData                       | .n |    | PaymentData.                        |
+--------------------------------+----+----+-------------------------------------+
| <*@paymentType>\*              | 1  | St | Payment type: CASH, CARD and EMIT.  |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| PaymentMethod/PaymentDatas/Pay | 1  |    | Contains details of the credit      |
| mentData/CardInfo              |    |    | card.                               |
+--------------------------------+----+----+-------------------------------------+
| Locators                       | 1  |    | Contains a list of locators.        |
+--------------------------------+----+----+-------------------------------------+
| Locators/Locator               | 1  |    | Contains details of the locator.    |
+--------------------------------+----+----+-------------------------------------+
| Locators/Locator/Id            | 1  | St | Unique identifier of the locator.   |
|                                |    | ri |                                     |
|                                |    | ng |                                     |
+--------------------------------+----+----+-------------------------------------+
| Locators/Locator/Type          | 1  | St | Locator type: PROVIDER,             |
|                                |    | ri | TFBOOKINGREFERENCE, UNIVERSAL,      |
|                                |    | ng | EMISSION and CARRIER.               |
+--------------------------------+----+----+-------------------------------------+

|
