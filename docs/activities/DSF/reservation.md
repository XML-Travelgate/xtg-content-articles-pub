---
title: Reservation
keywords: activities, data structure, reservation
sidebar: mydoc_sidebar
permalink: /developer-documentation/activities/DSF/reservation
---



### ReservationRQ Example




    <OTA_TourActivityBookRQ>
        xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance"
        xmlns:xsd = "http://www.w3.org/2001/XMLSchema"
        PrimaryLangID = "es">
        <ContactDetail>
            <BirthDate>1984-02-19T00:00:00</BirthDate>
            <PersonName>
                <GivenName>TestNameClient</GivenName>
                <Surname>TestApClient</Surname>
            </PersonName>
        </ContactDetail>
        <BookingInfo>
            <BasicInfo Name = "Palma Aquarium" TourActivityID = "000200515"/>
            <Schedule StartPeriod = "2014-02-26T00:00:00" EndPeriod = "2014-02-27T00:00:00"/>
            <ParticipantInfo>
                <Individual LeadCustomerInd = "true" age = "30">
                    <GivenName>TestName1</GivenName>
                    <Surname>TestAp1</Surname>
                </Individual>
            </ParticipantInfo>
            <Pricing>
                <Summary Amount = "19.660" CurrencyCode = "EUR">
                    <PricingType Extension = "PerTotal">Other_</PricingType>
                </Summary>
                <ParticipantCategory age = "30">
                    <QualifierInfo>Adult</QualifierInfo>
                    <Price
                        Amount = "19.660"
                        CurrencyCode = "EUR"/>
                </ParticipantCategory>
            </Pricing>
            <TPA_Extensions>
                <Confirmation ID = "4791780" type = "CLIENT"/>
                <!--OpenAvailability ="true" -->
                <Issue Mandatory = "true"/>
                <Attributes>
                    <!--Attributes mandatory for confirmation. Specific for IMP -->
                    <Attribute key = "idAgrupacion" value = "8181"/>
                    <Attribute key = "idPago" value = "1"/>
                </Attributes>
            </TPA_Extensions>
        </BookingInfo>
    </OTA_TourActivityBookRQ>



### ReservationRQ Description




| **Element**				| **Number**	| **Type**	| **Description**				|
| ------------------------------------- | ------------- | ------------- | --------------------------------------------- |
| OTA_TourActivityBookRQ		| 1      	|		| Root node.    				|
| @PrimaryLangID     			| 1  		| String	| Language code (ISO 3166-1 alpha-2) format.	|
| ContactDetail      			| 0..1    	|		| Information about holder client.    		|
| ContactDetail/BirthDate		| 0..1		| Date		| Holder BirthDate.				|
| ContactDetail/BirthDate/PersonName	| 0..1		| Date		| Information about name holder.		|
| ContactDetail/BirthDate/PersonName/GivenName | 0..1	| String	| Name holder.                        		|
| ContactDetail/BirthDate/PersonName/Surname | 0..1	| String	| Surname holder.				|
| BookingInfo        			| 0..1    	|		| Information about specific ticket.   		|
| BookingInfo/BasicInfo			| 0..1    	|		| If need search by activity provider code.	|
| @Name              			| 0..1		| String	| Name of ticket.				|
| @TourActivityID    			| 1  		| String	| Code of ticket, mandatory if need search by activity provider code. |
| BookingInfo/Schedule			| 1      	|		| Information about dates range on which you can enjoy the activity. |
| BookingInfo/Schedule			| 1      	|		| Information about dates range on which you can enjoy the activity. |
| @StartPeriod       			| 1  		| Date		| Start date that you apply availability.	|
| @EndPeriod         			| 1  		| Date		| End date that you apply availability.		|
| BookingInfo/CategoryAndType		| 0..1    	|		| Category of Ticket.				|
| BookingInfo/CategoryAndType/Category	| 0..1   	|		| Category of Ticket.				|
| @Code              			| 0..1		| String	| A category code from a predefined list, if Extension = "Other" then will be provider code. |
| @Extension         			| 0..1		| String	| Enter a category here if you have selected "Other" from the pre-defined list. |
| BookingInfo/ParticipantInfo		| 1..n    	|		| Information about all participants.		|
| @OtherInfo         			| 0..1		| String	| Other instructions pertaining to the pickup/dropoff. |
| BookingInfo/ParticipantInfo/Individual | 1      	|		| Information about each participant.		|
| @LeadCustomerInd   			| 1  		| Boolean	| When 'true', indicates that this is the 'lead' participantr (i.e., the primary contact making the booking). |
| @Age               			| 1  		| Integer	| Age of participant.  				|
| BookingInfo/ParticipantInfo/Individual/GivenName | 1 	| String	| Participant Name.				|
| BookingInfo/ParticipantInfo/Individual/Surname | 1 	| String	| Participant Surname.				|
| Pricing/ParticipantCategory/QualifierInfo | 0..1	| String	| Specifies participant type (Adult, Children or Babie). If value = "Other_" then then is mandatory specify Extension provider type. |
| Pricing/ParticipantCategory/Price	| 1      	|		| Specific price for each participantCategory.	|
| @Amount            			| 1  		| String	| ParticipantCategory price.			|
| @CurrencyCode      			| 0..1		| String	| Currency code (ISO 4217).			1
| Pricing/ParticipantCategory/TPA_Extensions | 0..1    	|		| Necessary information that we need send  between calls. |
| Pricing/ParticipantCategory/TPA_Extensions/DynamicToken | 0..1 | String | Inform about the participant types to valuate (if more than one type, the participant Types  must be separated by ";"). |
| Pricing/ParticipantCategory/TPA_Extensions/Issue | 0..1 |   		| Contains information about ticket printing.	|
| @Mandatory         			| 0..1		| Boolean	| Specifies if the ticket should be printed by the client. |
| Pricing/ParticipantCategory/TPA_Extensions/Attributes | 0..1 |    	| Attributes that we need send between calls.	|
| Pricing/ParticipantCategory/TPA_Extensions/Attributes/Attribute | 0..n |  | Attributes that we need send between calls.  |
| @idAgrupacion      			| 1  		| String	| In this case, is specific attribute mandatory for IMP. This can obtain in iFRAME, from UrlSitting that we return in availabilityRS, this is for preBook reservation. |
| @idPago            			| 1  		| String	| In this case, is specific attribute mandatory for IMP. This can obtain in iFRAME, from  UrlSitting that we return in availabilityRS, this is for preBook reservation. |



### ReservationRS Example




    <OTA_TourActivityBookRS>
        <ReservationDetails>
            <BasicInfo Name = "Palma Aquarium" TourActivityID = "000200515"/>
            <Confirmation ID = "1314215#1" type = "PROVIDER"/>
            <Schedule>
                <Detail>
                    <OperationTimes>
                        <OperationTime Start = "2014-03-07T21:00:00" End = "2014-03-07T23:00:00"/>
                    </OperationTimes>
                </Detail>
            </Schedule>
            <PaymentInfo Description = "El importe total de esta factura PRO-FORMA debe obrar en poder de Beds On Line, Banco: CITIBANK(Avenida de Europa, 19 - P.E. la Moraleja, 108 - Alcobendas, Madrid) Cuenta:ES35 1474 0000 10 0012272006,  SWIFT:CITIESMX,  7 das antes de la llegada de los clientes (excepto reservas de grupos. Das de antelacin fijados en el momento de la confirmacin). En la orden de pago rogamos indiquen nuestro nmero de referencia.    Gracias por su colaboracin., AVISO: CAMBIO CDIGO SWIFT"/>
            <Pricing>
                <Summary Amount = "19.660" CurrencyCode = "EUR"/>
                <ParticipantCategory age = "30">
                    <QualifierInfo>Adult</QualifierInfo>
                    <Price
                        Amount = "19.660"
                        CurrencyCode = "EUR"/>
                </ParticipantCategory>
            </Pricing>
            <TPA_Extensions>
                <Issue Mandatory = "true">
                    <Tickets>
                        <Ticket idTicket = "15782" url = "http://93.90.21.40:8080/Janto_4TICK/GetHomeTicket?xmlDoc=%0d%0a%3cGetHomeTicket++%3e%0d%0a++%3cIdCookie%3e9999999787%3c%2fIdCookie%3e%0d%0a++%3cUsuario+%2f%3e%0d%0a++%3cRefOperacion%3e15782%3c%2fRefOperacion%3e%0d%0a++%3cReimpresion%3eS%3c%2fReimpresion%3e%0d%0a%3c%2fGetHomeTicket%3e"/>
                    </Tickets>
                </Issue>
            </TPA_Extensions>
        </ReservationDetails>
    </OTA_TourActivityBookRS>



### Reservation RS Description




| **Element**				| **Number**	| **Type**	| **Description**				|
| ------------------------------------- | ------------- | ------------- | --------------------------------------------- |
| OTA_TourActivityBookRS		| 1      	|		| Root node.					|
| ReservationDetails   			| 0..1    	|		| Information about specific ticket.    	|
| ReservationDetails/BasicInfo		| 0..1    	|		| If need search by activity provider code.	|
| @Name                			| 0..1		| String	| Name of ticket.				|
| @TourActivityID      			| 0..1		| String	| Code of ticket.				|
| ReservationDetails/Confirmation	| 1      	|		| Contains information of the activity booked.	|
| @ID                  			| 1  		| String	| Activity booked identifier.			|
| @type                			| 1  		| String	| Activity booked type (Possible values: "PROVIDER").|
| ReservationDetails/Schedule		| 0..1    	|		| Information about dates range on which you can enjoy the activity. The same information that send in request. |
| ReservationDetails/Schedule/Detail	| 0..1    	|		| Information about specify dates on which you can enjoy the activity. |
| ReservationDetails/Schedule/Detail/OperationTimes | 0..1 |   		| Information about specify dates on which1 you can enjoy the activity. |
| ReservationDetails/Schedule/Detail/OperationTimes/OperationTime | 0..1 | | Information when activity starts.		|
| @Start               			| 0..1		| Date		| Start date activity.				|
| @End                 			| 0..1		| Date		| End date activity.				|
| ReservationDetails/PaymentInfo	| 0..1    	|		| Payment details that may be associated with an individual participant, a participant category and/or a group. |
| @Description         			| 0..1		| String	@ A description of the charge.			|
| Pricing/Summary      			| 0..1    	|		| Summary price for option, this element we return if OpenAvailability = false. |
| @Amount              			| 0..1		| Decimal	| Option price.					|
| @CurrencyCode        			| 0..1		| String	| Currency code (ISO 4217).			|
| Pricing/Summary/PricingType		| 0..1		| String	| Specifies type of the option price, if value = Other then is mandatory specify Extension type. |
| @Extension           			| 0..1		| String	| Specifies type of the option price.		|
| Pricing/ParticipantCategory		| 0..n		| String	| Specifies price and participant category.	|
| @age                 			| 0..1		| Integer	| Age of participant category.			|
| Pricing/ParticipantCategory/QualifierInfo | 0..1	| String	| Specifies participant type (Adult, Children or Babie). If value = Other then then is mandatory specify Extension provider type. |
| @Extension           			| 0..1		| String	| Specifies provider code of participant category. |
| Pricing/ParticipantCategory/Price	| 1      	|		| Specific price for each participantCategory.	|
| @Amount              			| 1  		| String	| ParticipantCategory price.			|
| @CurrencyCode        			| 0..1 		| String	| Currency code (ISO 4217).			|
| TPA_Extensions/Issue			| 0..1    	|		| Contains information about ticket printing.	|
| @Mandatory           			| 0..1		| Boolean	| Specifies if the ticket should be printed by the client. |
| TPA_Extensions/Issue/Tickets		| 0..1    	|		| Contains information about the tickets.	|
| TPA_Extensions/Issue/Tickets/Ticket	| 1..n    	|		| List of tickets.				|
| @idTicket            			| 1  		| String	| Ticket identifier. This ticket can be a one person ticket or an operation (Set of one person tickets for a same activity). |
| @url                 			| 1  		| String 	| Url containing the ticket bonus.		|
| TPA_Extensions/Attributes		| 0..1    	|		| Attributes that we need send between calls.	|
| TPA_Extensions/Attributes/Attribute	| 0..n    	|		| Attributes that we need send between calls.	|


