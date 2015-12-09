.. _acr-scheme:

ACR Scheme
==========

`ACR 
<https://github.com/webitel/acr>`_ (Advanced Call Routing) JSON Scheme - routes call that match configured rules. ACR Schemes are separated in two different route for different kinds of calls:

* **Default Route** handles calls originating from internal extensions 
* **Public Route** handles calls originating from the public phone network (`PSTN
  <http://en.wikipedia.org/wiki/Public_switched_telephone_network>`_).

Default Route Example
---------------------

.. code-block:: json 

    {
      "destination_number": "^\\+?3?8?(044\\d{7})$",
      "name": "Kyiv",
      "domain": "webitel.ua",
      "order": 1,
      "callflow": [
        {
          "setVar": [
            "effective_callee_id_number=380442228392",
          ]
        },
        {
          "recordSession": "start"
        },
        {
          "bridge": {
            "endpoints": [
              {
                "type": "sipGateway",
                "name": "kyiv",
                "dialString": "&reg0.$1"
              }
            ]
          }
        }
      ]
    }

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
