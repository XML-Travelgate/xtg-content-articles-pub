---
title: GeographicDestinationTree
keywords: hotel, data structure, destination tree, geographic destination tree
sidebar: mydoc_sidebar
permalink: /docs/hotel/DSF/GeographicDestinationTree
---



### Method Goals


This method returns the provider's geographic tree where each node
indicates whether the call is accessible from availability which is
indicate with a parameter with values of true and false. The main
difference between the methods GeographicalTree and DestinationTree is
that GeographicalTree has this boolean parameter.



### Request Format


The request not requires any element, it is empty.



### Response Format


The result returns a list of *DestinationTree* with corresponding
sub-destinations.



### Remarks


The maximum time, that is permitted in our system, before the connection
is closed, is of **240000** milliseconds.



### GeographicDestinationTreeRQ Example


~~~xml
    <GeographicDestinationTreeRQ>
    </GeographicDestinationTreeRQ>
~~~


### GeographicDestinationTreeRQ Description




| **Element**		      | **Number** | **Type** | **Description**	|
| --------------------------- | ---------- | -------- | --------------- |
| GeographicDestinationTreeRQ | 1          |	      | Root node.	|



### GeographicDestinationTreeRS Example


~~~xml
    <GeographicDestinationTreeRS>
        <DestinationTree code = "ES" name = "España" avail = "False">
            <DestinationLeaf code = "BAL"/>
            <DestinationLeaf code = "AST"/>
            <DestinationLeaf code = "AND"/>
        </DestinationTree>
        <DestinationTree code= "IT" name = "Italia" avail = "False">
            <DestinationLeaf code = "AA"/>
            <DestinationLeaf code = "BB"/>
            . . .
        </DestinationTree>
        <DestinationTree code = "EN" name = "England" avail = "False">. . .</DestinationTree>
        <DestinationTree code = "BAL" name = "Baleares" avail = "True">
            <DestinationLeaf code = "PAL0"/>
            <DestinationLeaf code = "ALC0"/>
        </DestinationTree>
        <DestinationTree code = "AST" name = "Asturias" avail = "True"/>
        <DestinationTree code = "AND" name = "Andalucia" avail = "True"/>
        . . .
        <DestinationTree code = "PAL0" name = "Palma de Mallorca" avail = " True"/>
        <DestinationTree code = "ALC0" name = "Alcudia" avail = " True"/>
        . . .
    </GeographicDestinationTreeRS>
~~~


### GeographicDestinationTreeRS Description




| **Element**			| **Number** | **Type** | **Description**	|
| ----------------------------- | ---------- | -------- | --------------------- |
| GeographicDestinationTreeRS	| 1          | 		| Root node.		|
| DestinationTree		| 1..n       |		| Father node.		|
| DestinationLeaf		| 0..1       |		| Child node.		|



### Detailed description


~~~xml
    <GeographicDestinationTreeRS>
     <DestinationTree code = "ES" name = "España" avail = "False">
         <DestinationLeaf code = "BAL"/>
         <DestinationLeaf code = "AST"/>
         <DestinationLeaf code = "AND"/>
     </DestinationTree>
     <DestinationTree code= "IT" name = "Italia" avail = "False">
         <DestinationLeaf code = "AA"/>
         <DestinationLeaf code = "BB"/>
         . . .
     </DestinationTree>
     <DestinationTree code = "EN" name = "England" avail = "False">. . .</DestinationTree>

     <DestinationTree code = "BAL" name = "Baleares" avail = "True">
         <DestinationLeaf code = "PAL0"/>
         <DestinationLeaf code = "ALC0"/>
     </DestinationTree>
     <DestinationTree code = "PAL0" name = "Palma de Mallorca" avail = " True"/>
         <DestinationLeaf code = "SAR"/>
         <DestinationLeaf code = "IND"/>

     <DestinationTree code = "AST" name = "Asturias" avail = "True"/>
     <DestinationTree code = "AND" name = "Andalucia" avail = "True"/>
     . . .
     <DestinationTree code = "ALC0" name = "Alcudia" avail = " True"/>
     <DestinationTree code = "SAR" name = "Son Sardina" avail = "false"/>
     <DestinationTree code = "IND" name = "Indioteria" avail = "false"/>
     . . .
    </GeographicDestinationTreeRS>
~~~


There are two primordial definitions that needs to be clear to
understand the difference in city and zone: types of nodes and if these
nodes are attackable or not.

Lets start with the two types of nodes. First there is the parent node,
also named DestinationTree node, and the child node, also named
Destination leaf node. A parent can have zero to n children ( 0..n ) and
a child will have only one parent ( 1..1 ). For example, the
DestinationTree code = "ES" is the parent of the DestinationLeaf code =
"BAL", "AST" and "AND" and at the same time DestinationTree code = "BAL"
is also a the parent of the DestinationLeaf code = "PAL0" and "ALC0",
and so on.

Attackable on an **availability** level means that it is possible doing
an avail for that zone. A node is attackable when the tag avail is set
as true, if it is set as false the node is not attackable and
consequently it is not available.

Therefore:

-   **City:** Lowest attackable node.
-   **Zone:** Not the lowest attackable node.



 **Note:** *In rare occasions it is possible finding nodes lower than cities, which won't be attackable, but the standard scenario is not to find lower nodes than cities.*

