---
title: Enum
keywords: transportation, data structure, flights, enum
search: Transportation - Flights - Data Structure - Enum
sidebar: mydoc_sidebar
permalink: /docs/transportation
---

### Enumerate description

##### Discount card 


| **Possible Values**	| **Description**	|
| --------------------- | ------------------ |
| N | None |
| NINYO |  |
| JOVEN | |
| ESCAPADA | |
| SENIOR | |
| THALYS_CORPORATE | |
| FORFAIT_LYS | |
| ABO_FREQUENCE_1ST_AND_2ND | |
| ABO_FORFAIT_1ST_AND_2ND | |
| BAHN_CARD_REDUCTION | |
| BAHN_CARD_25 | |
| SWITZERLAND_50 | |
| SWITZERLAND_100 | |
| EJERCITO_AIRE | |
| EJERCITO_TIERRA | |
| FUERZAS_NAVALES | |
| GUARDIA_CIVIL | |
| FREQUENT_FLYER | |
| CARTA_ARGENTO | |
| CARTA_FRECCIA | |
| UK_ANNUAL_GOLD | |
| UK_CHILD_DISABILITY | |
| UK_DISABILITY | |
| UK_FAMILY_FRIENDS | |
| UK_GROUPSAVE3 | |
| UK_GROUPSAVE4 | |
| UK_HM_ARMED_FORCES | |
| UK_JOBCENTRE_PLUS | |
| UK_NETWORK | |
| UK_SENIOR | |
| UK_TWO_TOGETHER | |
| UK_YOUTH | |
| UK_GROUPSAVE | |

##### Resident discount 
| **Possible Values**	| **Description**	|
| --------------------- | ------------------ |
| N | None |
| BP | Balearic Islands resident flying to mainland |
| BI | Balearic Islands resident flying to another balearic island |
| DC | Canarian Islands resident flying to another Canarian Island |
| RC | Canarian Islands resident flying to mainland |
| RM | Ceuta/Melilla resident |
| STR | Italian resident  discount |
| ELB | Italian resident Elba |
| SDG | Italian resident Sardegna |
| SLC | Italian resident Sicily |
| RE | Ceuta |

##### Vehicle type 
| **Possible Values**	| **Description**	|
| --------------------- | ------------------ |
| Turismo  | Touring  |
| Todoterreno  | All terrain  |
| Monovolumen  | Minivan  |
| CiclomotorMax50  | Moped max 50kg.  |
| MotocicletaMin50Max250  | Motorcicle min 50kg. max 250kg.  |
| MotocicletaMin250Max500  | Motorcicle min 250kg. max 500kg.  |
| MotocicletaMin500  | Motorcicle min 500kg.  |
| Bicicleta  | Bike  |
| Furgoneta  | Van  |
| VehiculoLargoMax6  | Long vehicle max 6m.  |
| VehiculoEmision  | Zero emissions vehicle  |
| Caravana  | Caravan  |
| Remolque  | Trailer  |

##### Charge type 
| **Possible Values**	| **Description**	|
| --------------------- | ------------------ |
| TASA  | Tax  |
| TARJETA  | Card  |
| EQUIPAJE  | Baggage  |
| CHECKIN  | Checkin  |
| GASTOS_CIA  | Carrier charges  |
| TASA_DU  | DU Taxes  |
| IMPORTE_BASE  | Base import  |
| DESCUENTO  | Discount  |
| VEHICULO  | Vehicle  |
| GASTOS_BANCARIOS  | Bank charges  |
| GASTOS_CONVERSION_DIVISA  | Currency conversion charges  |
| FEE_VEHICULO  | Vehicle fee  |
| FEE  | Fee  |
| ASIENTO  | Seat  |
| SUPLEMENTO  | Supplement  |
| TRAVELCARD  | Travel card  |
| MASCOTA  | Pet  |
| FEE_MASCOTA  | Pet fee  |
| SEGURO  | Ensurance  |
| ACCESO_PREFERENTE  | Fast Track  |
| EMBARQUE_PRIORITARIO  | Priority Boarding  |
| BLOQUEO_TARIFA  | Fare lock |
| ASISTENCIA_ESPECIAL  | Special assistance  |
| PENALTY  | Penalty  |

##### Block type 
| **Possible Values**	| **Description**	|
| --------------------- | ------------------ |
| OVER_WING | Over wing seat|
| MIDDLE  | Middle seat |
| AISLE  | Aisle seat  |
| WINDOW  | Window seat  |
| COMPARTMENT  | Compartment |
| LAVATORY | Lavatory |
| LUGGAGE | Luggage seat |
| PHONE | Phone seat |
| POWER | Power |
| TABLE | Table |
| EXITROW | Emergency exit |
| FEETBLOCKED | Feet blocked seat |
| NO_CHILD | No childs allowed seat |
| NO_INFANT | No infants allowed seat |
| XL_SEAT | XL seat |
| RESTRICTED | Seat with some kind of restriction |
| HANDICAP | Special seat for handicap people |
| QUIET | Quiet seat |
| GROUPS | Groups seat |
| NO_PET | No pets allowed seat |
| BULKHEAD | Bulk head seat |
| BLOCKED | Blocked seat |
| UNKNOWN | Unknown characterstic |
| LAST_OFF | Last off |

##### Refund type
| **Possible Values**	| **Description**	|
| --------------------- | ------------------ |
| All | Fare and taxes will be refunded |
| Fare | Only fare will be refunded |
| Taxes | Only taxes will be refunded |
| Auto | GDS automatic ticket change |

##### Refund process type
| **Possible Values**	| **Description**	|
| --------------------- | ------------------ |
| Info | Informative refund operation |
| Process | Efective refund operation |

##### Refund amount type
| **Possible Values**	| **Description**	 |
| --------------------- | ------------------ |
| Other | Other refund amount  |
| Tax | Tax amount |
| Flown | For partial refund when some segment is already flown |
| Penalty | Penalty amount|

##### Pax type
| **Possible Values**	| **Description**	|
| --------------------- | ------------------ |
| ADT | Adult  |
| CHD | Child |
| INF | Infant|

##### Direction type
| **Possible Values**	| **Description**	|
| --------------------- | ------------------ |
| DEPARTURE | Outbound  |
| RETURN | Inbound |
| DEPARTURE_RETURN | Outbound and Inbound|

##### Status response type
| **Possible Values**	| **Description**	|
| --------------------- | ------------------ |
| ok | ok status response |
| err | error status response|
| timeout | timeout status response|

##### Trip type
| **Possible Values**	| **Description**	|
| --------------------- | ------------------ |
| RT | Round Trip. Outbound and inbound with same origin and destination |
| OW | One Way. Outbound|
| OJ | Open Jaw. Outbound and inbound with diferent origin or destination|
| CT | Cicle Trip. Round trip with multiple destinations|

##### Locator type
| **Possible Values**	| **Description**	|
| --------------------- | ------------------ |
| PROVIDER |  Provider locator|
| ISSUING | Issue locator|
| CARRIER | Carrier locator|
| SERVICE | Service locator|
| REFUND | Refund locator|
| CHECKIN | CheckIn locator|

##### Amount Type 
| **Possible Values**	| **Description**	|
| --------------------- | ------------------ |
| N                     | None |
| AMOUNT                | |
| FEE                   | |
| TOTAL                 | |
| PERCENTUAL            | |

##### Payment Type 
| **Possible Values**	| **Description**	|
| --------------------- | ------------------ |
| N                     | None |
| CASH                  | |
| CARD                  | |
| EMIT                  | |

##### Issue Type
| **Possible Values**	| **Description**	|
| --------------------- | ------------------ |
| N                     | None |
| Air                   |Passenger tickets  |
| Extra                 |Ancillaries (bags, seats, etc.) |
| All                   |Both |