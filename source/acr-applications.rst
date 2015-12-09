.. _acr-applications:

Callflow Applications
=====================

answer
------

Answers an incoming call or session.

.. code-block:: json

   {
       "answer": "200 OK"
   }

+------------+-------------------------------------------------------------------------------------+
| 200 OK     |  Session Description Protocol (SDP) message that is sent by an answerer in response |
|            |  to an offer that is received from an offerer.                                      |
+------------+-------------------------------------------------------------------------------------+
| 183 Session| Establishes media (SDP) but does not answer. Is equivalent to a SIP status code     |
| Progress   | 183 with SDP.                                                                       |
+------------+-------------------------------------------------------------------------------------+
| 180 Ringing|  Is equivalent to a SIP status code 180 Ringing without SDP.                        |
+------------+-------------------------------------------------------------------------------------+
