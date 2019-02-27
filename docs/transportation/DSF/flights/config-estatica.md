---
title: StaticConfiguration
keywords: transportation, data structure, flights, staticconfiguration
search: Transportation - Flights - Data Structure - StaticConfiguration
sidebar: mydoc_sidebar
permalink: /docs/transportation/DSF/flights/config-static
---



### Method Goals

This method provides the static configuration of a supplier. For example: if the supplier allows the payment with credit/debit card.


### Request Format

The request does not require any elements - empty request.



### Response Format

The XML response contains many elements of the supplier’s configuration: provider type, whether or not the supplier allows RT and OJ trips, frequent flyer, filtering airlines, cabin class, etc.



### Remarks

Not implemented by all suppliers.



### StaticConfigurationRQ Description



| **Element**			        | **Number**	| **Type**	| **Description**			            |
| ----------------------------- | ------------- | ----------| ------------------------------------- |
| StaticConfigurationRQ         | 1     	    |		    | Root node.				            |



### StaticConfigurationRS Description


| **Element**			                        | **Number**	| **Type**	| **Description**			            |
| ----------------------------------------------| ------------- | ----------| ------------------------------------- |
| StaticConfigurationRS                         | 1     	    |		    | Root node.				            |
| ProviderType                                  | 1     	    | [Provider type](https://github.com/XML-Travelgate/xtg-content-articles-pub/blob/master/docs/transportation/enum.md#provider-type)	        | Provider type.|
| UnaccompaniedMinors                           | 1     	    | Boolean	| Allows the reservation of minors without adults in the same booking.|
| VirtualInterlining                            | 1     	    | Boolean	| Virtual Interlines. For instance: PMI-MAD (FR), MAD-JFK (AA), JFK-MAD (AA), MAD-PMI (FR).|
| MultiClassReservation                         | 1     	    | Boolean	| Reservation with different fare types for distinct passenger types. For instance: ADT with a private fare and CHD with a public fare in the same booking.|
| ReturnsFareFamily                             | 1     	    | Boolean	| Returns the fare family in which the fare is associated (carrier branded fare).|
| AllowsReservationLocking                      | 1     	    | Boolean	| Allows to book a fare and hold it without paying (like GDS does).|
| MultiTransportType                            | 1     	    | Boolean	| Multiple transportation types may be returned in the itinerary (train, bus, flights).|
| RequiresInmediatePayment                      | 1     	    | Boolean	| The payment must be provided at Reservation step. There is no Issue transaction.|
| LargeFamilyDiscount                           | 1     	    | Boolean	| Allows large family discounts.|
| ResidentDiscount                              | 1     	    | Boolean	| Allows resident discounts.|
| AlternativePassengerTypeDiscount              | 1     	    | Boolean	| Allows alternative passenger type discounts. Some suppliers associate passenger type codes (other than ADT, CHD and INF), in order to attacht a discount to it.|
| DiscountCard                                  | 1     	    | Boolean	| Allows discount cards.|
| FrequentFlyer                                 | 1     	    | Boolean	| Allows frequent flyer reservations.|
| ReturnsTaxes                                  | 1     	    | Boolean	| Return the taxes associated to the fare.|
| ReturnDuTaxes                                 | 1     	    | Boolean	| Returns the DU taxes associated to the fare, if there is any.|
| PassengerTypePriceBreakdown                   | 1     	    | Boolean	| Returns the price breakdown by passenger type. If false, only the total price will be returned.|
| Currencies                                    | 0..n     	    | String	| List of currencies allowed by the supplier.|
| Availability                                  | 1     	    | 		    | Availability.|
| Availability/Implemented                      | 1     	    | Boolean	| Availability transaction implemented.|
| Availability/ReturnsMultiTicketing            | 1     	    | Boolean	| Multiple OW and RT combinations can be returned in the same query.|
| Availability/ReturnsIncludedBaggage           | 1     	    | Boolean	| Returns information of the luggage included in the fare.|
| Availability/ReturnsExtraBaggage              | 1     	    | Boolean	| Returns information of the extra luggage purchasable at booking step.|
| Availability/ReturnsSupplements               | 1     	    | Boolean	| Returns information of the supplements purchasable at booking step.|
| Availability/ReturnsRemainingSeats            | 1     	    | Boolean	| Returns the remaining seats of the class (of single flight).|
| Availability/InformObFeesCharge               | 1     	    | Boolean	| Indicates if the customer will be charged with OB fees in case he pays with debit/credit card. If false, the supplier will not indicate this information.|
| Availability/ReturnsTerminals                 | 1     	    | Boolean	| Returns information of the airport terminals.|
| Availability/ReturnsOperatingCarrier          | 1     	    | Boolean	| Returns the operating carrier of the flight.|
| Availability/ReturnsValidatingCarrier         | 1     	    | Boolean	| Returns the validating carrier of the fare.|
| Availability/ReturnsTechnicalStops            | 1     	    | Boolean	| Returns information of the technical stops of a segment.|
| Availability/ReturnsLastTicketingDate         | 1     	    | Boolean	| Returns the last ticketing date of the fare.|
| Availability/MustIncludeAirlines              | 1     	    | Boolean	| The query must include the airline/s.|
| Availability/AllowsIncludeAirlines            | 1     	    | Boolean	| It is possible to filter out airline/s (INCLUDE).|
| Availability/AllowsExcludeAirlines            | 1     	    | Boolean	| It is possible to filter out airline/s (EXCLUDE).|
| Availability/AllowsIncludeAndExcludeAirlines  | 1     	    | Boolean	| It is possible to filter out airline/s (INCLUDE and EXCLUDE in the same query).|
| Availability/IataAirlineCodes                 | 1     	    | Boolean	| Uses IATA 2-letters codes for the airline filtering.|
| Availability/ReturnsMoreThanTwoOptionsByFare  | 1     	    | Boolean	| One RT/OJ fare may contain more than one option per leg. For instance a RT fare may include two options for the first journey and three options for the return journey.|
| Availability/JourneyType                      | 1     	    | 		    | Journey Type.|
| Availability/JourneyType/OneWay               | 1     	    | Boolean	| Allows one way trips.|
| Availability/JourneyType/RoundTrip            | 1     	    | Boolean	| Allows round trips.|
| Availability/JourneyType/OpenJaw              | 1     	    | Boolean	| Allows open jaw trips.|
| Availability/JourneyType/CircleTrip           | 1     	    | Boolean	| Allows circle trips.|
| Availability/JourneyType/RoundWorld           | 1     	    | Boolean	| Allows round the world trips (multi journey trip). See MaxJourneys to know how many journeys are allowed.|
| Availability/JourneyType/MaxJourneys          | 1     	    | Integer	| Maximum journeys allowed for circle and round world trips.|
| Availability/SearchRadius                     | 1     	    | Boolean	| Allows the search by radius (kilometers).|
| Availability/CityCodes                        | 1     	    | Boolean	| Allows the search by city codes.|
| Availability/CabinTypeFiltering               | 1     	    | Boolean	| Allows fare filtering by cabin class.|
| Availability/AlternativeDates                 | 1     	    | Boolean	| Allows the search with ranges of dates.|
| Availability/AlternativeLocations             | 1     	    | Boolean	| Allows the search with multiple locations for each journey in the same query.|
| Availability/AllowsSpecifyHour                | 1     	    | Boolean	| Allows the search for a concrete hour of the day for each journey.|
| Valuation                                     | 1     	    | 		    | Valuation.|
| Valuation/Implemented                         | 1     	    | Boolean	| Valuation transaction implemented.|
| Valuation/MultiItineraries                    | 1     	    | Boolean	| It is possible to price multiple itineraries in the same query.|
| Valuation/MultiCarrierItineraries             | 1     	    | Boolean	| It is possible to price multiple itineraries (each itinerary with a different carrier) in the same query.|
| Valuation/ReturnsTerminals                    | 1     	    | Boolean	| Returns information of the airport terminals.|
| Valuation/ReturnsOperatingCarrier             | 1     	    | Boolean	| Returns the operating carrier of the flight.|
| Valuation/ReturnsValidatingCarrier            | 1     	    | Boolean	| Returns the validating carrier of the fare.|
| Valuation/ReturnsTechnicalStops               | 1     	    | Boolean	| Returns information of the technical stops of a segment.|
| Valuation/ReturnsLastTicketingDate            | 1     	    | Boolean	| Returns the last ticketing date of the fare.|
| Valuation/ReturnsPaymentMethods               | 1     	    | Boolean	| Returns the different payment methods allowed (and their fees if any).|
| Valuation/ReturnsSpecialSupplements           | 1     	    | Boolean	| Returns the special supplements that are chargeable (pets in cabin, food, etc.).|
| Valuation/ReturnsSpecialLuggage               | 1     	    | Boolean	| Returns the special luggage chargeable (surf, guitar, etc.).|
| Valuation/ReturnsFareRules                    | 1     	    | Boolean	| Returns the fare rules (free text).|
| Valuation/ReturnsSummarizedRules              | 1     	    | Boolean	| Returns the fare rules (summarized).|
| Valuation/ReturnsSeating                      | 1     	    | Boolean	| Returns the seat map.|
| Valuation/ReturnsIncludedBaggage              | 1     	    | Boolean	| Returns the included baggage conditions.|
| Valuation/ReturnsExtraBaggage                 | 1     	    | Boolean	| Returns the chargeable baggage conditions.|
| Valuation/ReturnsInstalments                  | 1     	    | Boolean	| Returns the available instalments conditions to process a payment.|
| Reservation                                   | 1     	    | 		    | Reservation.|
| Reservation/Implemented                       | 1     	    | Boolean	| Reservation transaction implemented.|
| Reservation/MultiItineraries                  | 1     	    | Boolean	| It is possible to price multiple itineraries in the same query.|
| Reservation/MultiCarrierItineraries           | 1     	    | Boolean	| It is possible to price multiple itineraries (each itinerary with a different carrier) in the same query.|
| Reservation/DeltaPrice                        | 1     	    | Boolean	| It is possible to set a maximum amount increasement allowed between valuation and reservation.|
| Reservation/PaymentMethods                    | 1     	    | 		    | Payment methods.|
| Reservation/PaymentMethods/Card               | 1     	    | Boolean	| Allows the payment with card.|
| Reservation/PaymentMethods/Cash               | 1     	    | Boolean	| Allows the payment with cash (agency account).|
| Reservation/PaymentMethods/Instalments        | 1     	    | Boolean	| Allows tha payment by instalments.|
| Reservation/ReturnsLastTicketingDate          | 1     	    | Boolean	| Returns the last ticketing date of the fare.|
| Reservation/LuggageReservation                | 1     	    | Boolean	| Allows the reservation of extra baggage.|
| Reservation/SeatReservation                   | 1     	    | Boolean	| Allows the reservation of seats.|
| Reservation/SpecialSupplementsReservation     | 1     	    | Boolean	| Allows the reservation of special supplements.|
| Reservation/SpecialLuggageReservation         | 1     	    | Boolean	| Allows the reservation of special luggage.|
| Issue                                         | 1     	    | 		    | Issue.|
| Issue/Implemented                             | 1     	    | Boolean	| Issue transaction implemented.|
| Issue/AllowsExtraIssuance                     | 1     	    | Boolean	| Allows the issuance of extras (for example baggage).|
| Issue/PaymentMethods                          | 1     	    | 		    | Payment methods.|
| Issue/PaymentMethods/Card                     | 1     	    | Boolean	| Allows the payment with card at issuance step.|
| Issue/PaymentMethods/Cash                     | 1     	    | Boolean	| Allows the payment with cash (agency account) at issuance step.|
| Issue/PaymentMethods/Instalments              | 1     	    | Boolean	| Allows tha payment by instalments at issuance step.|
| Cancellation                                  | 1     	    | 		    | Cancellation.|
| Cancellation/Implemented                      | 1     	    | Boolean	| Cancellation transaction implemented.|
| Cancellation/VoidsTickets                     | 1     	    | Boolean	| The tickets are automatically voided when the PNR is being cancelled.|
| RetrieveReservation                           | 1     	    | 		    | Retrieve reservation.|
| RetrieveReservation/Implemented               | 1     	    | Boolean	| RetrieveReservation transaction implemented.|
| RetrieveReservation/RequiresEmail             | 1     	    | Boolean	| Requires the email (set up at booking step) to retrieve the reservation.|
| RetrieveReservation/ReturnsReservationStatus  | 1     	    | Boolean	| Returns the status of the reservation. Whether the booking is CANCELED, CONFIRMED, ON_HOLD, etc.|
| RetrieveReservation/ReturnsTickets            | 1     	    | Boolean	| Returns the tickets.|
| RetrieveReservation/ReturnsFareRules          | 1     	    | Boolean	| Returns the fare rules.|
| RetrieveReservation/ReturnsLastTicketingDate  | 1     	    | Boolean	| Returns the last ticketing date of the fare.|
| RetrieveReservation/ReturnsIncludedBaggage    | 1     	    | Boolean 	| Returns information of the luggage included in the fare.|
| RetrieveReservation/ReturnsTerminals          | 1     	    | Boolean	| Returns information of the airport terminals.|
| RetrieveReservationList                       | 1     	    | 		    | Retrieve reservation list.|
| RetrieveReservationList/Implemented           | 1     	    | Boolean	| RetrieveReservationList transaction implemented.|
| RetrieveReservationList/Email                 | 1     	    | Boolean	| Allows the retrieving by email.|
| RetrieveReservationList/Locations             | 1     	    | Boolean	| Allows the retrieving by origin/destination locations.|
| RetrieveReservationList/ReservationDate       | 1     	    | Boolean	| Allows the retrieving by reservation dates.|
| RetrieveReservationList/DepartureDate         | 1     	    | Boolean	| Allows the retrieving by departure dates.|
| RetrieveReservationList/TransportNumber       | 1     	    | Boolean	| Allows the retrieving by transport numbers.|
| RetrieveReservationList/PassengerData         | 1     	    | Boolean	| Allows the retrieving by passenger data (name and surnames).|
| Supplements                                   | 1     	    | 		    | Supplements.|
| Supplements/Implemented                       | 1     	    | Boolean	| Supplements transaction implemented.|
| Supplements/PreReservationSupplements         | 1     	    | Boolean	| Allows to get the availability of chargeable supplements BEFORE booking the flights.|
| Supplements/PostReservationSupplements        | 1     	    | Boolean	| Allows to get the availability of chargeable supplements AFTER booking the flights.|
| Supplements/ReturnsPaymentMethods             | 1     	    | Boolean	| Returns the different payment methods allowed (and their fees, if any).|
| Supplements/ReturnsSpecialSupplements         | 1     	    | Boolean	| Returns the special supplements that are chargeable (pets in cabin, food, etc.)|
| Supplements/ReturnsSpecialLuggage             | 1     	    | Boolean	| Returns the special luggage chargeable (surf, guitar, etc.).|
| Supplements/ReturnsFareRules                  | 1     	    | Boolean	| Returns the fare rules (free text).|
| Supplements/ReturnsSummarizedRules            | 1     	    | Boolean	| Returns the fare rules (summarized).|
| Supplements/ReturnsSeating                    | 1     	    | Boolean	| Returns the seat map.|
| Supplements/ReturnsIncludedBaggage            | 1     	    | Boolean	| Returns the included baggage conditions.|
| Supplements/ReturnsExtraBaggage               | 1     	    | Boolean	| Returns the chargeable baggage conditions.|
| Supplements/ReturnsInstalments                | 1     	    | Boolean	| Returns the available instalments conditions to process the payment.|
| Void                                          | 1     	    | 		    | Void.|
| Void/Implemented                              | 1     	    | Boolean	| Void transaction implemented.|
| Void/CancelsReservation                       | 1     	    | Boolean	| Cancels the PNR after voiding the ticket.|
| Void/AllowsVoidingAllPNRTickets               | 1     	    | Boolean	| Allows voiding all the tickets of a PNR at the same time (in the same query).|
| Refund                                        | 1     	    | 		    | Refund.|
| Refund/Implemented                            | 1     	    | Boolean	| Refund transaction implemented.|
| Refund/RefundTypes                            | 1     	    | 		    | Refund types.|
| Refund/RefundTypes/Total                      | 1     	    | Boolean	| Total refund.|
| Refund/RefundTypes/Partial                    | 1     	    | Boolean	| Partial refund (Example: in case one of the itineraries has already been flown).|
| Refund/RefundTypes/Fare                       | 1     	    | Boolean	| Fare refund (without taxes).|
| Refund/RefundTypes/Taxes                      | 1     	    | Boolean	| Taxes refund.|
| Refund/RefundTypes/Automatic                  | 1     	    | Boolean	| Automatic refund (GDS purposes).|
| Refund/RefundProcess                          | 1     	    | 		    | Refund processes.|
| Refund/RefundProcess/Process                  | 1     	    | Boolean	| It is possible to process a refund.|
| Refund/RefundProcess/Informative              | 1     	    | Boolean	| It is possible to get information of the refund amounts without processing it.|
| OperativeReservation                          | 1     	    | 		    | Operative Reservation.|
| OperativeReservation/Implemented              | 1     	    | Boolean	| OperativeReservation transaction implemented.|
| OperativeReservation/AcceptChanges            | 1     	    | Boolean	| It is possible to accept a change in a PNR (GDS purposes).|
| OperativeReservation/ReturnResponsability     | 1     	    | Boolean	| It is possible to change the responsability of a PNR to another office of an agency (GDS purposes).|
| AvailabilityFares                             | 1     	    | 		    | Availability fares.|
| AvailabilityFares/Implemented                 | 1     	    | Boolean	| AvailabilityFares transaction implemented.|
| AvailabilityFares/BrandedFares                | 1     	    | Boolean	| It is possible to get the branded fares for a concrete itinerary (Example: the customer selects the flight IB6065. Now with this flight, it is possible to get all the branded fares available).|
| AvailabilityFares/CustomFares                 | 1     	    | Boolean	| It is possible to get custom fares for a concrete itinerary.|
| AvailabilityFares/ReturnsIncludedBaggage      | 1     	    | Boolean	| Returns information of the luggage included in the fare.|
| AvailabilityFares/ReturnsExtraBaggage         | 1     	    | Boolean	| Returns information of the extra luggage purchasable at booking step.|
| AvailabilityFares/ReturnsSupplements          | 1     	    | Boolean	| Returns information of the supplements purchasable at booking step.|
| QueueDeleteElement                            | 1     	    | 		    | Queue delete element.|
| QueueDeleteElement/Implemented                | 1     	    | Boolean	| QueueDeleteElement transaction implemented.|
| QueueInsertElement                            | 1     	    | 		    | Queue insert element.|
| QueueInsertElement/Implemented                | 1     	    | Boolean	| QueueInsertElement transaction implemented.|
| QueueListElements                             | 1     	    | 		    | Queue list elements.|
| QueueListElements/Implemented                 | 1     	    | Boolean	| QueueListElements transaction implemented.|
| QueueListElements/RequireIndicateQueue        | 1     	    | Boolean	| It is obligatory to indicate the queue in which the PNR will be moved.|
| SupplementsReservation                        | 1     	    | 		    | Supplements reservation.|
| SupplementsReservation/Implemented            | 1     	    | Boolean	| SupplementsReservation transaction implemented.|
| SupplementsReservation/PaymentMethods         | 1     	    | 		    | Payment methods.|
| SupplementsReservation/PaymentMethods/Card    | 1     	    | Boolean	| Allows the payment with card at supplements reservation step.|
| SupplementsReservation/PaymentMethods/Cash    | 1     	    | Boolean	| Allows the payment with cash (agency account) at supplements reservation step.|
| SupplementsReservation/PaymentMethods/Instalments| 1     	    | Boolean	| Allows tha payment by instalments at supplements reservation step.|
| SupplementsReservation/LuggageReservation     | 1     	    | Boolean	| Allows the reservation of extra baggage.|
| SupplementsReservation/SeatReservation        | 1     	    | Boolean	| Allows the reservation of seats.|
| SupplementsReservation/SpecialSupplementsReservation| 1     	| Boolean	| Allows the reservation of special supplements.|
| SupplementsReservation/SpecialLuggageReservation| 1     	    | Boolean	| Allows the reservation of special luggage.|
| Revaluation                                   | 1     	    | 		    | Revaluation.|
| Revaluation/Implemented                       | 1     	    | Boolean	| Revaluation transaction implemented.|
| Revaluation/ReturnsLastTicketingDate          | 1     	    | Boolean	| Returns the last ticketing date of the fare.|
| Revaluation/ReturnsIncludedBaggage            | 1     	    | Boolean	| Returns information of the luggage included in the fare.|
| Routes                                        | 1     	    | 		    | Routes.|
| Routes/Implemented                            | 1     	    | Boolean	| Routes transaction implemented.|
| Routes/ReturnDates                            | 1     	    | Boolean	| Returns the departure dates for each route.|