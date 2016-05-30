---
title: Data Structure
keywords: common elements, elements, hotel
sidebar: mydoc_sidebar
permalink: /docs/hotel/data-structure
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

1. [Common-Elements](/docs/hotel/DSF/Common-Elements)
2. [Avail](/docs/hotel/DSF/Avail)
3. [Valuation](/docs/hotel/DSF/Valuation)
4. [Reservation](/docs/hotel/DSF/Reservation)
5. [ReservationRead](/docs/hotel/DSF/ReservationRead)
6. [ReservationList](/docs/hotel/DSF/ReservationList)
7. [Cancel](/docs/hotel/DSF/Cancel)
8. [HotelList](/docs/hotel/DSF/HotelList)
9. [DescriptiveInfo](/docs/hotel/DSF/DescriptiveInfo)
10. [DescriptiveInfoExtended](/docs/hotel/DSF/DescriptiveInfoExtended)
11. [AvailDestinationTree](/docs/hotel/DSF/AvailDestinationTree)
12. [GeographicDestinationTree](/docs/hotel/DSF/GeographicDestinationTree)
13. [MealPlanList](/docs/hotel/DSF/MealPlanList)
14. [RoomList](/docs/hotel/DSF/RoomList)
15. [CategoryList](/docs/hotel/DSF/CategoryList)
16. [StaticConfiguration](/docs/hotel/DSF/StaticConfiguration)
17. [RuntimeConfiguration](/docs/hotel/DSF/RuntimeConfiguration)
18. [ModifyValuation](/docs/hotel/DSF/ModifyValuation)
19. [ModifyReservation](/docs/hotel/DSF/ModifyReservation)
20. [CurrencyList](/docs/hotel/DSF/CurrencyList)
21. [Lists of Data](/docs/hotel/DSF/ListData)



