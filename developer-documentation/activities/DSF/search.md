---
title: Search
...

|

Method Goals
============

This method aims to return all the available activities for the selected
carrier.

|

Request Format
==============

The request requires a POS object.

|

Response Format
===============

The result returns a list of activities with the corresponding
information.

|

Remarks
=======

This method should be cached internally for know activities codes that
can will return.

|

Search RQ\_ Example
===================

:

    <OTA_TourActivitySearchRQ PrimaryLangID = "es">

          <SearchCriteria>


          </SearchCriteria>

    </OTA_TourActivitySearchRQ>

|

Search RQ\_ Description
=======================

  --------------------------------------------------------------------------
  Element              Number  Type    Description
  -------------------- ------- ------- -------------------------------------
  OTA\_TourActivitySea 1               Root node.
  rchRQ                                

  @PrimaryLangID       1       String  Language code (ISO 3166-1 alpha-2)
                                       format.

  SearchCriteria       0..1            Element where shall be the
                                       information for tickets.
  --------------------------------------------------------------------------

|

Search RS\_ Example
===================

:

    <OTA_TourActivitySearchRS>
        <TourActivityInfo>
            <BasicInfo Name = "Visita a la Casa de Madrid" TourActivityID = "CASAS1"/>
            <CategoryAndType>
                <Category Code = "" Extension = "Other"/>
            </CategoryAndType>
            <Location>
                <Region RegionCode = "568" RegionName = "Madrid"/>
                <Address>
                    <AddressLine>Avenida de la T?cnica 122</AddressLine>
                    <PostalCode/>
                    <County>ESPAA</County>
                </Address>
            </Location>
        </TourActivityInfo>
        .
        .
        .
    </OTA_TourActivitySearchRS>

|

Search RS\_ Description
=======================

  ------------------------------------------------------------------------
  Element              Numb Type Description
                       er        
  -------------------- ---- ---- -----------------------------------------
  OTA\_TourActivitySea 1         Root node.
  rchRS                          

  TourActivityInfo     1..n Stri Information about specific ticket.
                            ng   

  TourActivityInfo/Bas 0..1      Basic Information of ticket.
  icInfo                         

  @Name                0..1 Stri Name of ticket.
                            ng   

  @TourActivityID      0..1 Stri Code of ticket.
                            ng   

  TourActivityInfo/Cat 0..1      Category of Ticket.
  egoryAndType                   

  TourActivityInfo/Cat 0..1      Category of Ticket.
  egoryAndType/Categor           
  y                              

  @Code                0..1 Stri A category code from a predefined list,
                            ng   if Extension = "Other" then will be
                                 provider code.

  @Extension           0..1      Enter a category here if you have
                                 selected "Other" from the pre-defined
                                 list.

  Location             1         The location of the tour/ activity.

  Location/Region      1         Describes regional information.

  @RegionCode          1    Stri Specifies a region code.
                            ng   

  @RegionName          1    Stri Specifies the region name.
                            ng   

  Location/Address     0..1      Identifies the physical address of the
                                 tour departure and/or activity location.

  Location/Address/Add 0..1 Stri These lines will contain free form
  ressLine                  ng   address details.

  Location/Address/Pos 0..1 Stri Post Office Code number.
  talCode                   ng   

  Location/Address/Cou 0..1 Stri County or Region Name.
  nty                       ng   
  ------------------------------------------------------------------------

|
