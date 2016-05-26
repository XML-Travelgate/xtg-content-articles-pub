---
title: DescriptiveInfoExtended (In development)
keywords: hotel, data structure, descriptive, descriptive info, extended
sidebar: mydoc_sidebar
permalink: /developer-documentation/hotel/DSF/DescriptiveInfoExtended
---



### Method Goals


This method returns all the hotel information from the provider.

It allows you to map each hotel from the provider with your own
criteria.

With the combination of contextItem_ plus data_ you will have the
information (extracted from provider's documentation hierachy / fields
descriptions ) required to do it.



### Request Format


In addition to the hotel code, you can set language filters.

To define language filters fill LanguageCode element with *Culture* or
*No Culture* value:

-  *Culture (xx\_YY) :* Reponse will return only *values* /
 *text* with the specified language_culture.

-  *No Culture (xx) :* Response will return *values* / *text*
 with all cultures available for the language sent.

i.e. en could return en _GB and en _US

*For setting filters, recommendation is first call request without
filters to see which languages are available by the provider*



### Remarks


The maximum time before the connection gets closed, is of **180000**
milliseconds.



### DescriptiveInfoExtendedRQ Example


    <DescriptiveInfoExtendedRQ>
        <timeoutMilliseconds>180000</timeoutMilliseconds>
        <Hotel>
            <Code>343229</Code>
        </Hotel>
        <Filters>
            <LanguageCodes>
                <LanguageCode>es_ES</LanguageCode>
                <LanguageCode>en_US</LanguageCode>
            </LanguageCodes>
        </Filters>
    </DescriptiveInfoExtendedRQ>



### DescriptiveInfoExtendedRQ Description




| **Element**     			| **Number**	| **Type**	| **Description**				|
| ------------------------------------- | ------------- | ------------- | --------------------------------------------- |
| DescriptiveInfoExtendedRQ 		| 1   		|	        | Root node.					|
| DescriptiveInfoExtendedRQ/Hotel	| 1 		| String	| Hotel requested. 				|
| DescriptiveInfoExtendedRQ/Filters 	| 0..1  	| Filters  	| Filters. 					|
| DescriptiveInfoExtendedRQ/Filters/LanguageCodes | 0..1| LanguageCodes | LanguageCodes.				|
| LanguageCodes/LanguageCode 		| 1..n  	| String	| LanguageCode. 				|



### DescriptiveInfoExtendedRS Example


~~~

{
 "hotel" : {
        "codigo" : "343229",
        "codigosAlternativos" : [
        ],
        "nombre" : "Hotel Club Helios",
        "direccion" : "viale Lido",
        "poblacion" : "Noto",
        "codigoPostal" : "96107",
        "codigoPaisISO3166_1_alfa_2" : "IT",
        "destinoNivelMinimo" : {
            "codigo" : "IT#Noto",
            "nombre" : "Noto",
            "destinoHijo" : [
            ]
        },
        "destinoGeograficoMinimo" : {
            "codigo" : "IT#Noto",
            "nombre" : "Noto",
            "disponibilidad" : true,
            "destinoHijo" : [
            ]
        },
        "latitud" : "36.85142",
        "longitud" : "15.11054",
        "codigoCategoria" : "3.0",
        "numberOfRooms" : "130",
        "propertyType" : {
            "code" : "1",
            "text" : [
                {
                    "value" : "Hotel"
                }
            ]
        },
         "hotelAttributes" : [
            {
                "context" : [
                    {
                        "contextItem" : [
                            {
                                "id" : "HotelSummary",
                                "parentRefId" : "",
                                "Schema" : "Null",
                                "text" : [
                                    {
                                        "languageCode" : "en",
                                        "name" : "HotelSummary",
                                        "description" : "Summary elements for the property returned"
                                    },
                                    {
                                        "languageCode" : "pt",
                                        "name" : "HotelSummary",
                                        "description" : "Elementos de resumo do estabelecimento retornado"
                                    },
                                    {
                                        "languageCode" : "es",
                                        "name" : "HotelSummary",
                                        "description" : "Los elementos de resumen de la propiedad que se devuelve."
                                    }
                                ]
                            }
                        ]
                    }
                ],
                "data" : {
                    "id" : "HotelSummary#highRate",
                    "type" : "eNumeric",
                    "value" : [
                        {
                            "value" : "626.7603"
                        }
                    ],
                    "text" : [
                        {
                            "languageCode" : "en",
                            "name" : "highRate",
                            "description" : "Highest rate returned by the hotel in recent queries. This is a statistical figure and not necessarily a rate for current availability."
                        },
                        {
                            "languageCode" : "pt",
                            "name" : "highRate",
                            "description" : "Menor tarifa retornada pelo hotel em consultas recentes. Trata-se de um número estatístico e não é necessariamente uma tarifa para a disponibilidade atual."
                        },
                        {
                            "languageCode" : "es",
                            "name" : "highRate",
                            "description" : "La tarifa más alta que devuelve el hotel en consultas recientes. Se trata de una cifra estadística y no necesariamente de la tarifa para la disponibilidad actual."
                        }
                    ]
                }
            }
],
    "hotelDescriptions" : {
        "description" : {
                "description" : [
                    {
                        "context" : [
                            {
                                "contextItem" : [
                                    {
                                        "id" : "HotelSummary#locationDescription",
                                        "parentRefId" : "t:EXP:HotelSummary",
                                        "Schema" : "Null",
                                        "text" : [
                                            {
                                                "languageCode" : "en",
                                                "name" : "locationDescription",
                                                "description" : "General location as entered by the property, e.g. \"Near Pike Place Market\""
                                            },
                                            {
                                                "languageCode" : "pt",
                                                "name" : "locationDescription",
                                                "description" : "Local geral inserido pelo estabelecimento (por exemplo, \"perto do mercado Pike Place\")"
                                            },
                                            {
                                                "languageCode" : "es",
                                                "name" : "locationDescription",
                                                "description" : "La propiedad introduce la ubicación general, por ejemplo, \"cerca del mercado Pike Place Market\"."
                                            }
                                        ]
                                    },
                                    {
                                        "id" : "HotelSummary",
                                        "parentRefId" : "",
                                        "Schema" : "Null",
                                        "text" : [
                                            {
                                                "languageCode" : "en",
                                                "name" : "HotelSummary",
                                                "description" : "Summary elements for the property returned"
                                            },
                                            {
                                                "languageCode" : "pt",
                                                "name" : "HotelSummary",
                                                "description" : "Elementos de resumo do estabelecimento retornado"
                                            },
                                            {
                                                "languageCode" : "es",
                                                "name" : "HotelSummary",
                                                "description" : "Los elementos de resumen de la propiedad que se devuelve."
                                            }
                                        ]
                                    }
                                ]
                            }
                        ],
                        "text" : [
                            {
                                "languageCode" : "en_US",
                                "value" : "Near Eloro Beach"
                            },
                            {
                                "languageCode" : "es_ES",
                                "value" : "A poca distancia de Playa Eloro"
                            }
                        ]
                    },
                ]
            }
        },
        "roomTypes" : {
            "roomType" : [
                {
                    "code" : "486225",
                    "typeId" : "581778",
                    "name" : {
                        "text" : [
                            {
                                "languageCode" : "en_US",
                                "value" : "Standard Room"
                            },
                            {
                                "languageCode" : "es_ES",
                                "value" : "Habitación estándar"
                            }
                        ]
                    },
                    "descriptions" : {
                        "description" : [
                            {
                                "context" : [
                                    {
                                        "contextItem" : [
                                            {
                                                "id" : "RoomType#descriptionLong",
                                                "parentRefId" : "t:EXP:RoomType",
                                                "Schema" : "Null",
                                                "text" : [
                                                    {
                                                        "languageCode" : "en",
                                                        "name" : "descriptionLong",
                                                        "description" : "Longer room description, if available."
                                                    },
                                                    {
                                                        "languageCode" : "pt",
                                                        "name" : "descriptionLong",
                                                        "description" : "Descrição do quarto mais longa, se disponível."
                                                    },
                                                    {
                                                        "languageCode" : "es",
                                                        "name" : "descriptionLong",
                                                        "description" : "La descripción más larga de la habitación, si se encuentra disponible."
                                                    }
                                                ]
                                            },
                                            {
                                                "id" : "RoomType",
                                                "parentRefId" : "t:EXP:RoomTypes",
                                                "Schema" : "Null",
                                                "text" : [
                                                    {
                                                        "languageCode" : "en",
                                                        "name" : "RoomType",
                                                        "description" : "Contains information for a single room type. Has attributes roomTypeId and roomCode. roomCode corresponds with the roomTypeCode element returned in the room and list responses."
                                                    },
                                                    {
                                                        "languageCode" : "pt",
                                                        "name" : "RoomType",
                                                        "description" : "Contém informações sobre um único tipo de quarto. Tem atributos roomTypeId, e roomCode. roomCode corresponde ao elemento roomTypeCode retornado nas respostas da lista e do quarto."
                                                    },
                                                    {
                                                        "languageCode" : "es",
                                                        "name" : "RoomType",
                                                        "description" : "Contiene información de un solo tipo de habitación. Tiene los atributos roomTypeId y roomCode. roomCode se corresponde con el elemento roomTypeCode que se devolvió en las respuestas de lista y habitación."
                                                    }
                                                ]
                                            },
                                            {
                                                "id" : "RoomTypes",
                                                "parentRefId" : "",
                                                "Schema" : "Null",
                                                "text" : [
                                                    {
                                                        "languageCode" : "en",
                                                        "name" : "RoomTypes",
                                                        "description" : "Contains array of available room type at the property. Has size attribute to indicate the number of results contained."
                                                    },
                                                    {
                                                        "languageCode" : "pt",
                                                        "name" : "RoomTypes",
                                                        "description" : "Contém matriz de tipo de quarto disponível no estabelecimento. Tem o atributo size para indicar o número de resultados contidos."
                                                    },
                                                    {
                                                        "languageCode" : "es",
                                                        "name" : "RoomTypes",
                                                        "description" : "Contiene la matriz del tipo de habitación disponible de la propiedad. Tiene el atributo size para indicar el número de resultados que se devuelven."
                                                    }
                                                ]
                                            }
                                        ]
                                    }
                                ],
                                "text" : [
                                    {
                                        "languageCode" : "en_US",
                                        "value" : "&amp;lt;strong&amp;gt;1 double bed or 1 twin bed or 2 twin beds or 3 twin beds&amp;lt;/strong&amp;gt;&amp;lt;br /&amp;gt; &amp;lt;b&amp;gt;Food &amp;amp; Drink&amp;lt;/b&amp;gt; - Refrigerator&amp;lt;br /&amp;gt;&amp;lt;b&amp;gt;Bathroom&amp;lt;/b&amp;gt; - Private bathroom and free toiletries&amp;lt;br /&amp;gt;"
                                    },
                                    {
                                        "languageCode" : "es_ES",
                                        "value" : "&amp;lt;strong&amp;gt;1 cama doble o 1 cama individual o 2 camas individuales o 3 camas individuales&amp;lt;/strong&amp;gt;&amp;lt;br /&amp;gt; &amp;lt;b&amp;gt;Comida y bebida:&amp;lt;/b&amp;gt; frigorífico&amp;lt;br /&amp;gt;&amp;lt;b&amp;gt;Cuarto de baño:&amp;lt;/b&amp;gt; baño privado con artículos de higiene personal gratuitos&amp;lt;br /&amp;gt;"
                                    }
                                ]
                            }
                        ]
                    },
                    "valuableAttribute" : [
                        {
                            "context" : [
                                {
                                    "contextItem" : [
                                        {
                                            "id" : "RoomType#roomAmenities#RoomAmenity",
                                            "parentRefId" : "t:EXP:RoomType#roomAmenities",
                                            "Schema" : "Null",
                                            "text" : [
                                                {
                                                    "languageCode" : "en",
                                                    "name" : "RoomAmenity",
                                                    "description" : "Contains description element for a single amenity. Has attribute amenityId. Refer to the AttributeList file for mapping amenityId values."
                                                },
                                                {
                                                    "languageCode" : "pt",
                                                    "name" : "RoomAmenity",
                                                    "description" : "Contém elemento de descrição para uma única comodidade. Tem o atributo amenityId. Consulte o arquivo AttributeList para ver o mapeamento de valores amenityId."
                                                },
                                                {
                                                    "languageCode" : "es",
                                                    "name" : "RoomAmenity",
                                                    "description" : "Contiene el elemento de descripción para un solo servicio. Tiene el atributo amenityId. Consulte el archivo AttributeList para la asignación de valores de amenityId."
                                                }
                                            ]
                                        },
                                        {
                                            "id" : "RoomType#roomAmenities",
                                            "parentRefId" : "t:EXP:RoomType",
                                            "Schema" : "Null",
                                            "text" : [
                                                {
                                                    "languageCode" : "en",
                                                    "name" : "roomAmenities",
                                                    "description" : "Contains all provided amenities for the room. Has size attribute to indicate the number of results contained."
                                                },
                                                {
                                                    "languageCode" : "pt",
                                                    "name" : "roomAmenities",
                                                    "description" : "Contém todas as comodidades fornecidas para o quarto. Tem o atributo size para indicar o número de resultados contidos."
                                                },
                                                {
                                                    "languageCode" : "es",
                                                    "name" : "roomAmenities",
                                                    "description" : "Contiene todos los servicios que se proporcionan para la habitación. Tiene el atributo size para indicar el número de resultados que se devuelven."
                                                }
                                            ]
                                        },
                                        {
                                            "id" : "RoomType",
                                            "parentRefId" : "t:EXP:RoomTypes",
                                            "Schema" : "Null",
                                            "text" : [
                                                {
                                                    "languageCode" : "en",
                                                    "name" : "RoomType",
                                                    "description" : "Contains information for a single room type. Has attributes roomTypeId and roomCode. roomCode corresponds with the roomTypeCode element returned in the room and list responses."
                                                },
                                                {
                                                    "languageCode" : "pt",
                                                    "name" : "RoomType",
                                                    "description" : "Contém informações sobre um único tipo de quarto. Tem atributos roomTypeId, e roomCode. roomCode corresponde ao elemento roomTypeCode retornado nas respostas da lista e do quarto."
                                                },
                                                {
                                                    "languageCode" : "es",
                                                    "name" : "RoomType",
                                                    "description" : "Contiene información de un solo tipo de habitación. Tiene los atributos roomTypeId y roomCode. roomCode se corresponde con el elemento roomTypeCode que se devolvió en las respuestas de lista y habitación."
                                                }
                                            ]
                                        },
                                        {
                                            "id" : "RoomTypes",
                                            "parentRefId" : "",
                                            "Schema" : "Null",
                                            "text" : [
                                                {
                                                    "languageCode" : "en",
                                                    "name" : "RoomTypes",
                                                    "description" : "Contains array of available room type at the property. Has size attribute to indicate the number of results contained."
                                                },
                                                {
                                                    "languageCode" : "pt",
                                                    "name" : "RoomTypes",
                                                    "description" : "Contém matriz de tipo de quarto disponível no estabelecimento. Tem o atributo size para indicar o número de resultados contidos."
                                                },
                                                {
                                                    "languageCode" : "es",
                                                    "name" : "RoomTypes",
                                                    "description" : "Contiene la matriz del tipo de habitación disponible de la propiedad. Tiene el atributo size para indicar el número de resultados que se devuelven."
                                                }
                                            ]
                                        }
                                    ]
                                }
                            ],
                            "data" : {
                                "code" : "26",
                                "id" : "AttributeList#26",
                                "type" : "eBoolean",
                                "value" : [
                                    {
                                        "value" : "True"
                                    }
                                ],
                                "text" : [
                                    {
                                        "languageCode" : "en_US",
                                        "name" : "Television",
                                        "description" : ""
                                    },
                                    {
                                        "languageCode" : "es_ES",
                                        "name" : "Televisión",
                                        "description" : ""
                                    }
                                ]
                            }
                        }
                    ]
                }
            ]
        },
        "medias" : {
            "media" : [
                {
                    "id" : "5529023",
                    "context" : [
                        {
                            "contextItem" : [
                                {
                                    "code" : "0",
                                    "id" : "HotelImage#Category#0",
                                    "parentRefId" : "t:EXP:HotelImage",
                                    "Schema" : "Null",
                                    "text" : [
                                        {
                                            "languageCode" : "en",
                                            "name" : "Unknown"
                                        }
                                    ]
                                },
                                {
                                    "id" : "HotelImage",
                                    "parentRefId" : "t:EXP:HotelImages",
                                    "Schema" : "Null",
                                    "text" : [
                                        {
                                            "languageCode" : "en",
                                            "name" : "HotelImage",
                                            "description" : "Contains elements for the URL and reference values for a single image."
                                        },
                                        {
                                            "languageCode" : "pt",
                                            "name" : "HotelImage",
                                            "description" : "Contém elementos relativos ao URL e a valores de referência para uma única imagem."
                                        },
                                        {
                                            "languageCode" : "es",
                                            "name" : "HotelImage",
                                            "description" : "Contiene elementos de los valores de referencia y URL de una sola imagen."
                                        }
                                    ]
                                },
                                {
                                    "id" : "HotelImages",
                                    "parentRefId" : "",
                                    "Schema" : "Null",
                                    "text" : [
                                        {
                                            "languageCode" : "en",
                                            "name" : "HotelImages",
                                            "description" : "Contains all property images available. Does not contain room-level photos. Has size attribute to indicate the number of results contained. Review  image categorizations for more specific details about the data returned."
                                        },
                                        {
                                            "languageCode" : "pt",
                                            "name" : "HotelImages",
                                            "description" : "Contém todas as imagens do estabelecimento disponíveis. Não contém fotos dos quartos. Tem o atributo size para indicar o número de resultados contidos.Revise as  classificações de imagens para obter detalhes mais específicos sobre os dados retornados."
                                        },
                                        {
                                            "languageCode" : "es",
                                            "name" : "HotelImages",
                                            "description" : "Contiene todas las imágenes de propiedades disponibles. No contiene fotos de nivel de habitaciones. Tiene el atributo size para indicar el número de resultados que se devuelven.Consulte  las categorizaciones de imágenes para obtener más detalles específicos acerca de los datos que se devuelven."
                                        }
                                    ]
                                }
                            ]
                        },
                        {
                            "contextItem" : [
                                {
                                    "code" : "0",
                                    "id" : "HotelImage#Type#0",
                                    "parentRefId" : "t:EXP:HotelImage",
                                    "Schema" : "Null",
                                    "text" : [
                                        {
                                            "languageCode" : "en",
                                            "name" : "Unknown"
                                        }
                                    ]
                                },
                                {
                                    "id" : "HotelImage",
                                    "parentRefId" : "t:EXP:HotelImages",
                                    "Schema" : "Null",
                                    "text" : [
                                        {
                                            "languageCode" : "en",
                                            "name" : "HotelImage",
                                            "description" : "Contains elements for the URL and reference values for a single image."
                                        },
                                        {
                                            "languageCode" : "pt",
                                            "name" : "HotelImage",
                                            "description" : "Contém elementos relativos ao URL e a valores de referência para uma única imagem."
                                        },
                                        {
                                            "languageCode" : "es",
                                            "name" : "HotelImage",
                                            "description" : "Contiene elementos de los valores de referencia y URL de una sola imagen."
                                        }
                                    ]
                                },
                                {
                                    "id" : "HotelImages",
                                    "parentRefId" : "",
                                    "Schema" : "Null",
                                    "text" : [
                                        {
                                            "languageCode" : "en",
                                            "name" : "HotelImages",
                                            "description" : "Contains all property images available. Does not contain room-level photos. Has size attribute to indicate the number of results contained. Review  image categorizations for more specific details about the data returned."
                                        },
                                        {
                                            "languageCode" : "pt",
                                            "name" : "HotelImages",
                                            "description" : "Contém todas as imagens do estabelecimento disponíveis. Não contém fotos dos quartos. Tem o atributo size para indicar o número de resultados contidos.Revise as  classificações de imagens para obter detalhes mais específicos sobre os dados retornados."
                                        },
                                        {
                                            "languageCode" : "es",
                                            "name" : "HotelImages",
                                            "description" : "Contiene todas las imágenes de propiedades disponibles. No contiene fotos de nivel de habitaciones. Tiene el atributo size para indicar el número de resultados que se devuelven.Consulte  las categorizaciones de imágenes para obtener más detalles específicos acerca de los datos que se devuelven."
                                        }
                                    ]
                                }
                            ]
                        }
                    ],
                    "valuableAttribute" : [
                        {
                            "context" : [
                                {
                                    "contextItem" : [
                                        {
                                            "id" : "HotelImage",
                                            "parentRefId" : "t:EXP:HotelImages",
                                            "Schema" : "Null",
                                            "text" : [
                                                {
                                                    "languageCode" : "en",
                                                    "name" : "HotelImage",
                                                    "description" : "Contains elements for the URL and reference values for a single image."
                                                },
                                                {
                                                    "languageCode" : "pt",
                                                    "name" : "HotelImage",
                                                    "description" : "Contém elementos relativos ao URL e a valores de referência para uma única imagem."
                                                },
                                                {
                                                    "languageCode" : "es",
                                                    "name" : "HotelImage",
                                                    "description" : "Contiene elementos de los valores de referencia y URL de una sola imagen."
                                                }
                                            ]
                                        },
                                        {
                                            "id" : "HotelImages",
                                            "parentRefId" : "",
                                            "Schema" : "Null",
                                            "text" : [
                                                {
                                                    "languageCode" : "en",
                                                    "name" : "HotelImages",
                                                    "description" : "Contains all property images available. Does not contain room-level photos. Has size attribute to indicate the number of results contained. Review  image categorizations for more specific details about the data returned."
                                                },
                                                {
                                                    "languageCode" : "pt",
                                                    "name" : "HotelImages",
                                                    "description" : "Contém todas as imagens do estabelecimento disponíveis. Não contém fotos dos quartos. Tem o atributo size para indicar o número de resultados contidos.Revise as  classificações de imagens para obter detalhes mais específicos sobre os dados retornados."
                                                },
                                                {
                                                    "languageCode" : "es",
                                                    "name" : "HotelImages",
                                                    "description" : "Contiene todas las imágenes de propiedades disponibles. No contiene fotos de nivel de habitaciones. Tiene el atributo size para indicar el número de resultados que se devuelven.Consulte  las categorizaciones de imágenes para obtener más detalles específicos acerca de los datos que se devuelven."
                                                }
                                            ]
                                        }
                                    ]
                                }
                            ],
                            "data" : {
                                "id" : "HotelImage#supplierId",
                                "type" : "eNumeric",
                                "value" : [
                                    {
                                        "value" : "13"
                                    }
                                ],
                                "text" : [
                                    {
                                        "languageCode" : "en",
                                        "name" : "supplierId",
                                        "description" : "Indicates the supplier of the image. Follows the same mapping as the Supplier element's ID attribute."
                                    },
                                    {
                                        "languageCode" : "pt",
                                        "name" : "supplierId",
                                        "description" : "Indica o fornecedor da imagem. Segue o mesmo mapeamento do atributo ID do elemento Supplier."
                                    },
                                    {
                                        "languageCode" : "es",
                                        "name" : "supplierId",
                                        "description" : "Indica el proveedor de la imagen. Sigue la misma asignación que la del atributo ID del elemento Supplier."
                                    }
                                ]
                            }
                        },
                        {
                            "context" : [
                                {
                                    "contextItem" : [
                                        {
                                            "id" : "HotelImage",
                                            "parentRefId" : "t:EXP:HotelImages",
                                            "Schema" : "Null",
                                            "text" : [
                                                {
                                                    "languageCode" : "en",
                                                    "name" : "HotelImage",
                                                    "description" : "Contains elements for the URL and reference values for a single image."
                                                },
                                                {
                                                    "languageCode" : "pt",
                                                    "name" : "HotelImage",
                                                    "description" : "Contém elementos relativos ao URL e a valores de referência para uma única imagem."
                                                },
                                                {
                                                    "languageCode" : "es",
                                                    "name" : "HotelImage",
                                                    "description" : "Contiene elementos de los valores de referencia y URL de una sola imagen."
                                                }
                                            ]
                                        },
                                        {
                                            "id" : "HotelImages",
                                            "parentRefId" : "",
                                            "Schema" : "Null",
                                            "text" : [
                                                {
                                                    "languageCode" : "en",
                                                    "name" : "HotelImages",
                                                    "description" : "Contains all property images available. Does not contain room-level photos. Has size attribute to indicate the number of results contained. Review  image categorizations for more specific details about the data returned."
                                                },
                                                {
                                                    "languageCode" : "pt",
                                                    "name" : "HotelImages",
                                                    "description" : "Contém todas as imagens do estabelecimento disponíveis. Não contém fotos dos quartos. Tem o atributo size para indicar o número de resultados contidos.Revise as  classificações de imagens para obter detalhes mais específicos sobre os dados retornados."
                                                },
                                                {
                                                    "languageCode" : "es",
                                                    "name" : "HotelImages",
                                                    "description" : "Contiene todas las imágenes de propiedades disponibles. No contiene fotos de nivel de habitaciones. Tiene el atributo size para indicar el número de resultados que se devuelven.Consulte  las categorizaciones de imágenes para obtener más detalles específicos acerca de los datos que se devuelven."
                                                }
                                            ]
                                        }
                                    ]
                                }
                            ],
                            "data" : {
                                "id" : "HotelImage#byteSize",
                                "type" : "eNumeric",
                                "value" : [
                                    {
                                        "value" : "0"
                                    }
                                ],
                                "text" : [
                                    {
                                        "languageCode" : "en",
                                        "name" : "byteSize",
                                        "description" : "Size of the image, if available."
                                    },
                                    {
                                        "languageCode" : "pt",
                                        "name" : "byteSize",
                                        "description" : "Tamanho da imagem, se disponível."
                                    },
                                    {
                                        "languageCode" : "es",
                                        "name" : "byteSize",
                                        "description" : "El tamaño de la imagen, si se encuentra disponible."
                                    }
                                ]
                            }
                        }
                    ],
                    "description" : {
                        "context" : [
                            {
                                "contextItem" : [
                                    {
                                        "id" : "HotelImage#caption",
                                        "parentRefId" : "t:EXP:HotelImage",
                                        "Schema" : "Null",
                                        "text" : [
                                            {
                                                "languageCode" : "en",
                                                "name" : "caption",
                                                "description" : "Description for the image"
                                            },
                                            {
                                                "languageCode" : "pt",
                                                "name" : "caption",
                                                "description" : "Descrição da imagem."
                                            },
                                            {
                                                "languageCode" : "es",
                                                "name" : "caption",
                                                "description" : "La descripción de la imagen."
                                            }
                                        ]
                                    },
                                    {
                                        "id" : "HotelImage",
                                        "parentRefId" : "t:EXP:HotelImages",
                                        "Schema" : "Null",
                                        "text" : [
                                            {
                                                "languageCode" : "en",
                                                "name" : "HotelImage",
                                                "description" : "Contains elements for the URL and reference values for a single image."
                                            },
                                            {
                                                "languageCode" : "pt",
                                                "name" : "HotelImage",
                                                "description" : "Contém elementos relativos ao URL e a valores de referência para uma única imagem."
                                            },
                                            {
                                                "languageCode" : "es",
                                                "name" : "HotelImage",
                                                "description" : "Contiene elementos de los valores de referencia y URL de una sola imagen."
                                            }
                                        ]
                                    },
                                    {
                                        "id" : "HotelImages",
                                        "parentRefId" : "",
                                        "Schema" : "Null",
                                        "text" : [
                                            {
                                                "languageCode" : "en",
                                                "name" : "HotelImages",
                                                "description" : "Contains all property images available. Does not contain room-level photos. Has size attribute to indicate the number of results contained. Review  image categorizations for more specific details about the data returned."
                                            },
                                            {
                                                "languageCode" : "pt",
                                                "name" : "HotelImages",
                                                "description" : "Contém todas as imagens do estabelecimento disponíveis. Não contém fotos dos quartos. Tem o atributo size para indicar o número de resultados contidos.Revise as  classificações de imagens para obter detalhes mais específicos sobre os dados retornados."
                                            },
                                            {
                                                "languageCode" : "es",
                                                "name" : "HotelImages",
                                                "description" : "Contiene todas las imágenes de propiedades disponibles. No contiene fotos de nivel de habitaciones. Tiene el atributo size para indicar el número de resultados que se devuelven.Consulte  las categorizaciones de imágenes para obtener más detalles específicos acerca de los datos que se devuelven."
                                            }
                                        ]
                                    }
                                ]
                            }
                        ],
                        "text" : [
                            {
                                "languageCode" : "en_US",
                                "value" : "Aerial View"
                            },
                            {
                                "languageCode" : "es_ES",
                                "value" : "Aerial View"
                            }
                        ]
                    },
                    "photos" : {
                        "photo" : [
                            {
                                "witdh" : "350",
                                "height" : "350",
                                "thumbnail" : false,
                                "url" : "http://images.travelnow.com/hotels/4000000/3510000/3509600/3509541/3509541_21_b.jpg"
                            },
                            {
                                "thumbnail" : true,
                                "url" : "http://images.travelnow.com/hotels/4000000/3510000/3509600/3509541/3509541_21_t.jpg"
                            }
                        ]
                    }
                },

            ]
        }
    }
}
~~~



### DescriptiveInfoExtendedRS Description




| **Element**				| **Number**	| **Type**	| **Description**				|
| ------------------------------------- | ------------- | ------------- | --------------------------------------------- |
| DescriptiveInfoExtendedRS/Hotel 	| 0..n  	|         	| Root node. Hotel sheet.			|
| Code          			| 1     	| String  	| Code.	                                        |
| Name          			| 1     	| String  	| Name.                                         |
| Address       			| 1     	| String  	| Address.                                      |
| Town          			| 1     	| String  	| Town.                                         |
| ZipCode       			| 1     	| String  	| ZipCode.                                      |
| CountryISOCode 			| 1     	| String  	| CountryISOCode.                               |
| AvailDestination 			| 0..1  	|         	| Avail Destination ( will come only if it is attackable on availability, and the type is CTY). |
| @code         			| 1     	| String  	| Destination code.                             |
| @name         			| 1     	| String 	| Destination name.                             |
| GeographicDestination 		| 1     	|         	| Geographic Destination.                       |
| @code         			| 1     	| String  	| Destination code.                             |
| @name         			| 1     	| String  	| Destination name.                             |
| @avail        			| 1     	| Boolean 	| Indicates if it is attackable on availability.|
| Latitude      			| 1     	| String  	| Latitude.                                     |
| Longitude     			| 1     	| String  	| Longitude.                                    |
| Contact       			| 0..1  	|         	| Contact.                                      |
| Contact/Email 			| 1     	| String  	| Email.                                        |
| Contact/Telephone 			| 1     	| String  	| Telephone.                                    |
| Contact/Fax   			| 1     	| String  	| Fax.                                          |
| CategoryCode  			| 1     	| String  	| CategoryCode.                                 |
| BookingContact 			| 0..1  	|         	| Booking Contact.                              |
| BookingContact/Email 			| 1     	| String  	| Email.                                        |
| BookingContact/Telephone 		| 1     	| String  	| Telephone.                                    |
| BookingContact/Fax 			| 1     	| String  	| Fax.                                          |
| PropertyType  			|       	|         	|                                               |
| PropertyType/Code  			| 1     	| String  	| Poperty Code.                                 |
| PropertyType/Text  			| 1     	| Text    	| Property Text.                                |
| Chains        			| 1     	|         	|                                               |
| Chains/Code  				| 1     	| String  	| Chain Code.                                   |
| Chains/Name  				| 1     	| String  	| Chain Name.                                   |
| Chains/Data  				| 1     	| Data    	| Chain Data (more info in Hotel Summary)     |
| Languages     			| 0..1  	|         	|                                               |
| Languages/language      		| 1..n  	| String  	| Languages sopken at the hotel.                |
| PaymentOptions/Cards 			| 1     	|         	| List of cards allowed.                        |
| PaymentOptions/Cards/Card 		| 1..n  	|         	| Type card allowed.                            |
| @code>   				| 1     	| String  	| Code card (see in *Lists of Data* (VI,AX,BV,CA...)). |
| ExclusiveDeal 			| 0..1  	| Boolean 	| Indicates that a Hotel is an Exlusive Deal. The provider has formed partnerships with select Hotels in order to bring you list rates and superior prime availability in locations. The provider suggests with provide the best value. |
| NumberOfRooms 			| 0..1  	| Integer 	| Total rooms of hotel.   	                |
| HotelAttributes 			| 0..1  	|         	|                                               |
| HotelAttributes/Attributes 		| 0..1  	| Attributes 	|                                               |
| HotelDescriptions 			| 0..1  	| Descriptions 	|                                               |
| HotelDescriptions/Description 	| 1     	|         	|                                               |
| RoomTypes     			| 0..1  	|         	|                                               |
| RoomTypes/RoomType     		| 1..n  	|         	|                                               |
| RoomType/Code      			| 1     	| String  	| Room Code.                                    |
| RoomType/TypeId       		| 0..1  	| String  	| Room Type Id.                                 |
| RoomType/Name      			| 1     	|         	| Room Name.                                    |
| RoomType/Quantity      		| 1     	| Integer 	| Room Quantity.                                |
| RoomType/Descriptions      		| 1     	| Descriptions 	| Room Descriptions.                            |
| RoomType/RoomAttributes      		| 1     	| Attributes 	| Room Attributes.                              |
| RoomType/Medias      			| 1     	| Medias  	| Room Medias                                   |
| Medias        			| 1..n  	| Media   	|                                               |
| Attributes/Attribute    		| 1..n  	|         	| Attributes                                 	|
| Attribute/Context     		| 1..n  	|         	| ContextItem                                 	|
| Attribute/Data     			| 1     	|         	| Data                                    	|
| Description/Context   		| 1..n  	|         	| ContextItem                                 	|
| Description/text   			| 1..n  	|         	| Text                                        	|



### Response Format


The result returns the details of the hotel requested:

-   Hotel Summary ( standard for all providers ).
-   Hotel Attributes.
-   Hotel Descriptions.
-   Hotel Medias.
-   Room Summary ( standard for all providers ).
-   Room Attributes.
-   Room Descriptions.
-   Room Medias.



### Hotel Summary


Typified hotel information from the provider.

**Property Type** :

 -  This item contains code and text_ from the hotel category provider. (
   i.e. Hotel, ApartHotel, ...).

 - In the DescriptiveInfoExtendedRS Example_.

 -  Hotel has category Hotel which in providers side is specified by code
   1 ( Notice that no language code is sent, that means that the provider
   don't specify it ).

**Chains**

- Contains the chains infromation from the provider, it could be
 returned in 2 ways:
 
   1.  By code And Name.
 
   2.  By data.
 
- You can find code in data code field and value as a
 multiLanguage Value in data value field.



### Room Summary


Typified room information from the provider.

Room Name is multiLanguage text\_ field.

Name example:

~~~
{
    "name" : {
        "text" : [
            {
                "languageCode" : "en_US",
                "value" : "Standard Room"
            },
            {
                "languageCode" : "es_ES",
                "value" : "Habitación estándar"
            }
        ]
    }
}
~~~



### Attributes




| **Element**	| **Number**	| **Type**	| **Description**	|
| ------------- | ------------- | ------------- | --------------------- |
| Attribute 	|        	|           	|                       |
| @Context 	| 1..n   	| Context 	| contextItem           |
| @Data    	| 1      	| Data    	| data                  |

Attribute is defined as every element returned in the provider response
which is not either *Descriptions* or *Medias*.

Example:

~~~
{
    "hotelAttributes" : [
        {
            "context" : [
                {
                    "contextItem" : [
                        {
                            "id" : "HotelSummary",
                            "parentRefId" : "",
                            "Schema" : "Null",
                            "text" : [
                                {
                                    "languageCode" : "en",
                                    "name" : "HotelSummary",
                                    "description" : "Summary elements for the property returned"
                                },
                                {
                                    "languageCode" : "pt",
                                    "name" : "HotelSummary",
                                    "description" : "Elementos de resumo do estabelecimento retornado"
                                },
                                {
                                    "languageCode" : "es",
                                    "name" : "HotelSummary",
                                    "description" : "Los elementos de resumen de la propiedad que se devuelve."
                                }
                            ]
                        }
                    ]
                }
            ],
            "data" : {
                "id" : "HotelSummary#highRate",
                "type" : "eNumeric",
                "value" : [
                    {
                        "value" : "626.7603"
                    }
                ],
                "text" : [
                    {
                        "languageCode" : "en",
                        "name" : "highRate",
                        "description" : "Highest rate returned by the hotel in recent queries. This is a statistical figure and not necessarily a rate for current availability."
                    },
                    {
                        "languageCode" : "pt",
                        "name" : "highRate",
                        "description" : "Menor tarifa retornada pelo hotel em consultas recentes. Trata-se de um número estatístico e não é necessariamente uma tarifa para a disponibilidade atual."
                    },
                    {
                        "languageCode" : "es",
                        "name" : "highRate",
                        "description" : "La tarifa más alta que devuelve el hotel en consultas recientes. Se trata de una cifra estadística y no necesariamente de la tarifa para la disponibilidad actual."
                    }
                ]
            }
        }
    ]
}
~~~

-   Context explanation :

    There is 1 description with a contextItem child in HotelSummary (
    Summary elements for the property returned )

-   Data explanation (en) :

    Name "highRate" , description "Highest rate returned by the hotel
     in recent queries. This is a statistical figure and not
     necessarily a rate for current availability."
    
     Type: numeric
    
     Value: 626.7603



### Descriptions




| **Element**		| **Number**	| **Type**	| **Description**	|
| Description 		|        	|           	|                       |
| /Context 		| 1..n   	| Context 	| contextItem           |
| /Text    		| 1      	| Text    	| text                  |


Description is defined as every element returned in the provider
response which is a description (Hotel description, Room description,
Media description)

Example:

~~~
{
    "description" : [
        {
            "context" : [
                {
                    "contextItem" : [
                        {
                            "id" : "HotelSummary#locationDescription",
                            "parentRefId" : "t:EXP:HotelSummary",
                            "Schema" : "Null",
                            "text" : [
                                {
                                    "languageCode" : "en",
                                    "name" : "locationDescription",
                                    "description" : "General location as entered by the property, e.g. \"Near Pike Place Market\""
                                },
                                {
                                    "languageCode" : "pt",
                                    "name" : "locationDescription",
                                    "description" : "Local geral inserido pelo estabelecimento (por exemplo, \"perto do mercado Pike Place\")"
                                },
                                {
                                    "languageCode" : "es",
                                    "name" : "locationDescription",
                                    "description" : "La propiedad introduce la ubicación general, por ejemplo, \"cerca del mercado Pike Place Market\"."
                                }
                            ]
                        },
                        {
                            "id" : "HotelSummary",
                            "parentRefId" : "",
                            "Schema" : "Null",
                            "text" : [
                                {
                                    "languageCode" : "en",
                                    "name" : "HotelSummary",
                                    "description" : "Summary elements for the property returned"
                                },
                                {
                                    "languageCode" : "pt",
                                    "name" : "HotelSummary",
                                    "description" : "Elementos de resumo do estabelecimento retornado"
                                },
                                {
                                    "languageCode" : "es",
                                    "name" : "HotelSummary",
                                    "description" : "Los elementos de resumen de la propiedad que se devuelve."
                                }
                            ]
                        }
                    ]
                }
            ],
            "text" : [
                {
                    "languageCode" : "en_US",
                    "value" : "Near Eloro Beach"
                },
                {
                    "languageCode" : "es_ES",
                    "value" : "A poca distancia de Playa Eloro"
                }
            ]
        }
    ]
}
~~~

-   Context explanation :

     There is 1 description with a contextItem child
     locationDescription and description : General location as entered
     by the property, e.g. "Near Pike Place Market" which it's parent
     is HotelSummary ( Summary elements for the property returned )

-   Text explanation :

     The locationDescription has 2 text elements :
    
     en_US -\> Near Eloro Beach
    
     and
    
     es_ES -\> A poca distancia de Playa Eloro



### Medias




| **Element**			| **Number**	| **Type**	| **Description** 			|
| ----------------------------- | ------------- | ------------- | ------------------------------------- |
| Media       			|        	|          	|                                       |
| /id         			| 0..1   	| String 	| Media provider id                     |
| /Context    			| 1..n   	| Context 	| contextItem				|
| /ValuableAttribute 		| 0..n   	| Attributes 	| Attributes				|
| /Description 			| 0..1   	| Description 	| Descriptions                          |
| /Photos     			| 0..1   	|          	| Photos array                          |
| /Photos/photo 		| 1..n   	|          	|                                       |
| /Photo @width      		| 0..1   	| String 	| Photo width                           |
| /Photo @height     		| 0..1   	| String 	| Photo height                          |
| /Photo/Thumbnail 		| 1..n   	| Boolean 	| If true photo is specified as thumbnail |
| /Photos/Url 			| 1..n   	| String 	| Url                                   |
| /Videos     			| 0..1   	|          	| Videos array                          |
| /Videos/Video/Url 		| 1..n   	| String 	| Url                                   |
| /Others     			| 0..1   	|          	| Other Medias array                    |
| /Others/Other/Url 		| 1..n   	| String 	| Url                                   |



Example:

~~~
{
    "medias" : {
        "media" : [
            {
                "id" : "5529023",
                "context" : [
                    {
                        "contextItem" : [
                            {
                                "code" : "0",
                                "id" : "HotelImage#Category#0",
                                "parentRefId" : "t:EXP:HotelImage",
                                "Schema" : "Null",
                                "text" : [
                                    {
                                        "languageCode" : "en",
                                        "name" : "Unknown"
                                    }
                                ]
                            },
                            {
                                "id" : "HotelImage",
                                "parentRefId" : "t:EXP:HotelImages",
                                "Schema" : "Null",
                                "text" : [
                                    {
                                        "languageCode" : "en",
                                        "name" : "HotelImage",
                                        "description" : "Contains elements for the URL and reference values for a single image."
                                    },
                                    {
                                        "languageCode" : "pt",
                                        "name" : "HotelImage",
                                        "description" : "Contém elementos relativos ao URL e a valores de referência para uma única imagem."
                                    },
                                    {
                                        "languageCode" : "es",
                                        "name" : "HotelImage",
                                        "description" : "Contiene elementos de los valores de referencia y URL de una sola imagen."
                                    }
                                ]
                            },
                            {
                                "id" : "HotelImages",
                                "parentRefId" : "",
                                "Schema" : "Null",
                                "text" : [
                                    {
                                        "languageCode" : "en",
                                        "name" : "HotelImages",
                                        "description" : "Contains all property images available. Does not contain room-level photos. Has size attribute to indicate the number of results contained. Review  image categorizations for more specific details about the data returned."
                                    },
                                    {
                                        "languageCode" : "pt",
                                        "name" : "HotelImages",
                                        "description" : "Contém todas as imagens do estabelecimento disponíveis. Não contém fotos dos quartos. Tem o atributo size para indicar o número de resultados contidos.Revise as  classificações de imagens para obter detalhes mais específicos sobre os dados retornados."
                                    },
                                    {
                                        "languageCode" : "es",
                                        "name" : "HotelImages",
                                        "description" : "Contiene todas las imágenes de propiedades disponibles. No contiene fotos de nivel de habitaciones. Tiene el atributo size para indicar el número de resultados que se devuelven.Consulte  las categorizaciones de imágenes para obtener más detalles específicos acerca de los datos que se devuelven."
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "contextItem" : [
                            {
                                "code" : "0",
                                "id" : "HotelImage#Type#0",
                                "parentRefId" : "t:EXP:HotelImage",
                                "Schema" : "Null",
                                "text" : [
                                    {
                                        "languageCode" : "en",
                                        "name" : "Unknown"
                                    }
                                ]
                            },
                            {
                                "id" : "HotelImage",
                                "parentRefId" : "t:EXP:HotelImages",
                                "Schema" : "Null",
                                "text" : [
                                    {
                                        "languageCode" : "en",
                                        "name" : "HotelImage",
                                        "description" : "Contains elements for the URL and reference values for a single image."
                                    },
                                    {
                                        "languageCode" : "pt",
                                        "name" : "HotelImage",
                                        "description" : "Contém elementos relativos ao URL e a valores de referência para uma única imagem."
                                    },
                                    {
                                        "languageCode" : "es",
                                        "name" : "HotelImage",
                                        "description" : "Contiene elementos de los valores de referencia y URL de una sola imagen."
                                    }
                                ]
                            },
                            {
                                "id" : "HotelImages",
                                "parentRefId" : "",
                                "Schema" : "Null",
                                "text" : [
                                    {
                                        "languageCode" : "en",
                                        "name" : "HotelImages",
                                        "description" : "Contains all property images available. Does not contain room-level photos. Has size attribute to indicate the number of results contained. Review  image categorizations for more specific details about the data returned."
                                    },
                                    {
                                        "languageCode" : "pt",
                                        "name" : "HotelImages",
                                        "description" : "Contém todas as imagens do estabelecimento disponíveis. Não contém fotos dos quartos. Tem o atributo size para indicar o número de resultados contidos.Revise as  classificações de imagens para obter detalhes mais específicos sobre os dados retornados."
                                    },
                                    {
                                        "languageCode" : "es",
                                        "name" : "HotelImages",
                                        "description" : "Contiene todas las imágenes de propiedades disponibles. No contiene fotos de nivel de habitaciones. Tiene el atributo size para indicar el número de resultados que se devuelven.Consulte  las categorizaciones de imágenes para obtener más detalles específicos acerca de los datos que se devuelven."
                                    }
                                ]
                            }
                        ]
                    }
                ],
                "valuableAttribute" : [
                    {
                        "context" : [
                            {
                                "contextItem" : [
                                    {
                                        "id" : "HotelImage",
                                        "parentRefId" : "t:EXP:HotelImages",
                                        "Schema" : "Null",
                                        "text" : [
                                            {
                                                "languageCode" : "en",
                                                "name" : "HotelImage",
                                                "description" : "Contains elements for the URL and reference values for a single image."
                                            },
                                            {
                                                "languageCode" : "pt",
                                                "name" : "HotelImage",
                                                "description" : "Contém elementos relativos ao URL e a valores de referência para uma única imagem."
                                            },
                                            {
                                                "languageCode" : "es",
                                                "name" : "HotelImage",
                                                "description" : "Contiene elementos de los valores de referencia y URL de una sola imagen."
                                            }
                                        ]
                                    },
                                    {
                                        "id" : "HotelImages",
                                        "parentRefId" : "",
                                        "Schema" : "Null",
                                        "text" : [
                                            {
                                                "languageCode" : "en",
                                                "name" : "HotelImages",
                                                "description" : "Contains all property images available. Does not contain room-level photos. Has size attribute to indicate the number of results contained. Review  image categorizations for more specific details about the data returned."
                                            },
                                            {
                                                "languageCode" : "pt",
                                                "name" : "HotelImages",
                                                "description" : "Contém todas as imagens do estabelecimento disponíveis. Não contém fotos dos quartos. Tem o atributo size para indicar o número de resultados contidos.Revise as  classificações de imagens para obter detalhes mais específicos sobre os dados retornados."
                                            },
                                            {
                                                "languageCode" : "es",
                                                "name" : "HotelImages",
                                                "description" : "Contiene todas las imágenes de propiedades disponibles. No contiene fotos de nivel de habitaciones. Tiene el atributo size para indicar el número de resultados que se devuelven.Consulte  las categorizaciones de imágenes para obtener más detalles específicos acerca de los datos que se devuelven."
                                            }
                                        ]
                                    }
                                ]
                            }
                        ],
                        "data" : {
                            "id" : "HotelImage#supplierId",
                            "type" : "eNumeric",
                            "value" : [
                                {
                                    "value" : "13"
                                }
                            ],
                            "text" : [
                                {
                                    "languageCode" : "en",
                                    "name" : "supplierId",
                                    "description" : "Indicates the supplier of the image. Follows the same mapping as the Supplier element's ID attribute."
                                },
                                {
                                    "languageCode" : "pt",
                                    "name" : "supplierId",
                                    "description" : "Indica o fornecedor da imagem. Segue o mesmo mapeamento do atributo ID do elemento Supplier."
                                },
                                {
                                    "languageCode" : "es",
                                    "name" : "supplierId",
                                    "description" : "Indica el proveedor de la imagen. Sigue la misma asignación que la del atributo ID del elemento Supplier."
                                }
                            ]
                        }
                    }
                ],
                "description" : {
                    "context" : [
                        {
                            "contextItem" : [
                                {
                                    "id" : "HotelImage#caption",
                                    "parentRefId" : "t:EXP:HotelImage",
                                    "Schema" : "Null",
                                    "text" : [
                                        {
                                            "languageCode" : "en",
                                            "name" : "caption",
                                            "description" : "Description for the image"
                                        },
                                        {
                                            "languageCode" : "pt",
                                            "name" : "caption",
                                            "description" : "Descrição da imagem."
                                        },
                                        {
                                            "languageCode" : "es",
                                            "name" : "caption",
                                            "description" : "La descripción de la imagen."
                                        }
                                    ]
                                },
                                {
                                    "id" : "HotelImage",
                                    "parentRefId" : "t:EXP:HotelImages",
                                    "Schema" : "Null",
                                    "text" : [
                                        {
                                            "languageCode" : "en",
                                            "name" : "HotelImage",
                                            "description" : "Contains elements for the URL and reference values for a single image."
                                        },
                                        {
                                            "languageCode" : "pt",
                                            "name" : "HotelImage",
                                            "description" : "Contém elementos relativos ao URL e a valores de referência para uma única imagem."
                                        },
                                        {
                                            "languageCode" : "es",
                                            "name" : "HotelImage",
                                            "description" : "Contiene elementos de los valores de referencia y URL de una sola imagen."
                                        }
                                    ]
                                },
                                {
                                    "id" : "HotelImages",
                                    "parentRefId" : "",
                                    "Schema" : "Null",
                                    "text" : [
                                        {
                                            "languageCode" : "en",
                                            "name" : "HotelImages",
                                            "description" : "Contains all property images available. Does not contain room-level photos. Has size attribute to indicate the number of results contained. Review  image categorizations for more specific details about the data returned."
                                        },
                                        {
                                            "languageCode" : "pt",
                                            "name" : "HotelImages",
                                            "description" : "Contém todas as imagens do estabelecimento disponíveis. Não contém fotos dos quartos. Tem o atributo size para indicar o número de resultados contidos.Revise as  classificações de imagens para obter detalhes mais específicos sobre os dados retornados."
                                        },
                                        {
                                            "languageCode" : "es",
                                            "name" : "HotelImages",
                                            "description" : "Contiene todas las imágenes de propiedades disponibles. No contiene fotos de nivel de habitaciones. Tiene el atributo size para indicar el número de resultados que se devuelven.Consulte  las categorizaciones de imágenes para obtener más detalles específicos acerca de los datos que se devuelven."
                                        }
                                    ]
                                }
                            ]
                        }
                    ],
                    "text" : [
                        {
                            "languageCode" : "en_US",
                            "value" : "Aerial View"
                        },
                        {
                            "languageCode" : "es_ES",
                            "value" : "Aerial View"
                        }
                    ]
                },
                "photos" : {
                    "photo" : [
                        {
                            "witdh" : "350",
                            "height" : "350",
                            "thumbnail" : false,
                            "url" : "http://images.travelnow.com/hotels/4000000/3510000/3509600/3509541/3509541_21_b.jpg"
                        },
                        {
                            "thumbnail" : true,
                            "url" : "http://images.travelnow.com/hotels/4000000/3510000/3509600/3509541/3509541_21_t.jpg"
                        }
                    ]
                }
            }
        ]
    }
}
~~~

**Contains 1 element media :**

- **Child contextItems id:**

HotelImage#Category#0 (Unknown) , HotelImage#Type#0 (Unknown)

- **Context hierarchy:**

 HotelImage#Category#0 -\> HotelImage -\> HotelImages

 HotelImage#Type#0 -\> HotelImage -\> HotelImages

- **Attribute :**

HotelImage#supplierId = 13

- **Description:**

"Aerial View"

- **Item Photos :**

2 photos ( thumbnail and not thumbnail )



### ContextItem




| **Element**		| **Number**	| **Type** 	| **Description**	                         |
| --------------------- | ------------- | ------------- | ---------------------------------------------- |
| Context      		|       	| Context 	|                                                |
| /Context/contextItem 	| 1..n  	|         	|                                                |
| contextItem  		|       	|         	|                                                |
| /code        		| 0..1  	| String 	| Provider code	                                 |
| /id          		| 1     	| String 	| Unique id identifier                           |
| /parentRefId 		| 0..1  	| String  	| If this field is not null, exist in this context a contextItem with id = parentRefId. This field is used to build a context hierachy. |
| /Schema      		| 0..1  	|         	|                                                |
| /text        		| 1..n  	| Text  	| text: Providers explanation of the context.    |



ContextItem provide context information to each data / text and
Medias ( Attributes, Descriptions and Medias).

It can represent both provider typified data type (i.e. Media type
Exterior, Facility type bar/lounge...) and depth level of the provider
response (i.e. Attribute refers to a Property Amenity, Description -\>
text is the Hotel Long Description...).

Each context item is typified by:

*id*

parentRefId ( if parentRefId is not null, means that exist a contextItem
which is in a low depth and match it's Id with parentRefId that provide
more context information to the child element)

*text*

It can contain N child elements, child element is a contextItem that
it's id is not contained in other contexItem's -\> parentRefId (in the
same context)



### Data




| **Element**		| **Number**	| **Type**	| **Description**					|
| --------------------- | ------------- | ------------- | ----------------------------------------------------- |
| Data         		| 1     	| Data  	|	                                                |
| @type        		| 1     	| String 	| Available types : string, numeric, boolean, xml (for complex types). |
| /Code        		| 1     	| String 	| Providers Code  	                                |
| /Id          		| 1     	| String 	| Unique Id         	                                |
| /Value       		| 1     	| Value 	|  	                                                |
| /Value @languageCode  | 1     	| String 	| Value's language (if not returned, it fills in all langagues read below). |
| /Value/value 		| 1     	| String 	| Value of the element.     	                        |
| /Text        		| 1     	| Text  	| text 		                                        |



Data element is used to return the value of an item which is in the
context specified by the contextItem_ element.

**Different types:**

-   Boolean
-   Numeric
-   String
-   xml

*xml is only returned when we cannot parse a provider response element.
When xml is returned in type field, value element will be the raw xml
value of the provider.*

**Multilanguage value :**

There will be a value element for each language available for each element, languageCode is specified as attribute for each value

**Language not provided will be returned as default :**

There will be only 1 value element with languageCode set as "" or not being returned.



### Text




| **Element**		| **Number**	| **Type**	| **Description**					|
| --------------------- | ------------- | ------------- | ----------------------------------------------------- |
| Text         		|       	| Text  	|                                                       |
| @languageCode 	| 0..1 		| Text  	| languaceCode format: language_culture, culture could not be provided. |
| name         		| 1   		| Text  	| Text Name                                       	|
| description  		| 0..1 		| Text  	| Provider explanation of the context specyfied   	|
| value        		| 0..1 		| Text  	| This field is returned in the Descriptions text field. It refers to the description value. |



Description field is filled with the provider documentation or response
from the provider. It will be empty if the provider documentation /
response doesn't provide explanation of the element.

It is returned by each language Code available. If and contains name and
description of the element refered to.

See data section regarding Languages.


