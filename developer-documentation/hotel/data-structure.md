---
title: Data Structure
keywords: common elements, elements, hotel
sidebar: mydoc_sidebar
permalink: /developer-documentation/hotel/data-structure
---

The structure of the API specification follows a standard. This document
intends to explain every aspect of this structure and their fields. The
integration will have the following methods:

| **Method**                | **Input**                   | **Output**                  | **Required** | **Description** |
| ------------------------- | --------------------------- | --------------------------- | ------------ | --------------- |
| AvailDestination Tree      | AvailDestination TreeRQ      | AvailDestination TreeRS      | No           | Returns a tree of available destinations. |
| Geographic DestinationTree | Geographic DestinationTreeRQ | Geographic DestinationTreeRS | Yes          | Returns a tree of provider destinations. |
| HotelList                 | HotelListRQ                 | HotelListRS                 | Yes          | Returns a list of available hotels. |
| Descriptive Info           | Descriptive InfoRQ           | Descriptive InfoRS           | Yes          | Returns hotel information per hotel. |
| RoomList                  | RoomListRQ                  | RoomListRS                  | No           | Returns available room types. |
| MealPlanList              | MealPlanListRQ              | MealPlanListRS              | Yes          | Returns a list of available boards. |
| CategoryList              | CategoryListRQ              | CategoryListRS              | Yes  	       | Returns a list of available categories. |
| Avail                     | AvailRQ                     | AvailRS                     | Yes          | Makes an availability call. |
| Valuation                 | ValuationRQ                 | ValuationRS                 | Yes          | Gets a booking quote (pre-book). |
| Reservation               | ReservationRQ               | ReservationRS               | Yes          | Makes a booking. |
| Cancel                    | CancelRQ                    | CancelRS                    | No           | Cancels a booking. |
| ReservationRead           | ReservationReadRQ           | ReservationReadRS           | No           | Gets booking details. |
| ReservationList           | ReservationListRQ           | ReservationListRS           | No           | Gets a list of bookings. |
| Runtime Configuration      | Runtime ConfigurationRQ      | Runtime ConfigurationRS      | Yes          | Gets the provider’s run-time configuration. |
| Static Configuration       | Static ConfigurationRQ       | StaticC onfigurationRS       | Yes          | Gets the provider’s static configuration. |
| ModifyValuation           | ModifyValuationRQ           | ModifyValuationRS           | No           | Valuation a possible booking modification. |
| ModifyReservation         | Modify ReservationRQ         |  Modify ReservationRS        | No           | Confirm a booking modification. |


Each request sent to the **service url** requires a node called *rqXML*.
Inside this node travels the current method's Input object.



The data structure will always have common elements in all objects and
the specific objects related to the operation



**Data structure content:**

1. [Common-Elements](/developer-documentation/hotel/DSF/Common-Elements)
2. [Avail](/developer-documentation/hotel/DSF/Avail)
3. [Valuation](/developer-documentation/hotel/DSF/Valuation)
4. [Reservation](/developer-documentation/hotel/DSF/Reservation)
5. [ReservationRead](/developer-documentation/hotel/DSF/ReservationRead)
6. [ReservationList](/developer-documentation/hotel/DSF/ReservationList)
7. [Cancel](/developer-documentation/hotel/DSF/Cancel)
8. [HotelList](/developer-documentation/hotel/DSF/HotelList)
9. [DescriptiveInfo](/developer-documentation/hotel/DSF/DescriptiveInfo)
10. [DescriptiveInfoExtended](/developer-documentation/hotel/DSF/DescriptiveInfoExtended)
11. [AvailDestinationTree](/developer-documentation/hotel/DSF/AvailDestinationTree)
12. [GeographicDestinationTree](/developer-documentation/hotel/DSF/GeographicDestinationTree)
13. [MealPlanList](/developer-documentation/hotel/DSF/MealPlanList)
14. [RoomList](/developer-documentation/hotel/DSF/RoomList)
15. [CategoryList](/developer-documentation/hotel/DSF/CategoryList)
16. [StaticConfiguration](/developer-documentation/hotel/DSF/StaticConfiguration)
17. [RuntimeConfiguration](/developer-documentation/hotel/DSF/RuntimeConfiguration)
18. [ModifyValuation](/developer-documentation/hotel/DSF/ModifyValuation)
19. [ModifyReservation](/developer-documentation/hotel/DSF/ModifyReservation)
20. [CurrencyList](/developer-documentation/hotel/DSF/CurrencyList)
21. [Lists of Data](/developer-documentation/hotel/DSF/ListData)



