---
title: RoomList
keywords: hotel, data structure, room list, list
sidebar: mydoc_sidebar
permalink: /developer-documentation/hotel/DSF/RoomList
---



### Method Goals


This method aims to return a list of the available rooms code, which
will be used in the availability response.



### Request Format


The request does not require any elements empty request.



### Response Format


The result returns a list of *RoomInfo*.



### Remarks


The maximum time, that is permitted in our system, before the connection
is closed, is of **240000** milliseconds.

This message must be implemented solely in case it can not be provided
the description is room in the hotel availability. ( It is indicated in
the *StaticConfiguration* )



### RoomListRQ Example




    <RoomListRQ>
    </RoomListRQ>



### RoomListRQ Description



| **Element**		| **Number**	| **Type**	| **Description**	|
| --------------------- | ------------- | ------------- | --------------------- |
| RoomListRQ 		| 1          	|		| Root node.		|
  



### RoomListRS Example


    <RoomListRS>
        <RoomsInfo>
             <RoomInfo>
                 <Code>DBLSTD</Code>
                  <Name>Doble Estandard</Name>
            </RoomInfo>
            <RoomInfo>
                <Code>DBLSUP</Code>
                <Name>Doble Superior</Name>
            </RoomInfo>
                ...
            <RoomInfo/>
        </RoomsInfo>
    </RoomListRS>



### RoomListRS Description



| **Element**		| **Number**	| **Type**	| **Description**	|
| --------------------- | ------------- | ------------- | --------------------- |
| RoomListRS 		| 1          	|		| Root node.		|
  



### Detailed description


**Room types & languages**

The language of the room description can be defined the RQ ( Common
Elements ) given that the provider supplies the selected language,
otherwise it will use a default language which in most cases will be
English. The standard languages are : English & Spanish.
