---
title: RoomList
keywords: hotel, data structure, room list, list
search: Hotel - Data Structure - RoomList
sidebar: mydoc_sidebar
permalink: /docs/hotel/DSF/RoomList
---



### Method Goals


This method aims to return a list of the available room codes which
will be used in the availability response.



### Request Format


The request does not require any elements - empty request.



### Response Format


The result returns a list of *RoomInfo*.



### Remarks


The maximum time permitted in our system before the connection is closed is **240000** milliseconds.

This message must be implemented solely in case the supplier does not return room description in Avail. This requirement will be indicated in *StaticConfiguration*.



### RoomListRQ Example


~~~xml
    <RoomListRQ>
    </RoomListRQ>
~~~


### RoomListRQ Description



| **Element**		| **Number**	| **Type**	| **Description**	|
| --------------------- | ------------- | ------------- | --------------------- |
| RoomListRQ 		| 1          	|		| Root node.		|
  



### RoomListRS Example


~~~xml
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
~~~


### RoomListRS Description



| **Element**		| **Number**	| **Type**	| **Description**	|
| --------------------- | ------------- | ------------- | --------------------- |
| RoomListRS 		| 1          	|		| Root node.		|
  



### Detailed description


**Room types & languages**

You can define in AvailRQ (Common Elements) which language you want the room description returned in  - as long as the supplier supports the selected language, otherwise the default language is most commonly English. The standard languages are: English & Spanish.
