---
title: DestinationsTree
keywords: transfers, destination tree, destination
sidebar: mydoc_sidebar
permalink: /developer-documentation/transfers/DSF/destionationtree
---

|

Method Goals
============

This method aims to return all the available destinations for the
selected carrier.

|

Remarks
=======

This method should be cached internally and only called once a week and
in most cases once a month. The hierarchically structure of the tree is
defined by the provider.

|

DestinationsTreeRQ Example
==========================

:

    <DestinationsTreeRQ>
        <timeoutMilliseconds>60000</timeoutMilliseconds>
        <source>
            <agencyCode>test</agencyCode>
            <languageCode>es</languageCode>
        </source>
        <filterAuditData>
            <registerTransactions>false</registerTransactions>
        </filterAuditData>
        <Configuration codeProvider = "XXX">
            <Credentials user = "XXX" password = "XXX">
                <UrlGeneric>XXX</UrlGeneric>
                <UrlIdentification xsi:nil = "true"/>
                <UrlAvailability xsi:nil = "true"/>
                <UrlRateRule xsi:nil = "true"/>
                <UrlBook xsi:nil = "true"/>
                <UrlsSpecific xsi:nil = "true"/>
            </Credentials>
            <Attributes></Attributes>
        </Configuration>
    </DestinationsTreeRQ>

|

DestinationsTreeRQ Description
==============================

The request just contains the elements of BaseRQ.

  ------------------------------------------------------------------------
  Element             Num Type     Description
                      ber          
  ------------------- --- -------- ---------------------------------------
  DestinationsTreeRQ  1            Root node.
  ------------------------------------------------------------------------

|

DestinationsTreeRS Example
==========================

:

    <DestinationsTreeRS>
        <auditData>
            <timeStamp>2014-09-11T15:08:20.7037707+01:00</timeStamp>
            <processTimeMilliseconds>0</processTimeMilliseconds>
        </auditData>
        <operationImplemented>true</operationImplemented>
        <Destination code="000" name = "xxxx" type="CTY" avail = "true">
            <Child code="111" />
            <Child code="222" />
        </Destination>
        <Destination code="111" name = "Xxxx" type="ARP" avail = "true">
            <Child code="444" />
            <Child code="222" />
        </Destination>
        <Destination code="222" name = "Xxxx" type="ZON" avail = "true">
            <Child code="444" />
            <Child code="333" />
            <Child code="XXX" />
            <Child code="XXX" />
            <Child code="XXX" />
            <Child code="XXX" />
        </Destination>
        <Destination code="333" name = "Xxxx" type="OTH" avail = "false">
            <Child code="XXX" />
            <Child code="XXX" />
            <Child code="XXX" />
            <Child code="XXX" />
            <Child code="XXX" />
            <Child code="XXX" />
            <Child code="XXX" />
            <Child code="XXX" />
            <Child code="XXX" />
            <Child code="XXX" />
            <Child code="XXX" />
        </Destination>
        <Destination code = "444" name = "Xxxx" type = "HOT" avail = "true"/>
    ...
    </DestinationsTreeRS>

|

DestinationsTreeRS Description
==============================

The response returns a list of Destination with a code that identifies
it in the provider's system. The Destination object also contains a list
of Child , these children contain the code that identifies the
destinations that hang from that "Parent" destination. Usually not all
Destination are available for booking so we added the boolean avail that
indicates if this code can be used on the Availability method.

  --------------------------------------------------------------------------
  Element   Num Type  Description
            ber       
  --------- --- ----- ------------------------------------------------------
  Destinati 1         Root Node
  onsTreeRS           

  Destinati 1.. Desti Contains a list of Destinations. Each destination
  onsTreeRS n   natio contains its own information and a list of children
  /Destinat     n     (destinations of a lower level that belong to this
  ion                 destination).

  @Destinat 1   Strin Contains the code that must be used in Availability in
  ion/code      g     order to Search for this location.

  @Destinat 1   Strin It is the full name of the destination in the
  ion/name      g     provider's system.

  @Destinat 1   eLoca Indicates the type of location. This information must
  ion/type      tionT be sent in the AvailabilityRQ too. The possible values
                ype   are: **CTY**; **ZON**; **ARP**; **STA**; **PRT**;
                      **HOT**; **PDI** and **OTH**.

  @Destinat 1   Boole Indicates if this code can be used on the Availability
  ion/avail     an    method in order to obtain results.

  @Destinat 0.. Child Contains a list of children (destinations of a lower
  ion/Child n         level that belong to this destination).

  @Child/co 1   Strin Indicates the destination code of the child. The
  de            g     information of the child is explained in the specific
                      destination with this code.

  @Destinat 1   Posit This object contains the geolocation coordinates of
  ion/Posit     ion   the destination.
  ion                 

  @Position 1   Strin Indicates latitude value of geolocation.
  /latitude     g     

  @Position 1   Strin Indicates longitude value of geolocation.
  /longitud     g     
  e                   
  --------------------------------------------------------------------------

|
