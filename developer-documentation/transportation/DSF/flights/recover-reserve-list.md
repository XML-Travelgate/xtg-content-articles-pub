---
title: RetrieveReservationList
keywords: transportation, data structure, flights, recover reserve, retrieve list, list, reservation
sidebar: mydoc_sidebar
permalink: /developer-documentation/transportation/DSF/flights/recover-reserve-list
---



Method Goals
============

This method aims to return a list of bookings for a given time period
being that either booking date or the travelling date.



RetrieveReservationListRQ Example
=================================



    <RetrieveReservationListRQ>
        <Configuration/>
        <ClientConfiguration currencyCode = "GBP"/>
        <ReservationDate>2014-03-04T00:00:00</ReservationDate>
        <DepartureDate>2010-09-09T00:00:00</DepartureDate>
        <ClientEmail>client@clientmail.com</ClientEmail>
        <OriginCode></OriginCode>
        <DestinationCode></DestinationCode>
        <AgencyCode></AgencyCode>
    </RetrieveReservationListRQ>



RetrieveReservationListRQ Description
=====================================


| **Element**				| **Number**	| **Type**	| **Description**						|
| ------------------------------------- | ------------- | ------------- | ------------------------------------------------------------- |
| RetrieveReservationListRQ     	| 1    		|		| Root node.							|
| ReservationDate               	| 1 		| String	| Reservation date.						|
| DepartureDate                 	| 1 		| String	| Departure date.						|
| ClientEmail                   	| 1 		| String	| Client's email.						|
| OriginCode                    	| 1 		| String	| Origin code.							|
| DestinationCode               	| 1 		| String	| Destination code.						|
| AgencyCode                    	| 1 		| String	| Contains a list of Passengers.				|
 



RetrieveReservationListRS Example
=================================



    <RetrieveReservationListRS xmlns:xsd = "http://www.w3.org/2001/XMLSchema" xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance">
        <auditData>
            <timeStamp>2014-03-11T09:04:11.1793394+01:00</timeStamp>
            <processTimeMilliseconds>0</processTimeMilliseconds>
        </auditData>
        <operationImplemented>true</operationImplemented>
        <ResponseStatus tripType = "IDA" petitionType = "OW" status = "ok"/>
        <ReservationList>
            <PaymentInfo locator = "V65CQC" totalAmount = "0">
                <OriginCode>VCE</OriginCode>
                <DestinationCode>ORY</DestinationCode>
                <ReservationDate>0001-01-01T00:00:00</ReservationDate>
                <DepartureDate>2014-03-25T20:30:00</DepartureDate>
                <MainPaxName/>
                <HolderName>Jean Francois PRUNIER</HolderName>
                <ProviderReservationStatus/>
                <ReservationStatus>
                    <ReservationStatusType>CONFIRMED</ReservationStatusType>
                </ReservationStatus>
            </PaymentInfo>
            <PaymentInfo locator = "M3LIUI" totalAmount = "0">
                <OriginCode>OPO</OriginCode>
                <DestinationCode>AMS</DestinationCode>
                <ReservationDate>0001-01-01T00:00:00</ReservationDate>
                <DepartureDate>2014-05-12T16:10:00</DepartureDate>
                <MainPaxName/>
                <HolderName>Antonio Rui Santos Almeida</HolderName>
                <ProviderReservationStatus/>
                <ReservationStatus>
                    <ReservationStatusType>CONFIRMED</ReservationStatusType>
                </ReservationStatus>
            </PaymentInfo>
            <PaymentInfo locator = "V36MSL" totalAmount = "0">
                <OriginCode>LIS</OriginCode>
                <DestinationCode>ORY</DestinationCode>
                <ReservationDate>0001-01-01T00:00:00</ReservationDate>
                <DepartureDate>2014-05-25T19:30:00</DepartureDate>
                <MainPaxName/>
                <HolderName>Damien THERET</HolderName>
                <ProviderReservationStatus/>
                <ReservationStatus>
                    <ReservationStatusType>CONFIRMED</ReservationStatusType>
                </ReservationStatus>
            </PaymentInfo>
            <PaymentInfo locator = "M6WM6Z" totalAmount = "0">
                <OriginCode>LIS</OriginCode>
                <DestinationCode>ORY</DestinationCode>
                <ReservationDate>0001-01-01T00:00:00</ReservationDate>
                <DepartureDate>2014-03-19T08:50:00</DepartureDate>
                <MainPaxName/>
                <HolderName>maria esteves</HolderName>
                <ProviderReservationStatus/>
                <ReservationStatus>
                    <ReservationStatusType>CONFIRMED</ReservationStatusType>
                </ReservationStatus>
            </PaymentInfo>
            <PaymentInfo locator = "KCR8MX" totalAmount = "0">
                <OriginCode>LIS</OriginCode>
                <DestinationCode>ORY</DestinationCode>
                <ReservationDate>0001-01-01T00:00:00</ReservationDate>
                <DepartureDate>2014-03-20T08:50:00</DepartureDate>
                <MainPaxName/>
                <HolderName>antonio francisco alves</HolderName>
                <ProviderReservationStatus/>
                <ReservationStatus>
                    <ReservationStatusType>CONFIRMED</ReservationStatusType>
                </ReservationStatus>
            </PaymentInfo>
            <PaymentInfo locator = "F45R3C" totalAmount = "0">
                <OriginCode>FNC</OriginCode>
                <DestinationCode>OPO</DestinationCode>
                <ReservationDate>0001-01-01T00:00:00</ReservationDate>
                <DepartureDate>2014-05-06T17:10:00</DepartureDate>
                <MainPaxName/>
                <HolderName>RAFAEL GARCIA CONDE</HolderName>
                <ProviderReservationStatus/>
                <ReservationStatus>
                    <ReservationStatusType>CONFIRMED</ReservationStatusType>
                </ReservationStatus>
            </PaymentInfo>
            <PaymentInfo locator = "V3MIRY" totalAmount = "0">
                <OriginCode>ORY</OriginCode>
                <DestinationCode>NAP</DestinationCode>
                <ReservationDate>0001-01-01T00:00:00</ReservationDate>
                <DepartureDate>2014-04-06T16:15:00</DepartureDate>
                <MainPaxName/>
                <HolderName>chiara mauro</HolderName>
                <ProviderReservationStatus/>
                <ReservationStatus>
                    <ReservationStatusType>CONFIRMED</ReservationStatusType>
                </ReservationStatus>
            </PaymentInfo>
            <PaymentInfo locator = "IC1FGK" totalAmount = "0">
                <OriginCode>ORY</OriginCode>
                <DestinationCode>MIR</DestinationCode>
                <ReservationDate>0001-01-01T00:00:00</ReservationDate>
                <DepartureDate>2014-03-16T06:15:00</DepartureDate>
                <MainPaxName/>
                <HolderName>Habib KHALED</HolderName>
                <ProviderReservationStatus/>
                <ReservationStatus>
                    <ReservationStatusType>CONFIRMED</ReservationStatusType>
                </ReservationStatus>
            </PaymentInfo>
            <PaymentInfo locator = "A8V4FD" totalAmount = "0">
                <OriginCode>LIS</OriginCode>
                <DestinationCode>ORY</DestinationCode>
                <ReservationDate>0001-01-01T00:00:00</ReservationDate>
                <DepartureDate>2014-03-20T08:50:00</DepartureDate>
                <MainPaxName/>
                <HolderName>DIOGO FREITAS</HolderName>
                <ProviderReservationStatus/>
                <ReservationStatus>
                    <ReservationStatusType>CONFIRMED</ReservationStatusType>
                </ReservationStatus>
            </PaymentInfo>
            <PaymentInfo locator = "H4YF4C" totalAmount = "0">
                <OriginCode>OPO</OriginCode>
                <DestinationCode>FNC</DestinationCode>
                <ReservationDate>0001-01-01T00:00:00</ReservationDate>
                <DepartureDate>2014-05-17T07:50:00</DepartureDate>
                <MainPaxName/>
                <HolderName>Laurinda Gomes</HolderName>
                <ProviderReservationStatus/>
                <ReservationStatus>
                    <ReservationStatusType>CONFIRMED</ReservationStatusType>
                </ReservationStatus>
            </PaymentInfo>
        </ReservationList>
    </RetrieveReservationListRS>



RetrieveReservationListRS Description
=====================================


| **Element**				| **Number**	| **Type**	| **Description**						|
| ------------------------------------- | ------------- | ------------- | ------------------------------------------------------------- |
| RetrieveReservationListRS     	| 1    		|		| Root node.							|
| ReservationList               	| 1    		|		| Contains a list of Reservations.				|
| ReservationList/PaymentInfo   	| 1..n   	|		| Contains the information of the payment.			|
| @locator                 		| 1 		| String	| Unique identifier of the locator.				|
| @totalAmount             		| 1 		| Decimal	| Total amount. with taxes and other charges included.		|
| @currency                		| 1 		| String	| Currency code of the fare.					|
| ReservationList/PaymentInfo /OriginCode | 1 		| String	| Trip origin location code.					|
| ReservationList/PaymentInfo /DestinationCode | 1 	| String	| Trip destination location code.				|
| ReservationList/PaymentInfo /ReservationDate | 1 	| Date		| Date on which the reservation was made.			|
| ReservationList/PaymentInfo /DepartureDate | 1 	| Date		| Departure date.						|
| ReservationList/PaymentInfo /MainPaxName | 1 		| String	| Name and surname of the main passenger of the reservation.	|
| ReservationList/PaymentInfo /HolderName | 1 		| String	| Name of the holder of the reservation.			|
| ReservationList/PaymentInfo /ReservationStatus | 1    |		| Current status of the reservation.				|
| ReservationList/PaymentInfo /ReservationStatus /ReservationStatusType | 1 | String | Reservation status: CONFIRMED (OK), CANCELLED (Change of programming).	|



