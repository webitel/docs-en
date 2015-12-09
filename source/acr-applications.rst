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

Default action is :ref:`hangup` with **INCOMING_CALL_BARRED** code (See: :ref:`hangup-cause-code-table`).

bridge
------

Bridge a new channel to the existing one.Generally used to route an incoming call to one or more endpoints. Multiple endpoints can be dialed simultaneously or sequentially.

.. code-block:: json

    {
        "bridge": {
            "strategy": "multiple",
            "pickup": "mygroup",
            "parameters": ["instant_ringback=true"],
            "endpoints": [{
                "name": "gw_name1",
                "type": "sipGateway",
                "dialString": "&reg0.$1",
                "parameters": ["absolute_codec_string='PCMA,G729'"]
              },
              {
                "name": "1000",
                "type": "device"
              },
              {
                "name": "1001",
                "type": "user",
                "domainName": "10.10.10.144",
                "parameters": ["d=3"]
              }]
        }
    }

Endpoints types:

- **sipGateway** 
- **user**
- **device**

``strategy``
++++++++++++

- **multiple** - no limit to concurrency, first one to answer wins.
- **failover** -  no limit to failover number.

``pickup``
++++++++++

:ref:`pickup` group name. The pickup endpoint is a dummy channel that never answers to which you can originate from anywhere you can place calls.

``parameters``
++++++++++++++

Set variables to all endpoints. Some useful variables:

+--------------------------------------------+-------------------------------------------------------------------------------------+
| ``instant_ringback=true``                  | Ringback will not wait for indication before sending ringback tone to calling party.|
+--------------------------------------------+-------------------------------------------------------------------------------------+
| ``ignore_early_media=true``                | Ignore early media from the endpoint.                                               |
+--------------------------------------------+-------------------------------------------------------------------------------------+
| ``ignore_early_media=ring_ready``          | The same as ``ignore_early_media=true`` but also send a SIP 180 to the inbound leg  |
|                                            | when the first SIP 183 is caught.                                                   |
+--------------------------------------------+-------------------------------------------------------------------------------------+
| ``call_timeout=20``                        | Controls how long (in seconds) to ring the endpoint. Default is 60 seconds.         |
+--------------------------------------------+-------------------------------------------------------------------------------------+
| ``leg_timeout=15``                         | Can be used inside endpoints parameters only.                                       |
+--------------------------------------------+-------------------------------------------------------------------------------------+
| ``leg_delay_start=15``                     | Specifies a wait time in seconds before the leg is called.                          |
|                                            | Can be used inside endpoints parameters only.                                       |
+--------------------------------------------+-------------------------------------------------------------------------------------+
| ``origination_caller_id_number=911``       | Sets the origination CallerID number.                                               |
+--------------------------------------------+-------------------------------------------------------------------------------------+
| ``absolute_codec_string='PCMA,PCMU'``      | Sets the absolute codec string to use (nothing will be appended).                   |
+--------------------------------------------+-------------------------------------------------------------------------------------+
| ``sip_renegotiate_codec_on_reinvite=true`` | Allow SDP codec change with re-INVITE.                                              |
+--------------------------------------------+-------------------------------------------------------------------------------------+


conference
----------

The inbound and outbound conference bridge service.

.. code-block:: json

    {
        "conference": {
            "name": "ConferenceName",
            "pin": "1234" ,
            "flags": ["mute", "moderator"]
        }
    }


- **name** - Conference room name.
- **pin** - Pin code that must be entered before user is allowed to enter the conference.

+----------------+-----------------------------------------------------------------------------------------+
| Flags          | Description                                                                             |
+================+=========================================================================================+
| ``moderator``  | Flag member as a moderator.                                                             |
+----------------+-----------------------------------------------------------------------------------------+
| ``join-only``  | Only allow joining a conference that already exists.                                    |
+----------------+-----------------------------------------------------------------------------------------+
| ``vmute``      | Enter conference video muted.                                                           |
+----------------+-----------------------------------------------------------------------------------------+
| ``mute``       | Enter conference muted.                                                                 |
+----------------+-----------------------------------------------------------------------------------------+
| ``deaf``       | Enter conference deafed (can not hear conference); will also mute the mic.              |
+----------------+-----------------------------------------------------------------------------------------+
| ``endconf``    | Ends conference when all members with this flag leave the conference.                   |
+----------------+-----------------------------------------------------------------------------------------+
| ``mintwo``     | End conference when it drops below 2 participants after a member enters with this flag. |
+----------------+-----------------------------------------------------------------------------------------+
| ``nomoh``      | Disable music on hold when this member is the only member in the conference.            |
+----------------+-----------------------------------------------------------------------------------------+


echo
----

Simply returns all audio sent, including voice, DTMF, etc after the specified delay *milliseconds*.

.. code-block:: json

    {
        "echo": "0"
    }


goto
----

Immediately goto an another extension (or route) and exit from current extension.

.. code-block:: json

    {
        "goto": "my_extension"
    },
    {
        "goto": "public:my_extension"
    }

Goto extension called my_extension in the **current**, **default** or **public** route.


.. _hangup:

hangup
------

Hangs up a channel, with an optional cause code supplied.

.. code-block:: json

    {
        "hangup": ""
    }

The default code is **NORMAL_CLEARING**. You can specify any code from the :ref:`hangup-cause-code-table`.

httpRequest
-----------

.. code-block:: json

    {
        "httpRequest": {
                "url": "https://sales.bpmonline.com/0/ServiceModel/GetCallerOwnerService.svc/GetCallerOwner",
                "method": "POST",
                "headers": {
                    "Content-Type":"application/json"
                },
                "data": {
                    "callerIdNumber": "${caller_id_number}"
                },
                "exportVariables": {
                    "effective_caller_id_name": "callerIdName",
                    "owner_caller_id_number": "callerIdOwner"
                }
        }
    }


inBandDTMF
---------

You can use ``inBandDTMF`` to enable in-band DTMF detection (i.e. the detection of DTMF tones on a channel). You should do this when you want to be able to identify DTMF tones on a channel that doesn't otherwise support another signaling method (like RFC2833 or INFO).

.. code-block:: json

    {
      "inBandDTMF": "start"
    },
    {
      "inBandDTMF": "stop"
    }


log
---

Logs a string of text to the console.

.. code-block:: json

    {
        "log": "my log message"
    }

park
----

Places a channel "on hold" in the switch, instead of in the phone.

.. code-block:: json

    {
        "park": {
            "name": "myPark",
            "lot": "1000-2000",
            "auto": "in"
        }
    }

+----------+------------------------------------------------------------------------+
| ``name`` | Park lot name.                                                         |
+----------+------------------------------------------------------------------------+
| ``lot``  | Park lot number.                                                       |
+----------+------------------------------------------------------------------------+
| ``auto`` | Put caller to park (in) or retrieve (out) with "parking lot" numbers.  |
+----------+------------------------------------------------------------------------+

.. _pickup:

pickup
------

Permits proper answering of multiple simultaneous calls to the same pickup group.

.. code-block:: json

    {
        "pickup": "mygroup"
    }


