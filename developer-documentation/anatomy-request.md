---
title: Anatomy of Request
keywords:
sidebar: mydoc_sidebar
permalink: /developer-documentation/anatomy-request/
---

The request is composed basically of two parts: the hub structure and
then the XML petition.

The hub structure is a generic structure that wraps the XML petition
which will indicate the following information:

-   Hub credentials.
-   Hub timeoutMillisecond.
-   Petition version. Usually indicated with a 1.
-   Provider code which you wish to use.
-   Id to indicate the which provider is used in the petition. If in the
    request is inserted id = 1, the response will contain a refId = 1 (
    this will only be used in the multiAvail petition, in the rest of
    petition ID will be indicated with a 1 )

:

    <soapenv:Envelope
    xmlns:soapenv = "http://schemas.xmlsoap.org/soap/envelope/"
    xmlns:ns = "http://schemas.xmltravelgate.com/hub/2012/06"
    xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
    <soapenv:Header>
        <wsse:Security>
            <wsse:UsernameToken>
                <wsse:Username>xxxxxxxxxx</wsse:Username> <!--Hub Credentials-->
                <wsse:Password>xxxxxxxxxx</wsse:Password>
            </wsse:UsernameToken>
        </wsse:Security>
    </soapenv:Header>
       <soapenv:Body>
          <ns:Cancel>
             <ns:cancelRQ>
                <ns:timeoutMilliseconds>xxxxxx</ns:timeoutMilliseconds> <!--Hub timeoutMillisecond-->
                <ns:version>x</ns:version> <!--Petition version-->
                <ns:providerRQ>
                   <ns:code>xxx/ns:code> <!--Provider's code-->
                   <ns:id>x/ns:id> <!--Id-->
                   <ns:rqXML>
                      <!--XML petition, for example, a cancellation of a hotel reservation-->
                   </ns:rqXML>
                </ns:providerRQ>
             </ns:cancelRQ>
          </ns:Cancel>
       </soapenv:Body>
    </soapenv:Envelope>

|

**Remark:**

For each petition or call there will be **only one** supplier per
request, i.e. in this example displayed there is a cancellation
petition, where we will use the provider TEST with the provider code TST
(\<ns:code\>TST/ns:code\>), then the response of this call will be
exclusively for the provider TST.

The only exception where there is a possibility of using one or more
providers in the same petition is with the call Avail. To identify which
provider is used in the MultiAvail call is by using the field ID in the
request. For example, for TST the ID will be 1 (\<ns:id\>1/ns:id\>) and
for the provider TST2 the ID will be 2 (\<ns:id\>2/ns:id\>), then in the
response for the provider TST the refId will be 1 (\<refId\>1\</refId\>)
and for the second provider TST2 the refID will be 2
(\<refId\>2\</refId\>). This will be visually shown in the SOAP
Examples.

|
