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

blackList
----------

The blackList application executes actions for the blacklisted numbers.

.. code-block:: json

    {
        "blackList": {
            "name": "myNewBlackList",
            "action": {[]}
        }
    }

Default action is :ref:`hangup`.

.. _hangup:

hangup
------

Hangs up a channel, with an optional cause code supplied.

.. code-block:: json

    {
        "hangup": ""
    }

The default code is **NORMAL_CLEARING**. You can specify any code from the :ref:`hangup-cause-code-table`.
