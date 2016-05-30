---
title: Data Structure
...

The structure of the API specification follows a standard. This document
intends to explain every aspect of this structure and their fields.

|

The integration will have the following methods:

|

+-----------------+----------------+----------------+---------+----------------------+
| Method          | Input          | Output         | Require | escription           |
|                 |                |                | d       |                      |
|                 |                |                | | D     |                      |
+=================+================+================+=========+======================+
| Disponibilidad  | Disponibilidad | Disponibilidad | Yes | M | akes a availability  |
|                 | RQ             | RS             |         | call                 |
+-----------------+----------------+----------------+---------+----------------------+
| Valoracion      | ValoracionRQ   | ValoracionRS   | Yes | M | akes a pre-booking   |
+-----------------+----------------+----------------+---------+----------------------+
| Suplementos     | SuplementosRQ  | SuplementosRS  | Yes | G | ets available        |
|                 |                |                |         | supplements          |
+-----------------+----------------+----------------+---------+----------------------+
| Reserva         | ReservaRQ      | ReservaRS      | Yes | M | akes a booking       |
+-----------------+----------------+----------------+---------+----------------------+
| Emitir          | EmitirRQ       | EmitirRS       | No | I  | ssues a ticket       |
+-----------------+----------------+----------------+---------+----------------------+
| Rutas           | RutasRQ        | RutasRS        | Yes | G | ets a static routes  |
|                 |                |                |         | list                 |
+-----------------+----------------+----------------+---------+----------------------+
| Transportes     | TransportesRQ  | TransportesRS  | No | G  | ets a static list of |
|                 |                |                |         | ransportations with  |
|                 |                |                | :   t   | routing info         |
+-----------------+----------------+----------------+---------+----------------------+
| RecuperaReserva | RecuperarReser | RecuperarReser | No | G  | ets booking details  |
|                 | vaRQ           | vaRS           |         |                      |
+-----------------+----------------+----------------+---------+----------------------+
| RecuperaListaRe | RecuperarLista | RecuperarLista | No | G  | ets booking list     |
| serva           | ReservaRQ      | ReservaRS      |         |                      |
+-----------------+----------------+----------------+---------+----------------------+
| CancelarReserva | CancelarReserv | CancelarReserv | No | C  | ancels a booking     |
|                 | aRQ            | aRS            |         |                      |
+-----------------+----------------+----------------+---------+----------------------+

|

Each request sent to the **service url** requires a node called rqXML .
Inside this node travels the current method's Input object.

|

The data structure will always have common elements in all objects and
the specific objects related to the operation

|

**Data structure content:**

> maxdepth
>
> :   3
>
> numbered
>
> :   
>
> Common-Elements\<./DSF/common-elements.rst\> Avail\<./DSF/avail.rst\>
> Valuation\<./DSF/valuation.rst\> Supplements \<./DSF/supplement.rst\>
> Reservation\<./DSF/reservation.rst\> Ticket
> issue\<./DSF/ticket-issue.rst\> Routes \<./DSF/routes.rst\>
> Transportation Batch\<./DSF/transportation-batch.rst\> Recover
> Reservation \<./DSF/recover-reserve.rst\> Recover Reservation List
> \<./DSF/recover-reserve-list.rst\> Cancel\<./DSF/cancel.rst\> Void
> \<./DSF/void.rst\> Refund \<./DSF/refund.rst\>
> Queue\<./DSF/queue.rst\> Discount Verification
> \<./DSF/verification-discount.rst\> Code Lists
> \<./DSF/codes-list.rst\>
