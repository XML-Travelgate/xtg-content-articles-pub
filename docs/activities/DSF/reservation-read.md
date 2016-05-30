---
title: Reservation Read
keywords: activities, data structure, reservation read
sidebar: mydoc_sidebar
permalink: /developer-documentation/activities/DSF/reservation-read
---



### Method Goals


This method aims to consult a reservation



### Request Format


The request requires the booking code and the name of the customer



### Response Format


The result returns the new status of the reservation and the possible
cost of the consultation.



### Remarks


Not implemented by all suppliers



### ReservationReadRQ Example




    <OTA_ReadRQ>
        xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance"
        xmlns:xsd = "http://www.w3.org/2001/XMLSchema"
        PrimaryLangID = "es">
        <UniqueID ID = "1283712#1" Type = "PROVIDER"/>
    </OTA_ReadRQ>



### ReservationReadRQ Description




| **Element**			| **Number**	| **Type**	| **Description**				|
| ----------------------------- | ------------- | ------------- | --------------------------------------------- |
| OTA_ReadRQ			| 1          	|		| Root node.					|
| @PrimaryLangID		| 1    		| String	| Language code (ISO 3166-1 alpha-2) format. 	|
| UniqueID  			| 1          	|		| Contains information of the activity booked. 	|
| @ID       			| 1    		| String	| Activity booked identifier.			|
| @type     			| 1    		| String	| Activity booked type (Possible values: "PROVIDER" or "CLIENT"). Usually by provider locator. |



### ReservationReadRS Example




    <OTA_TourActivityResRetrieveRS xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd = "http://www.w3.org/2001/XMLSchema">
        <operationImplemented>true</operationImplemented>
        <Detail ResStatus = "Confirmed" CreateDateTime = "2013-11-21T00:00:00" LastModifyDateTime="2014-02-19T00:00:00">
            <BasicInfo Name = "Palma Aquarium" TourActivityID = "000200515"/>
            <Confirmation ID = "1283712#1" type = "PROVIDER"/>
            <PaymentInfo Description = "El importe total de esta factura PRO-FORMA debe obrar en poder de Beds On Line, Banco: CITIBANK(Avenida de Europa, 19 - P.E. la Moraleja, 108 - Alcobendas, Madrid) Cuenta:ES35 1474 0000 10 0012272006,  SWIFT:CITIESMX,  7 das antes de la llegada de los clientes (excepto reservas de grupos. Das de antelacin fijados en el momento de la confirmacin). En la orden de pago rogamos indiquen nuestro nmero de referencia.    Gracias por su colaboracin., AVISO: CAMBIO CDIGO SWIFT"/>
            <PickupDropoff OtherInfo = "El cliente puede canjear el bono en la oficina de billetes de Aquarium en C/ Manuela de los Herreros i Sor, 21 | 07610 Palma de Mallorca 

            Invierno (1 de noviembre a 31 de marzo):
            Lunes a viernes de 10:00 a 15:30 h
            Sbado & Domingo de 10:00h a 16:30h
            Verano (1 de abril a 31 de octubre):
            Todos los das de 9:30h a 18:30h

            El cliente no puede olvidar llevar su documento de identidad.

            En caso de emergencia, el cliente deber llamar al siguiente nmero: (+34) 902 430 419

             "/>
            <Pricing>
                <Summary Amount = "33.340" CurrencyCode = "EUR">
                    <PricingType Extension = "PerTotal">Other_</PricingType>
                </Summary>
                <ParticipantCategory age = "30">
                    <QualifierInfo>Adult</QualifierInfo>
                    <Price
                        Amount = "19.660"
                        CurrencyCode = "EUR"/>
                </ParticipantCategory>
                <ParticipantCategory age = "2">
                    <QualifierInfo>Infant</QualifierInfo>
                    <Price
                        Amount = "0.000"
                        CurrencyCode = "EUR"/>
                </ParticipantCategory>
                <ParticipantCategory age = "10">
                    <QualifierInfo>Children</QualifierInfo>
                    <Price
                        Amount = "13.681"
                        CurrencyCode = "EUR"/>
                </ParticipantCategory>
            </Pricing>
            <Schedule>
                <Detail>
                    <OperationTimes>
                        <OperationTime StartDate = "2013-12-18T00:00:00" EndDate = "2013-12-18T00:00:00"/>
                    </OperationTimes>
                </Detail>
            </Schedule>
        </Detail>
    </OTA_TourActivityResRetrieveRS>



### ReservationReadRS Description




| **Element**				| **Number**	| **Type**	| **Description**				|
| ------------------------------------- | ------------- | ------------- | --------------------------------------------- |
| OTA_TourActivityResRetrieveRS		| 1       	|		| Root node.					|
| Detail            			| 1       	|		| Information about reservation status and date time.|
| @ResStatus        			| 1  		| Enum		| Information about reservation status (Possibles types: "Confirmed", "Cancel" or "Unknow"). |
| @CreateDateTime   			| 1  		| Date		| Information about create reservation date time. |
| @LastModifyDateTime			| 1  		| Date		| Information about last modify reservation date time. For example, if cancel we return date time when client cancel this reservation. |
| Detail/BasicInfo  			| 0..1     	|		| If need search by activity provider code.	|
| @Name             			| 0..1		| String	| Name of ticket.				|
| @TourActivityID   			| 0..1		| String	| Code of ticket.				|
| Detail/Confirmation			| 1       	|		| Contains information of the activity booked.	|
| @ID               			| 1  		| String	| Activity booked identifier.			|
| @type             			| 1  		| String	| Activity booked type (Possible values: "PROVIDER").|
| Detail/PaymentInfo			| 0..1     	|		| Payment details that may be associated with an individual participant, a participant category and/or a group. |
| @Description      			| 0..1		| String	| A description of the charge.			|
| Detail/PickupDropoff			| 0..1		| String	| The pickup and/or dropoff information if transportation is provided to/ from thetour/activity location. |
| @OtherInfo        			| 0..1		| String	| Other instructions pertaining to the pickup/dropoff. |
| Pricing/Summary   			| 0..1     	|		| Summary price for option, this element we return if OpenAvailability = false. |
| @Amount           			| 0..1		| Decimal	| Option price.					|
| @CurrencyCode     			| 0..1		| String	| Currency code (ISO 4217).			|
| Detail/Pricing/Summary/PricingType	| 0..1		| String	| Specifies type of the option price, if value = Other then is mandatory specify Extension type. |
| @Extension        			| 0..1		| String	| Specifies type of the option price.		|
| Detail/Pricing/ParticipantCategory	| 0..n		| String	| Specifies price and participant category.	|
| @age              			| 0..1		| Integer	| Age of participant category.			|
| Detail/Pricing/ParticipantCategory/QualifierInfo | 0..1 | String	| Specifies participant type (Adult, Children or Baby). If value = Other then then is mandatory specify Extension providertype. |
| @Extension        			| 0..1 		| String	| Specifies provider code of participant category. |
| Detail/Pricing/ParticipantCategory/Price | 1       	|		| Specific price for each participantCategory.	|
| @Amount           			| 1  		| String	| ParticipantCategory price.			|
| @CurrencyCode     			| 0..1		| String	| Currency code (ISO 4217).			|
| Detail/Schedule   			| 0..1     	|		| Information about dates range on which you can enjoy the activity. The same information that send in request. |
| Detail/Schedule/Detail		| 0..1     	|		| Information about specify dates on which you can enjoy the activity. |
| Detail/Schedule/Detail/OperationTimes	| 0..1     	|		| Information about specify dates on which you can enjoy the activity. |
| Detail/Schedule/Detail/OperationTimes/OperationTime | 0..1 |		| Information when activity starts.		|
| @Start            			| 0..1		| Date		| Start date activity.				|
| @End              			| 0..1		|		| Date End date activity.			|


