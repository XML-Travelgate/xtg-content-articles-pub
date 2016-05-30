---
title: Common Elements
keywords: common elements, elements, hotel
sidebar: mydoc_sidebar
permalink: /developer-documentation/hotel/DSF/Common-Elements
---



This node will be in every request and response objects.

The request objects contains the provider's configuration, urls and
credentials.

The response object contains the operation status and errors if any.



### Common Elements RQ Example


    <HotelBaseRQ>
        <echoToken>TEST</echoToken>
        <timeoutMilliseconds>20000</timeoutMilliseconds>
        <source>
            <agencyCode>XXXX</agencyCode>
            <languageCode>es</languageCode>
        </source>
        <filterAuditData>
            <registerTransactions>True</registerTransactions>
        </filterAuditData>
        <optionsQuota>500</optionsQuota>
        <ContinuationToken expectedRange = "6000"></ContinuationToken>
        <Configuration>
            <User>USERXX</User>
            <Password>PWXX</Password>
            <UrlAvail>www.proveedor.es/avail</UrlAvail>
            <UrlReservation>www.proveedor.es/reservation</UrlReservation>
            <UrlValuation>www.proveedor.es/valuation</UrlValuation>
            <UrlGeneric>www.proveedor.es</UrlGeneric>
            <Parameters>
                <Parameter key = "SegundoPW" value = "PWXML"/>
            </Parameters>
        </Configuration>
        …
    </HotelBaseRQ>



### Common Elements RQ Description



| **Element**                          | **Number** | **Type** | **Description** |
| ------------------------------------ | ---------- | -------- | --------------- |
| HotelBaseRQ                          | 1          |          | Root node. |
| echoToken                            | 0..1       | String   | Echo token to be returned in response (valid for test purposes). |
| timeoutMillisencods                  | 1          | Integer  | Timeout in milliseconds that client will be waiting that response. |
| source                               | 1          |          |  	Information about source requesting the operation. |
| source/agencyCode                    | 0..1       | String   |  	Agency code that requests the operation. |
| source/languageCode                  | 1          | String   |  	Language code (ISO 3166-1 alpha-2) format lowercase. |
| filterAuditData                      | 1          |          | Enables or disables information returned in audit data. |
| filterAuditData/registerTransactions | 1          | Boolean  | Returns all the transactions (XMLs) exchanged with the provider.|
| optionsQuota                         | 0..1       | Integer  | Numbers of options wanted by MealPlan. |
| ContinuationToken                    | 0..1       | String   | Internal Token to identify the next set of HotelList. |
| @expectedRange                       | 0..1       | Integer  |  	Number of hotels expected in HotelList call. |
| Configuration                        | 1          |          |  	Information about source requesting the operation. |
| Configuration/User                   | 0..1       | String   | User code for connection. |
| Configuration/Password               | 0..1       | String   | Password for the connection. |
| Configuration/UrlGeneric             | 0..1       | String   | Url generic connection. |
| Configuration/UrlAvail               | 0..1       | String   | Url for Avail method. |
| Configuration/UrlValuation           | 0..1       | String   | Url for Valuation method. |
| Configuration/UrlReservation         | 0..1       | String   |  	Url for Reservation method. |
| Configuration/Parameters             | 0..1       |          | Parameters for additional information. |
| Configuration/Parameters/Parameter   | 0..n       |          | List of parameter. |
| @key                                 | 1          | String   | Contains the keyword/Id to identify a parameter. |
| @value                               | 1          | String   | Contains the value of the parameter. |



### Detailed description


**optionsQuota:**

This new tag will be used just for those suppliers that return a really
big quantity of options into availability response (more than 20.000
options in the same response). It is impractible treat so much options
for us and for the client. In order to avoid this issue the client will
be able to decide numbers of options wanted by MealPlan, as long as the
provider returns it in this call (see StaticConfiguration
*ImplementsBusinessRule*). In case that the provider will have
ImplementsBusinessRule = True, the client can choose between different
business rules to filter the options they are interested in (see in
Avail). We also have a system level limit, if the OptionsQuota sent by
the client is different than the established by us, we use the minimum
of those two values. This way, the rest of the traffic won't be
affected.



### Common Elements RS Example


    <HotelBaseRS>
        <echoToken>TEST</echoToken>
        <OperationImplemented>true</OperationImplemented>
        <ContinuationToken expectedRange = "4000">&lt;?xml version="1.0" encoding="utf-16"?&gt;&lt;ContinuationToken&gt;&lt;ContinuationToken&gt;&lt;Version&gt;2.0&lt;/Version&gt;&lt;Type&gt;Table&lt;/Type&gt;&lt;NextPartitionKey&gt;1!24!bG93Y29zdGhvbGlkYXlfWk1U&lt;/NextPartitionKey&gt;&lt;NextRowKey&gt;1!40!bG93Y29zdGhvbGlkYXlfWk1UXzBoNFIlMjNvcXBr&lt;/NextRowKey&gt;&lt;TargetLocation&gt;Primary&lt;/TargetLocation&gt;&lt;/ContinuationToken&gt;&lt;/ContinuationToken&gt;</ContinuationToken>
        <applicationErrors>
            <type>102</type>
            <code>xxx</code>
            <description>xxx</description>
        </applicationErrors>
        …
        <auditData>
            <transactions>
                <timeStamp>2011-10-6T15:19:45.3544495+02:00</timeStamp>
                <RQ/>
                <RS/>
            </transactions>
            …
            <timeStamp>2011-10-26T15:19:43.4014745+02:00</timeStamp>
            <processTimeMilliseconds>19532</processTimeMilliseconds>
        </auditData>
        …
    </HotelBaseRS>



### Common Elements RS Description


| **Element**                       | **Number** | **Type** | **Description**|
| --------------------------------- | ---------- | -------- | -------------- |
| HotelBaseRS                       | 1          |          | Root node.     |
| echoToken                         | 0..1       | String   | Echo token to be returned in response (valid for test purposes). |
| OperationImplemented              | 1          | Boolean  | If the operation is implemented by this provider or not. |
| ContinuationToken                 | 0..1       | String   | Internal Token to identify the next set of HotelList. |
| @expectedRange                    | 0..1       | Integer  | Number of hotels expected in HotelList call. |
| applicationErrors                 | 0..n       |          | Application errors reported by provider. |
| applicationErrors/type            | 1          | String   | Error Type as specified by XML Travelgate. |
| applicationErrors/code            | 1          | String   | Native error code reported by provider. |
| applicationErrors/description     | 1          | String   | Error description. |
| auditData                         | 1          |          | Information about processing that transaction. |
| auditData/transactions            | 0..n       |          | List of transactions communicated with provider. |
| auditData/transactions/timeStamp  | 1          | Integer  | TimeStamp in which has been generated that transaction. |
| auditData/transactions/RQ         | 1          | String   | Transaction Request. |
| auditData/transactions/RS         | 1          | String   | Transaction Response. |
|auditData/timeStamp                | 1          | Integer  | TimeStamp in which response has been generated. |
| auditData/processTimeMilliseconds | 1          | Integer  | Time in milliseconds consumed by this method. |



### Detailed description


**ContinuationToken:**

This new tag is useful to split the hotel list response. This is done
because there are suppliers that have a big amount of hotels (over
250.000). In those cases, the response has to be splitted in order to
get all the hotels. In case that ContinuationToken is not sent, the
HotelList returns a maximum of 250.000 hotels. Using this
ContinuationToken and the attribute *expectedRange* the client may
decide the number of hotels expected in each HotelList call. If the
provider has more hotels than the amount mentioned before, in order to
get all the hotels the client will need to do requests using the
ContinuationToken returned inside the HotelListRS response until the
ContinuationToken field is not returned in the response (see the example
in Common Elements RS). Once the tag is not returned the hotel list is
completed. The value of this tag is an internal Token that identifies
the next set of HotelList to be returned.

-   *expectedRange* :

Hotel list range that the client want to get in each HotelList response.
The number of hotels returned will be established in the expectedRange
value, though it is possible to get more hotels than the requested.
Having the list of hotels paged we can not return a range of hotels in
one page so we are forced to set a range of +999 hotels. This means that
if the client request 6000 hotels, the response may contain a range of
6000 to 6999 hotels. In case that this value is not sent, the maximum
hotel range is 250.000 although it is recommended to make requests of
multiple of 1000.


