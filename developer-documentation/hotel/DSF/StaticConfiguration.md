---
title: StaticConfiguration
keywords: hotel, data structure, static configuration, static
sidebar: mydoc_sidebar
permalink: /developer-documentation/hotel/DSF/StaticConfiguration
---




Method Goals
============

This message provides information about the static configuration of the
provider, to see and configure the provider in the best way.



Request Format
==============

The request does not require any elements empty request.



Response Format
===============

The XML returned contains more elements on the configuration (number of
hotels, the number of cities and the number of areas of availability, if
the provider returns the cancellation policies, maximum number of
distributions, maximum number of paxes in a distribution, release days,
stay minimum, list of languages that allows ....).



StaticConfigurationRQ Example
=============================

    <StaticConfigurationRQ>
    </StaticConfigurationRQ>



StaticConfigurationRQ Description
=================================

  
| **Element**			| **Number**	| **Type**	| **Description**	|
| ----------------------------- | ------------- | ------------- | --------------------- |
| StaticConfigurationRQ		| 1          	|		| Root node.		|
                
  

StaticConfigurationRS Example
=============================

    <StaticConfigurationRS>
        <MaxNumberHotels>2000</MaxNumberHotels>
        <MaxNumberCities>1</MaxNumberCities>
        <MaxNumberZones>1</MaxNumberZones>
        <MaxNumberGeoCodes>0</MaxNumberGeoCodes>
        <RequiredRoomList>false</RequiredRoomList>
        <InformCancelPolicies>true</InformCancelPolicies>
        <InformBindingPriceValuation>true</InformBindingPriceValuation>
        <InformBindingPrice>true</InformBindingPrice>
        <InformNRFValuation>true</InformNRFValuation>
        <InformNRFRate>true</InformNRFRate>
        <Inform55Rate>true</Inform55Rate>
        <InformPackageRate>true</InformPackageRate>
        <InformExtraActivity>false</InformExtraActivity>
        <InformForfait>true</InformForfait>
        <RemarksValuation>true</RemarksValuation>
        <MaxNumberRoomCandidates>9</MaxNumberRoomCandidates>
        <MaxPaxInRoomCandidates>9</MaxPaxInRoomCandidates>
        <Release>0</Release>
        <MinimumStay>0</MinimumStay>
        <InformBillingSupplierReservation>false</InformBillingSupplierReservation>
        <ImplementsProvideLocatorReservationRead>true</ImplementsProvideLocatorReservationRead>
        <ImplementsClientLocatorReservationRead>true</ImplementsClientLocatorReservationRead>
        <ImplementsCancel>true</ImplementsCancel>
        <InformPriceReservation>true</InformPriceReservation>
        <HotelListLanguages>
            <Languages>
                <Language>en</Language>
                <Language>es</Language>
                <Language>de</Language>
                <Language>pt</Language>
                <Language>fr</Language>
                <Language>it</Language>
            </Languages>
        </HotelListLanguages>
        <ReservationListCreationDate>true</ReservationListCreationDate>
        <ReservationListCheckDate>true</ReservationListCheckDate>
        <HotelListType>OffLineCompleted</HotelListType>
        <DescriptiveInfoType>NotImplemented</DescriptiveInfoType>
        <GeographicDestinationTreeType>OffLine</GeographicDestinationTreeType>
        <AvailDestinationTreeType>OffLine</AvailDestinationTreeType>
        <RoomListType>OnLine</RoomListType>
        <InformCancelPoliciesReservationRead>false</InformCancelPoliciesReservationRead>
        <InformCancelPoliciesReservationList>false</InformCancelPoliciesReservationList>
        <InformCancelPoliciesAvail>false</InformCancelPoliciesAvail>
        <InformChangesPolicies>false</InformChangesPolicies>
        <ImplementsDeltaPrice>false</ImplementsDeltaPrice>
        <RequiredAllPassengers>true</RequiredAllPassengers>
        <InformBedsAvail>false</InformBedsAvail>
        <InformModificationPolicies>false</InformModificationPolicies>
        <ModifyTransactions>
            <ModifyTransaction>
                <Modify>ModifyStartDateAddDays</Modify>
                <Modify>ModifyEndDateAddDays</Modify>
            </ModifyTransaction>
            <ModifyTransaction>
                <Modify>ModifyHolder</Modify>
                <Modify>ModifyRoomsAddRooms</Modify>
                <Modify>ModifyRoomsRemoveRooms</Modify>
            </ModifyTransaction>
        </ModifyTransactions>
        <AllowsCurrencyAvail>true</AllowsCurrencyAvail>
        <InformCancelPoliciesModify>false</InformCancelPoliciesModify>
        <AllowOnRequest>false</AllowOnRequest>
        <ImplementsDailyRatePlan>false</ImplementsDailyRatePlan>
        <AllowRemarks>false</AllowRemarks>
        <InformSharedBed>false</InformSharedBed>
        <InformBedType>false</InformBedType>
        <InformNumberOfBeds>false</InformNumberOfBeds>  
        <AllowBlockOption>false</AllowBlockOption>  
        <InformExclusiveDeal>false</InformExclusiveDeal>    
        <InformPriceCancel>false</InformPriceCancel>
        <AllowUrlCard>false</AllowUrlCard>
        <InformCancelPoliciesDescription>false</InformCancelPoliciesDescription>        
        <PaymentTypes>
             <PaymentType>LaterPay</PaymentType>
             <PaymentType>MerchantPay</PaymentType>
        </PaymentTypes>     
        <InformAvailableModificationsInReservationRead>false</InformAvailableModificationsInReservationRead>    
        <RequiredNationality>false</RequiredNationality>    
        <Inform60Rate>false</Inform60Rate>
        <Inform65Rate>false</Inform65Rate>
        <InformCanaryResidentRate>false</InformCanaryResidentRate>
        <InformBalearicResidentRate>false</InformBalearicResidentRate>
        <InformLargeFamilyRate>false</InformLargeFamilyRate>
        <InformHoneymoonRate>false</InformHoneymoonRate>        
        <ImplementsBusinessRules>false</ImplementsBusinessRules>    
        <ImplementsProviderLocatorCancel>false</ImplementsProviderLocatorCancel>    
        <ImplementsClientLocatorCancel>false</ImplementsClientLocatorCancel>            
        <NumMarketsAllowed>5</NumMarketsAllowed>            
        <InformTiket>false</InformTiket>
        <ImplementsDescriptiveInfoExtended>false</ImplementsDescriptiveInfoExtended>
        <InformNumberOfUnits>true</InformNumberOfUnits>     
    </StaticConfigurationRS>



StaticConfigurationRS Description
=================================


| **Element**				| **Number**	| **Type**	| **Description**						|
| ------------------------------------- | ------------- | ------------- | ------------------------------------------------------------- |
| StaticConfigurationRS			| 1        	|		| Root node.							|
| MaxNumberHotels      			| 1   		| Integer	| Maximum number of hotel that can be requested in a avail petition. |
| MaxNumberCities      			| 1   		| Integer	| Maximum number of cities that can be requested in a avail petition. |
| MaxNumberZones       			| 1   		| Integer	| Maximum number of zones that can be requested in a avail petition. |
| MaxNumberGeoCodes    			| 1   		| Integer	| Maximum number of GeoCodes that can be requested in a avail petition.|
| RequiredRoomList     			| 1   		| Boolean	| The provider has implemented a list of rooms, where the provider will return the description of the room in availability, not a mandatory call.	|
| InformCancelPolicies 			| 1   		| Boolean	| The provider informs of the cancellation policies.		|
| InformBindingPriceValuation		| 1   		| Boolean	| Informs if the price of the option in the response of valuation is binding.	 |
| InformBindingPrice   			| 1   		| Boolean	| Provider returns binding PVPs in availability.		|
| InformNRFValuation   			| 1   		| Boolean	| The provider can inform in valuation if the rate is non-refundable. |
| InformNRFRate        			| 1   		| Boolean	| The provider can inform in availability if the rate is non-refundable. |
| InformNRFRateByRoom   		| 1   		| Boolean	| The provider can inform in availability if the room is non-refundable. |
| Inform55Rate         			| 1   		| Boolean	| The provider informs the options with rates of pax of 55 years old or over in availability.	|
| InformPackageRate    			| 1   		| Boolean	| The provider informs the options with package rates in availability. These options cant be sold by separate, need to add a service (like a plane ticket).	|
| InformExtraActivity  			| 1   		| Boolean	| The provider informs of the possible option type Hotel+entrance.  |
| InformForfait        			| 1   		| Boolean	| The provider informs of the possible option type Hotel+Forfait.  |
| RemarksValuation     			| 1   		| Boolean	| The provider informs of the important observation in policies, like per example, supplies paid in the hotel.	|
| MaxNumberRoomCandidates		| 1   		| Integer	| Maximum number of room candidates that can be requested in the same avail request.	|
| MaxPaxInRoomCandidates		| 1   		| Integer	| Maximum number paxs in same room that can be requested in the same avail request.	|
| Release              			| 1   		| Integer	| Minimum days that is required in between booking date and checking date ( days in advance ). If the value is zero then there is no limitation.	|
| MinimumStay          			| 1   		| Integer	| Minimum number of days that are needed to be booked. If the value is zero then there is no limitation.  |
| InformBillingSupplier Reservation	| 1   		| Boolean	| Informs of the data of the external provider in the booking.	|
| ImplementsProvideLocator ReservationRead | 1   	| Boolean	| The provider implements the consult transaction with the **provider** localizator.	|
| ImplementsClientLocator ReservationRead | 1   	| Boolean	| The provider implements the consult transaction with the **client** localizator.	|
| ImplementsCancel     			| 1   		| Boolean	| The provider implements cancellation transaction.		|
| InformPriceReservation		| 1   		| Boolean	| The provider informs about the price in the reservation in the booking RS.	|
| HotelListLanguages   			| 1        	|		| Languages that the provider can return their information.	|
| HotelListLanguages/Languages		| 1        	|		|Languages.							| 
| HotelListLanguages/Languages /Language | 1..n 	| String	| Languages description.					|
| ReservationListCreationDate		| 1   		| Boolean	| The provider implements the list of bookings transaction by creation date.	|
| ReservationListCheckDate		| 1   		| Boolean	| The provider implements the list of bookings transaction by check in date.	|
| HotelListType        			| 1   		| Enum		| See the specification in Static-Type section_.		|
| DescriptiveInfoType  			| 1   		| Enum		| See the specification in Static-Type section_.		|
| GeographicDestination TreeType	| 1   		| Enum		| See the specification in Static-Type section_.		|
| AvailDestinationTreeType		| 1   		| Enum		| See the specification in Static-Type section_.		|
| RoomListType         			| 1   		| Enum		| See the specification in Static-Type section_.		|
| InformCancelPolicies ReservationRead	| 1   		| Boolean	| Informs of the cancellation policies in the booking consultation. |
| InformCancelPolicies ReservationList	| 1   		| Boolean	| Informs of the cancellation policies in the booking list.	|
| InformCancelPoliciesAvail		| 1   		| Boolean	| Informs of the cancellation policies in availability.		|
| InformChangesPolicies			| 1   		| Boolean	| The provider informs if there is an extra fee for any booking modification.	|
| ImplementsDeltaPrice 			| 1   		| Boolean	| Implemented a margin stipulated by the client for booking with a higher price (delta).	|
| RequiredAllPassengers			| 1   		| Boolean	| Needs all of the data (names and surnames) of all the pax in booking.|
| ImplementsOffersAvail			| 1   		| Boolean	|If it shows in availability the applied offers.		|
| ImplementsRemarksAvail		| 1   		| Boolean	| Observation and comments.					|
| AllowsCurrencyAvail  			| 1   		| Boolean	| If true, then it is possible to indicate the currency on a availability level.	|
| AllowOnRequest      	 		| 1   		| Boolean	| If true, then the provider specifies the on request status option on a availability, valuation, or reservation level. |
| InformCancelPoliciesModify		| 1   		| Boolean	| Informs of the cancellation policies in Modification call.	|
| ImplementsDailyPrice 			| 1   		| Boolean	| Specifies if the provider return the daily price in availability call.	|
| ImplementsDailyRatePlan		| 1   		| Boolean	| Specifies if the provider return the daily rate in availability call.|
| AllowRemarks         			| 1   		| Boolean	| Specifies if the provider allows send remarks in Reservation request.|
| InformSharedBed      			| 1   		| Boolean	| Specifies if the provider informs in availability response if beds in the room are shared.	|
| InformBedType        			| 1   		| Boolean	| Specifies if the provider informs in availability response the beds types.	|
| InformNumberOfBeds   			| 1   		| Boolean	| Specifies if the provider informs in availability response the number of beds for each room.	|
| AllowBlockOption     			| 1   		| Boolean	| Specifies if the provider block the option in valuation call.	|
| InformExclusiveDeal  			| 1   		| Boolean	| The provider indicates in one Hotel is an Exclusive Deal in HotelList and/or DescriptiveInfo.	|
| InformPriceCancel    			| 1   		| Boolean	| The provider informs about the cancelation price in the cancel response.	|
| AllowUrlCard         			| 1   		| Boolean	| Specifies if the provider allows url card data encode when the option type is LaterPay.	|
| InformCancelPolicies Description	| 1   		| Boolean	| Specifies if the provider inform the cancel policies in free text in Valuation response.	|
| ImplementsBusinessRules		| 1   		| Boolean	| Specifies if in this provider use the business rules in availability.|
| PaymentTypes         			| 1        	|		| List of payment types accepted by the supplier.		|
| PaymentTypes/PaymentType		| 1..n     	|		| Indicates the typology of payment (Merchant, Direct ...) .	|
| InformAvailableModifications InReservationRead | 1   	| Boolean	| Specifies if the provider inform the available modifications in	 ReservationReadRS.	 |
| RequiredNationality  			| 1   		| Boolean	| Specifies if the provider required the nationality in Avail, Valuation and Reservation call.	|
| Inform60Rate         			| 1   		| Boolean	| The provider informs the options with rates of pax of 60 years old or over in availability.	|
| Inform65Rate         			| 1   		| Boolean	| The provider informs the options with rates of pax of 65 years old or over in availability.	|
| InformCanaryResidentRate		| 1   		| Boolean	| The provider informs the options with canary resident rates in availability. These options cant be sold if the customer don't have this condition.	|
| InformCanaryResidentRate		| 1   		| Boolean	| The provider informs the options with balearic resident rates in availability. These options can't be sold if the customer don't have this condition.	|
| InformBalearicResidentRate		| 1   		| Boolean	| The provider informs the options with large family rates in availability. These options can't be sold if the customer don't have this condition.	|
| InformLargeFamilyRate			| 1   		| Boolean	| The provider informs the options with canary resident rates in availability. These options can't be sold if the customer don't have this condition.	|
| InformHoneymoonRate  			| 1   		| Boolean	| The provider informs the options with honeymoon rates in availability. These options can't be sold if the customer don't have this condition.	|
| ImplementsProviderLocatorCancel	| 1   		| Boolean	| The provider implements the cancel transaction with the **provider** localizator.	|
| ImplementsClientLocatorCancel		| 1   		| Boolean	| The provider implements the cancel transaction with the **client** localizator.	|
| InformModificationPolicies 		| 1   		| Boolean	| The provider informs of the modification policies in Valuation process.	|
| ModifyTransactions   			| 0..1     	|		| Modifications allowed by the supplier.			|
| ModifyTransactions /ModifyTransaction | 1..n     	|		| Modifications set allowed in the same request by the supplier. |
| ModifyTransactions /ModifyTransaction/Modify | 1..n   |  		| Modification type (ModifyStartDateAddDays, ModifyStartDateSubtractDays, ModifyEndDateAddDays, ModifyEndDateSubtractDays, ModifyHolder, ModifyRoomsAddRooms, ModifyRoomsRemoveRooms, ModifyMealPlan or ModifyAddComment). |
| NumMarketsAllowed    			| 1   		| Integer	| Number of markets that the provider support in the same request. |
| InformTiket          			| 1   		| Boolean	| The provider informs of the possible option type Hotel+Tiket.	|
| ImplementsDescriptive InfoExtended	| 1   		| Boolean	| It indicates whether the new DescriptiveInfo is implemented.	|
| InformNumberOfUnits  			| 1   		| Boolean	| The provider inform the number of units are available per room.  |
 


Detailed description
====================

**HotelListType, DescriptiveInfoType, GeographicDestinationTreeType,
AvailDestinationTreeType and RoomListType:**

If the parameter value is set as online, then the information of these
methods is obtained of the supplier system. On the other hand if the
parameter takes antoher value means that the process takes more than 4
minutes. In this case, we need to load the information process in our
BBDD. Information of these methods are updated every week.



In case that the provider return the status in process response in
avail, valuation or reservation you can filter this option if you send
the parameter <OnRequest>true</OnRequest>.

By default the following tags:

-   **ImplementsDailyRatePlan**
-   **InformSharedBed**
-   **InformBedType**
-   **InformNumberOfBeds**
-   **AllowBlockOption**
-   **InformPriceCancel**
-   **InformAvailableModificationsInReservationRead**
-   **RequiredNationality**
-   **Inform60Rate**
-   **Inform65Rate**
-   **InformCanaryResidentRate**
-   **InformBalearicResidentRate**
-   **InformLargeFamilyRate**
-   **InformHoneymoonRate**
-   **ImplementsProviderLocatorCancel**
-   **ImplementsClientLocatorCancel**
-   **NumMarketsAllowed**
-   **ImplementsDescriptiveInfoExtended**
-   **InformNumberOfUnits**

Rigth now, this tags are set up to false value, either because the
provider doesn't support it or because is not updated yet.



