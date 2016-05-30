---
title: Avail
keywords: activities, data structure, avail
sidebar: mydoc_sidebar
permalink: /docs/activities/DSF/avail
---



### Method Goals


This method aims to return all the available options for a given date
and search type. It does not filter different classes, times or fares.
It will always return all results returned by the supplier between
specific date range.



### Request Format


It is mandatory to pass a date range and a search type. Depends if
OpenAvailability is true or false (this attribute return in
StaticConfiguration call), you need specify passengers.

**Search types**

-   RegionCode : Specify a provider region code where you want to
    perform availability.
-   Activity ID : Specify a provider activity code of the desired
    activity.
-   Category/Code : Specify a provider category code of the desired
    activity category.



### Response Format


The response contains information of each activity that provider return.
Depends if OpenAvailability is true or false (this attribute return in
StaticConfiguration call).

**OpenAvailability**

-   OpenAvailability = false: Need specify passangers in avail request.
    In response, provider return price of option that you specify.
-   OpenAvailability = true: Not neccesary specify passangers in avail
    request. In this case provider return all possible participant types
    that can provide, and you can choose the participants types that you
    are interested.



### AvailRQ Example



~~~xml
    <OTA_TourActivityAvailRQ>
        xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance"
        xmlns:xsd = "http://www.w3.org/2001/XMLSchema"
        PrimaryLangID = "es">
        <TourActivity>
            <!--Search by activity provider code-->
            <BasicInfo TourActivityID = "PRUEBAPORESPECT1"/>
            <Schedule StartPeriod = "2014-03-20T00:00:00" EndPeriod = "2014-03-21T00:00:00"/>
            <!--Search by provider category code-->
            <CategoryAndTypes>
                <Category Code = "1" Extension = "Other"/>
            </CategoryAndTypes>
            <Schedule StartPeriod = "2014-03-20T00:00:00" EndPeriod = "2014-03-21T00:00:00"/>
            <!--Search by provider region code-->
            <Location>
                <Region RegionCode = "PMI"/>
            </Location>
            <!--Mandatory specify if OpenAvailability = false-->
            <ParticipantCount Age = "30" Quantity = "1"/>
        </TourActivity>
    </OTA_TourActivityAvailRQ>
~~~


### AvailRQ Description




| **Element**				| **Number**	| **Type**	| **Description**				|
| ------------------------------------- | ------------- | ------------- | --------------------------------------------- |
| OTA_TourActivityAvailRQ		| 1         	|		| Root node.					|
| @PrimaryLangID      			| 1   		| String	| Language code (ISO 3166-1 alpha-2) format.	|
| TourActivityInfo    			| 0..n      	|		| Information about specific ticket.		|
| TourActivityInfo/BasicInfo		| 0..1      	|		| If need search by activity provider code.	|
| @Name               			| 0..1		| String	| Name of ticket.				|
| @TourActivityID     			| 0..1		| String	| Code of ticket, mandatory if need search  by activity provider code. |
| TourActivityInfo/Schedule		| 1         	|		| Information about dates range on which you can enjoy the activity. |
| TourActivityInfo/Schedule/Summary	| 1         	|		| Information dates range that you apply availability. |
| @Start              			| 1   		| Date		| Start date that you apply availability.	|
| @End                			| 1   		| Date 		| End date that you apply availability.		|
| TourActivityInfo/CategoryAndType/Category | 0..1      |		| Category of Ticket.				|
| @Code               			| 0..1		| String	| A category code from a predefined list, if Extension = "Other" then will be provider code. |
| @Extension          			| 0..1		| String	| Enter a category here if you have selected "Other" from the pre-defined list. |
| TourActivityInfo/CategoryAndType	| 0..1      	|		| Category of Ticket.				|
| TourActivityInfo/CategoryAndType/Category | 0..1      |		| Category of Ticket.				|
| @Code               			| 0..1		| String	| A category code from a predefined list, if Extension = "Other" then will be provider code. |
| @Extension          			| 0..1      	|		| Enter a category here if you have selected "Other" from the pre-defined list. |
| Location            			| 0..1      	|		| The location of the tour/ activity.		|
| Location/Region     			| 0..1      	|		| Describes regional information.		|
| @RegionCode         			| 0..1		| String	| Specifies a region code.  			|
| @RegionName         			| 0..1		| String	| Specifies the region name.			|
| ParticipantCount    			| 0..n      	|		| Information about participant type, specifying age for each participant. |
| @Age                			| 1   		| Integer	| Age of participant.				|
| @Quantity           			| 1   		| Integer	| Number of participant with same age.		|



### AvailRS Example



~~~xml
    <OTA_TourActivityAvailRS xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd = "http://www.w3.org/2001/XMLSchema">
        <!--OpenAvailability = false -->
        <TourActivityInfo>
            <BasicInfo Name = "Palma Aquarium" TourActivityID = "000200515"/>
            <Schedule>
                <Summary Start = "2014-03-20T00:00:00" End = "2014-03-21T00:00:00"/>
                <Detail>
                    <OperationTimes>
                        <OperationTime Start = "2014-03-20T00:00:00" End = "2014-03-20T00:00:00"/>
                    </OperationTimes>
                    <!-- Attributes required to pass between calls or information necessary for the client-->
                    <TPA_Extensions>
                        <Attributes>
                            <Attribute key = "availToken" value = "BpvkqOrfqU6ZpOqiJ0k21g=="/>
                            <Attribute key = "modalityCode" value = "0#8"/>
                            <Attribute key = "dateFrom" value = "20140320"/>
                            <Attribute key = "dateTo" value = "20140320"/>
                            <Attribute key = "limitAdult" value = "12"/>
                            <Attribute key = "modeCode" value = "P"/>
                        </Attributes>
                    </TPA_Extensions>
                </Detail>
                <Detail>
                    <OperationTimes>
                        <OperationTime Start = "2014-03-21T00:00:00" End = "2014-03-21T00:00:00"/>
                    </OperationTimes>
                    <TPA_Extensions>
                        <Attributes>
                            <Attribute key = "availToken" value = "BpvkqOrfqU6ZpOqiJ0k21g=="/>
                            <Attribute key = "modalityCode" value = "0#8"/>
                            <Attribute key = "dateFrom" value = "20140321"/>
                            <Attribute key = "dateTo" value = "20140321"/>
                            <Attribute key = "limitAdult" value = "12"/>
                            <Attribute key = "modeCode" value = "P"/>
                        </Attributes>
                    </TPA_Extensions>
                </Detail>
            </Schedule>
            <Location>
                <Region RegionCode = "PMI"/>
            </Location>
            <Description>
                <ShortDescription>Descubre los secretos mejor guardados del mundo marino recorriendo los rincones de este maravilloso parque marino con ms de 8.000 animales de 700 especies diferentes y ms de 5 millones de litros de agua salada. Recorre los 900 metros que forman el itinerario del parque y descubre los espectaculares secretos que esconde en su interior. Adems podrs disfrutar de un sinfn de actividades que te permitirn combinar un amplio conocimiento del fondo del mar.</ShortDescription>
                <Multimedia>
                    <MultimediaDescription>
                        <ImageItems>
                            <ImageItem>
                                <ImageFormat>
                                    <URL>http://www.hotelbeds.com/giata/extras/big/ds/11479/11479_4.jpg</URL>
                                </ImageFormat>
                            </ImageItem>
                            <ImageItem>
                                <ImageFormat>
                                    <URL>http://www.hotelbeds.com/giata/extras/big/ds/11479/11479_1.jpg</URL>
                                </ImageFormat>
                            </ImageItem>
                            <ImageItem>
                                <ImageFormat>
                                    <URL>http://www.hotelbeds.com/giata/extras/big/ds/11479/11479_2.jpg</URL>
                                </ImageFormat>
                            </ImageItem>
                            <ImageItem>
                                <ImageFormat>
                                    <URL>http://www.hotelbeds.com/giata/extras/big/ds/11479/11479_3.jpg</URL>
                                </ImageFormat>
                            </ImageItem>
                            <ImageItem>
                                <ImageFormat>
                                    <URL>http://www.hotelbeds.com/giata/extras/big/ds/11479/11479_4.jpg</URL>
                                </ImageFormat>
                            </ImageItem>
                            <ImageItem>
                                <ImageFormat>
                                    <URL>http://www.hotelbeds.com/giata/extras/big/ds/11479/11479_5.jpg</URL>
                                </ImageFormat>
                            </ImageItem>
                            <ImageItem>
                                <ImageFormat>
                                    <URL>http://www.hotelbeds.com/giata/extras/big/ds/11479/11479_6.jpg</URL>
                                </ImageFormat>
                            </ImageItem>
                        </ImageItems>
                    </MultimediaDescription>
                </Multimedia>
            </Description>
            <Pricing>
                <Summary Amount = "19.661" CurrencyCode = "EUR">
                    <PricingType Extension = "PerPersonPerDay">Other_</PricingType>
                </Summary>
                <ParticipantCategory age = "30">
                    <QualifierInfo>Adult</QualifierInfo>
                    <Price
                        Amount = "19.661"
                        CurrencyCode = "EUR"/>
                </ParticipantCategory>
            </Pricing>
        </TourActivityInfo>
        <!--OpenAvailability = true-->
        <TourActivityInfo>
            <BasicInfo Name = "La Prueba Final (EVENTO DE PRUEBA)" TourActivityID = "PRUEBAPORESPECT1"/>
            <Schedule>
                <Summary Start = "2014-02-26T00:00:00" End = "2014-02-27T00:00:00"/>
                <Detail>
                    <OperationTimes>
                        <OperationTime Start = "2014-02-26T20:00:00"/>
                    </OperationTimes>
                </Detail>
            </Schedule>
            <CategoryAndType>
                <Category Code = "1" Extension = "Other"/>
            </CategoryAndType>
            <Location>
                <Region RegionCode = "20" RegionName = "Madrid"/>
                <Address>
                    <AddressLine>-</AddressLine>
                    <PostalCode/>
                    <County>ESPAA</County>
                </Address>
            </Location>
            <Pricing>
                <ParticipantCategory>
                    <QualifierInfo Extension = "27#pr1">Other</QualifierInfo>
                    <Price
                        Amount = "5"
                        CurrencyCode = "EUR"/>
                    <!-- Attributes required to pass between calls and information necessary for the client-->
                    <TPA_Extensions>
                        <Seat>
                            <Level id = "N1" description = "Nivel 1"/>
                            <Area id = "A1" description = "Area 1"/>
                            <Zone id = "A1_z1" description = "Parte Central"/>
                            <Sector id = "A1_z1_b1" description = "Delantera Derecha"/>
                            <UrlSitting>http://93.90.21.41/Janto/traveltino/public/janto/main.php?Nivel=Detalle_1_Sesion&Idioma=es&idSesion=0000000000000211&idZona=A1_z1&idBloque=A1_z1_b1&idConcesion=XXX&numEntradas=1&modo=IFRAME</UrlSitting>
                        </Seat>
                        <DynamicToken/>
                        <Issue Mandatory = "false"/>
                        <Attributes>
                            <Attribute key = "idSesion" value = "0000000000000211"/>
                        </Attributes>
                    </TPA_Extensions>
                </ParticipantCategory>
                <ParticipantCategory>
                    <QualifierInfo Extension = "27#pr2">Other</QualifierInfo>
                    <Price
                        Amount = "2"
                        CurrencyCode = "EUR"/>
                    <TPA_Extensions>
                        <Seat>
                            <Level id = "N1" description = "Nivel 1"/>
                            <Area id = "A1" description = "Area 1"/>
                            <Zone id = "A1_z1" description = "Parte Central"/>
                            <Sector id = "A1_z1_b1" description = "Delantera Derecha"/>
                            <UrlSitting>http://93.90.21.41/Janto/traveltino/public/janto/main.php?Nivel=Detalle_1_Sesion&Idioma=es&idSesion=0000000000000211&idZona=A1_z1&idBloque=A1_z1_b1&idConcesion=XXX&numEntradas=1&modo=IFRAME</UrlSitting>
                        </Seat>
                        <DynamicToken/>
                        <Issue Mandatory = "false"/>
                        <Attributes>
                            <Attribute key = "idSesion" value = "0000000000000211"/>
                        </Attributes>
                    </TPA_Extensions>
                </ParticipantCategory>
            </Pricing>
        </TourActivityInfo>
                    .
                    .
    </OTA_TourActivityAvailRS>
~~~


### AvailRS Description




| **Element**				| **Number**	| **Type**	| **Description**				|
| ------------------------------------- | ------------- | ------------- | --------------------------------------------- |
| OTA TourActivityAvailRS  		| 1      	|		| Root node.					|
| TourActivityInfo         		| 0..n    	|		| Information about specific ticket.		|
| TourActivityInfo/BasicInfo		| 0..1    	|		| Basic Information of ticket.			|
| @Name                   		| 0..1		| String	| Name of ticket.				|
| @TourActivityID          		| 0..1		| String	| Code of ticket.				|
| TourActivityInfo/Schedule		| 1      	|		| Information about dates range on which you can enjoy the activity. |
| TourActivityInfo/Schedule/Summary	| 1      	|		| Information dates range that you apply availability. |
| @Start                   		| 1  		| Date		| Start date that you apply availability. 	|
| @End                     		| 1  		| Date		| End date that you apply availability.		|
| TourActivityInfo/Schedule/Detail	| 0..1    	|		| Information when activity starts and attributes that we need send between calls. |
| TourActivityInfo/Schedule/Detail/OperationTimes | 0..1 |		| Information when activity starts.		|
| TourActivityInfo/Schedule/Detail/OperationTimes/OperationTime | 0..1 || Information when activity starts.		|
| @Start                   		| 0..1		| Date		| Start date activity.				|
| @End                     		| 0..1		| Date		| End date activity. 				|
| TourActivityInfo/Schedule/Detail/TPA_Extensions | 0..1 |		| Necessary information that we need send between calls. |
| TourActivityInfo/Schedule/Detail/TPA_Extensions/Attributes | 0..1 |	| Attributes that we need send between calls.	|
| TourActivityInfo/Schedule/Detail/TPA_Extensions/Attributes/Attribute | 0..n || Attributes that we need send between calls.|
| TourActivityInfo/CategoryAndType	| 0..1    	|		| Category of Ticket.				|
| TourActivityInfo/CategoryAndType/Category | 0..1    	|		| Category of Ticket.				|
| @Code                    		| 0..1		| String	| A category code from a predefined list, if Extension = "Other" then will be provider code. |
| @Extension               		| 0..1		| String	| Enter a category here if you have selected "Other" from the pre-defined list. |
| Location                 		| 1      	|		| The location of the tour/ activity.		|
| Location/Region          		| 1      	|		| Describes regional information.		|
| @RegionCode              		| 1  		| String	| Specifies a region code.			|
| @RegionName              		| 1  		| String	| Specifies the region name.			|
| Location/Address         		| 0..1    	|		| Identifies the physical address of the tour departure and/or activity location. |
| Location/Address/AddressLine		| 0..1		| String	| These lines will contain free form address details.|
| Location/Address/PostalCode		| 0..1		| String	| Post Office Code number.			|
| Location/Address/County  		| 0..1		| String	| County or Region Name.			|
| Description              		| 0..1    	|		| Images and descriptions of the activity.	|
| Description/ShortDescription		| 0..1		| String	| Short description of the activity.		|
| Description/Multimedia   		| 0..1    	|		| Information and url images. 			|
| Description/Multimedia/MultimediaDescription | 0..1   | 		| Information and url images.			|
| Description/Multimedia/MultimediaDescription/ImageItems | 0..1 |   	| Information and url images.			|
| Description/Multimedia/MultimediaDescription/ImageItems/ImageItem | 0..n || Information for each image.		|
| Description/Multimedia/MultimediaDescription/ImageItems/ImageItem/ImageFormat | 0..1 || Url image.			|
| Description/Multimedia/MultimediaDescription/ImageItems/ImageItem/ImageFormat/URL | 0..1 | String | Access to image url.|
| Pricing                  		| 1      	|		| Price for option if OpenAvailability = false and price for each  participantCategory if OpenAvailability = true. |
| Pricing/Summary          		| 0..1    	|		| Summary price for option, this element we return if OpenAvailability = false. |
| @Amount                  		| 0..1		| Decimal	| Option price.					|
| @CurrencyCode            		| 0..1		| String	| Currency code (ISO 4217).			|
| Pricing/Summary/PricingType		| 0..1		| String	| Specifies type of the option price, if value = Other then is mandatory specify Extension type. |
| @Extension               		| 0..1		| String	| Specifies type of the option price.		|
| Pricing/ParticipantCategory		| 0..n		| String	| Specifies price and participant category.	|
| @age                     		| 0..1		| Integer	| Age of participant category.			|
| Pricing/ParticipantCategory/QualifierInfo | 0..1	| String	| Specifies participant type (Adult, Children or Babie). If value = Other then then is mandatory specify Extension provider type. |
| @Extension               		| 0..1		| String	| Specifies provider code of participant category. |
| Pricing/ParticipantCategory/Price	| 1      	|		| Specific price for each participantCategory.	|
| @Amount                  		| 1  		| String	| ParticipantCategory price.			|
| @CurrencyCode            		| 0..1		| String	| Currency code (ISO 4217).			|
| Pricing/ParticipantCategory/TPA_Extensions | 0..1    	|		| Necessary information that we need send between calls. |
| Pricing/ParticipantCategory/TPA_Extensions/Seat | 0..1 |		| Information about location of seat.		|
| Pricing/ParticipantCategory/TPA_Extensions/Level | 0..1 |		| Information about level/floor of seat.	|
| Pricing/ParticipantCategory/TPA_Extensions/Area | 0..1 |   		| Area where the site is located.		|
| Pricing/ParticipantCategory/TPA_Extensions/Zone | 0..1 |    		| Zone where the site is located.		|
| Pricing/ParticipantCategory/TPA_Extensions/Sector | 0..1 |    	| Sector where the site is located.		|
| Pricing/ParticipantCategory/TPA_Extensions/UrlSitting | 0..1 |    	| Specify the interface provider access where client can choose seat. |
| @id                      		| 0..1		| String	| Provider code about location of seat.		|
| @description             		| 0..1		| String	| Description about location of seat.		|
| Pricing/ParticipantCategory/TPA_Extensions/DynamicToken | 0..1 | String | If openAvailability is true, dynamicToken will be Nothing/Empty. | 
| Pricing/ParticipantCategory/TPA_Extensions/Issue | 0..1 |   		| Contains information about ticket printing.	|
| @Mandatory               		| 0..1		| Boolean	| Specifies if the ticket should be printed by the client. |
| Pricing/ParticipantCategory/TPA_Extensions/Attributes | 0..1 |   	| Attributes that we need send between calls.	|
| Pricing/ParticipantCategory/TPA_Extensions/Attributes/Attribute | 0..n | | Attributes that we need send between calls. |


