.. _acr-applications:

Callflow Applications
=====================

agent
-----

.. py:module:: agent

Modify agent status.

.. code-block:: json

   {
      "agent":  {
          "name": "1000",
          "status": "Available",
          "state":  "Waiting"
      }
   }

+--------+-------------------------------------------------------------------------------------+
| status |  Logged Out, Available, Available (On Demand) or On Break.                          |
+--------+-------------------------------------------------------------------------------------+
| state  |  Waiting or Idle.                                                                   |
+--------+-------------------------------------------------------------------------------------+

amd
---

.. py:module:: amd

Answering machine detection (voice activity detection).

.. code-block:: json

   {
     "amd":  {
        "maximumWordLength": 5000,
        "maximumNumberOfWords": 3,
        "betweenWordsSilence": 50,
        "minWordLength": 100,
        "totalAnalysisTime": 5000,
        "silenceThreshold": 256,
        "afterGreetingSilence": 800,
        "greeting": 1500,
        "initialSilence": 2500
        }
   }

+----------------------+------------------------------------------------------------+
| maximumWordLength    | Maximum duration of a single Voice utterance allowed       |
+----------------------+------------------------------------------------------------+
| maximumNumberOfWords | Maximum number of words in the greeting.                   |
|                      | If exceeded then MACHINE                                   |
+----------------------+------------------------------------------------------------+
| betweenWordsSilence  | Minimum duration of silence after a word to consider       |
|                      | the audio what follows as a new word                       |
+----------------------+------------------------------------------------------------+
| minWordLength        | Minimum duration of Voice to considered as a word          |
+----------------------+------------------------------------------------------------+
| totalAnalysisTime    | Maximum time allowed for the algorithm to decide           |
|                      | on a HUMAN or MACHINE                                      |
+----------------------+------------------------------------------------------------+
| afterGreetingSilence | Silence after detecting a greeting. If exceeded then HUMAN |
+----------------------+------------------------------------------------------------+
| greeting             | Maximum length of a greeting. If exceeded then MACHINE.    |
+----------------------+------------------------------------------------------------+
| initialSilence       | Maximum silence duration before the greeting.              |
|                      | If exceeded then MACHINE.                                  |
+----------------------+------------------------------------------------------------+

After the AMD execution, the variable **amd_result** and **amd_cause** will be set.

The variable **amd_result** will return one of the following results:

- NOTSURE: take this value if total_analysis_time is over and decision could not be made
- HUMAN: if a human is detected
- MACHINE: if a human is detected

The variable **amd_cause** will return one of the following results:

- INITIALSILENCE (MACHINE)
- SILENCEAFTERGREETING (HUMAN)
- MAXWORDLENGTH (MACHINE)
- MAXWORDS (MACHINE)
- LONGGREETING (MACHINE)
- TOOLONG (NOTSURE)

answer
------

.. py:module:: answer

Answers an incoming call or session.

.. code-block:: json

   {
       "answer": "200 OK"
   }

+----------------------+-------------------------------------------------------------------------------------------------+
| 200 OK               |  Session Description Protocol (SDP) message that is sent by an answerer in response to an offer |
|                      |  that is received from an offerer.                                                              |
+----------------------+-------------------------------------------------------------------------------------------------+
| 183 Session Progress | Establishes media (SDP) but does not answer. Is equivalent to a SIP status code 183 with SDP.   |
+----------------------+-------------------------------------------------------------------------------------------------+
| 180 Ringing          |  Is equivalent to a SIP status code 180 Ringing without SDP.                                    |
+----------------------+-------------------------------------------------------------------------------------------------+

blackList
----------

.. py:module:: blackList

The blackList application executes various actions for the blacklisted numbers.

.. code-block:: json

    {
        "blackList": {
            "name": "myNewBlackList",
            "number": "${caller_id_number}",
            "actions": [
                {
                    "hangup": "INCOMING_CALL_BARRED"
                }
            ]
        }
    }

Default action is :py:mod:`hangup` with **INCOMING_CALL_BARRED** code (See: :ref:`hangup-cause-code-table`).

bridge
------

.. py:module:: bridge

Bridge a new channel to the existing one.Generally used to route an incoming call to one or more endpoints. Multiple endpoints can be dialed simultaneously or sequentially.

.. code-block:: json

    {
        "bridge": {
            "strategy": "multiple",
            "pickup": "mygroup",
            "codecs": ["G729", "PCMA"],
            "parameters": ["instant_ringback=true"],
            "endpoints": [
                {
                "name": "gw_name1",
                "type": "sipGateway",
                "dialString": "$1",
                "parameters": ["sip_invite_params=user=phone"]
              },
              {
                "name": "1000",
                "type": "device",
                "parameters": ["leg_timeout=15"]
              },
              {
                "name": "1001",
                "type": "user",
                "domainName": "10.10.10.144",
                "parameters": ["leg_delay_start=15"]
              },
              {
                "type": "sipUri",
                "profile": "nonreg",
                "host": "wbtl.pstn.twilio.com",
                "dialString": "+1$1",
                "parameters": ["origination_caller_id_number=911"]
              }
            ]
        }
    }

endpoints types
+++++++++++++++

The `endpoints` block can contain not more than 15 endpoints.

- **sipGateway**
- **user**
- **device**
- **sipUri**

strategy
++++++++

- **multiple** - no limit to concurrency, first one to answer wins.
- **failover** -  no limit to failover number.

pickup
++++++

:py:mod:`pickup` group name. The pickup endpoint is a dummy channel that never answers to which you can originate from anywhere you can place calls.

parameters
++++++++++

+--------------------------------------------+-------------------------------------------------------------------------------------+
| ``continue_on_fail=true``                  | Controls what happens when the called party can not be reached (busy/offline).      |
|                                            | If "true" the dialplan continues to be processed. If "false" - will stop processing.|
+--------------------------------------------+-------------------------------------------------------------------------------------+
| ``instant_ringback=true``                  | Ringback will not wait for indication before sending ringback tone to calling party.|
+--------------------------------------------+-------------------------------------------------------------------------------------+
| ``ignore_early_media=true``                | Ignore early media from the endpoint.                                               |
+--------------------------------------------+-------------------------------------------------------------------------------------+
| ``ignore_early_media=ring_ready``          | The same as ``ignore_early_media=true`` but also send a SIP 180 to the inbound leg  |
|                                            | when the first SIP 183 is caught.                                                   |
+--------------------------------------------+-------------------------------------------------------------------------------------+
| ``hangup_after_bridge=true``               | Controls what happens to a calling (A) party when in a bridge state and the         |
|                                            | called (B) party hangs up. If "true" the dialplan will stop processing and the      |
|                                            | A leg will be terminated when the B leg terminates. If "false" (default) the        |
|                                            | dialplan continues to be processed after the B leg terminates.                      |
+--------------------------------------------+-------------------------------------------------------------------------------------+
| ``ignore_display_updates=true``            | Not to send display UPDATEs to the leg of the call. (update_display)                |
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
| ``sip_renegotiate_codec_on_reinvite=true`` | Allow SDP codec change with re-INVITE.                                              |
+--------------------------------------------+-------------------------------------------------------------------------------------+

uuid bridge
+++++++++++

Bridge two call legs together. **Bridge** needs atleast any one leg to be answered.

.. code-block:: json

    {
        "bridge": {
            "uuid": "${new_uuid}",
            "other_uuid": "${other_uuid}"
        }
    }

calendar
--------

.. py:module:: calendar

Set `true` or `false` into the variable when current datetime is in the Calendar.

.. code-block:: json

    {
        "calendar": {
            "name": "my Business Calendar",
            "extended": false,
            "setVar": "isWorkDay"
        }
    }

If `extended` is true, the varaible can takes additional values:

- holiday
- ahead
- expire

conference
----------

.. py:module:: conference

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

callback
--------

.. py:module:: callback

Add number to the callback queue.

.. code-block:: json

    {
        "callback": {
            "setVar": "return_value",
            "widget": "myWidget",
            "queue": "callbackQueueName",
            "number": "${caller_id_number}"
        }
    }

cdr
---

.. py:module:: cdr

Create search request into the CDR

.. code-block:: json

    {
        "cdr": {
            "exportVar": {
                "res": "aggregations.avgQueue.value"
            },
            "elastic": {
                "aggs": {
                    "avgQueue": {
                        "avg": {
                            "field": "Queue Answer Delay"
                        }
                    }
                },
                "limit": 0,
                "query": "",
                "filter": [
                {
                    "bool": {
                        "must": [
                            {
                                "term": {
                                    "variables.cc_queue": "myQueueName@domain.com"
                                    }
                                }
                            ]
                        }
                    }
                ]
            }
        }
    }

DTMF
----

`FreeSWITCH` attempts to negotiate `rfc2833` DTMF out-of-band transmission. The `INFO` DTMF is also supported.

inBandDTMF
++++++++++

.. py:module:: inBandDTMF

You can use ``inBandDTMF`` to enable in-band DTMF detection (i.e. the detection of DTMF tones on a channel). You should do this when you want to be able to identify DTMF tones on a channel that doesn't otherwise support another signaling method (like RFC2833 or INFO).

.. code-block:: json

    [{
      "inBandDTMF": "start"
    },
    {
      "inBandDTMF": "stop"
    }]

flushDTMF
+++++++++

.. py:module:: flushDTMF

Flushes DTMFs received on a channel. Useful in cases where callers may have entered extra digits in one dialog and you want to flush them out before sending them into another dialog.

.. code-block:: json

   {
     "flushDTMF": true
   }

eavesdrop
---------

.. py:module:: eavesdrop

``eavesdrop`` provides the ability to spy on a channel.

.. code-block:: json

    {
        "eavesdrop": {
            "user": "1000",
            "spy": false
        }
    }

DTMF signals during eavesdrop:

- **2** to speak with the user
- **1** to speak with the other half
- **3** to engage a three way
- **0** to restore eavesdrop.

The *spy: true* provides persistent eavesdrop on all channels bridged to a certain user.

echo
----

.. py:module:: echo

Simply returns all audio sent, including voice, DTMF, etc after the specified delay *milliseconds*.

.. code-block:: json

    {
        "echo": "0"
    }

exists
------

.. py:module:: exists

Determines whether the given resource exists or not.

.. code-block:: json

    [{
        "exists": {
            "resource": "media",
            "name": "myFile.wav",
            "type": "wav",
            "setVar": "DoesMyFileExist"
        }
    },
    {
       "exists": {
            "resource": "dialer",
            "name": "5b4351e0a6e784000ab5fc89",
            "member": {
                "communications": {
                "number": "${caller_id_number}",
                "state": 0
                }
            },
            "setVar": "DoesMemberExist"
        }
    }]

- **resource**: media, account, queue or dialer.
- **name**: the resource name
- **setVar**: assigns the `true` or `false` into the variable
- **type**: mp3 or wav, for media resources only
- **member**: the member parameters for dialer resources only

Email
-----

For sending emails, you need to configure :ref:`restful-http-api-email`.

sendEmail
+++++++++

.. py:module:: sendEmail

Sending an Email.

.. code-block:: json

    {
        "sendEmail": {
            "to": [
              "office@gmail.com",
              "support@webitel.ua"
            ],
            "subject": "[webitel](${Caller-Caller-ID-Number}) SMS notification",
            "message": "<H3>Turn on SMS</h3>\n<b>Creditcard</b>: ${Creditcard[0]} <i>***</i> ${Creditcard[1]}"
        }
    }

FAX
---

receiveFax
++++++++++

.. py:module:: receiveFax

Receive a FAX as a PDF file.

.. code-block:: json

    {
        "receiveFax": {
            "enable_t38": false,
            "email": ["office@webitel.com", "admin@webitel.com"]
        }
    }

+----------------+-----------------------------------------------------------------------------------------+
| ``enable_t38`` | If you want Webitel to send the re-INVITE for T.38 (per the standard) set to **false**. |
+----------------+-----------------------------------------------------------------------------------------+
| ``email``      | Send PDF file to Email *(optional)*. :ref:`restful-http-api-email` is required.         |
+----------------+-----------------------------------------------------------------------------------------+

js
--

.. py:module:: js

Executes JavaScript code.

.. code-block:: json

   {
    "js": {
      "data": "var time = LocalDate(); time.setDate(time.getDate() + (+${dpd}*-1)); return time.getMonth() + '-' + time.getDate() + '-' + time.getFullYear()",
      "setVar": "myVar"
    }
   }


goto
----

.. py:module:: goto

Immediately goto an another extension (or route) and exit from current extension.

.. code-block:: json

    [{
        "goto": "default:my_extension"
    },
    {
        "goto": "public:my_extension"
    }]

Goto extension called my_extension in the **default** or **public** route.

hangup
------

.. py:module:: hangup

Hangs up a current channel, with an optional cause code supplied.

.. code-block:: json

    {
        "hangup": ""
    }

Hangs up a specific **<uuid>** channel, with an optional cause code supplied.

.. code-block:: json

    {
        "hangup": {
            "uuid": "${another_channel_uuid}",
            "cause": "NORMAL_CLEARING"
        }
    }

The default code is **NORMAL_CLEARING**. You can specify any code from the :ref:`hangup-cause-code-table`.

httpRequest
-----------

.. py:module:: httpRequest

.. code-block:: json

    [{
        "httpRequest": {
                "url": "https://sales.bpmonline.com/ServiceModel/AuthService.svc/Login",
                "method": "POST",
                "timeout": 2000,
                "responseCode": "http_response_code",
                "exportCookie": "my_cookie",
                "data": {
                    "UserName": "Supervisor",
                    "UserPassword": "Supervisor"
                }
        }
    },
    {
        "httpRequest": {
                "url": "https://sales.bpmonline.com/${id}/dataservice/json/reply/SelectQuery",
                "method": "POST",
                "timeout": 1000,
                "responseCode": "http_response_code",
                "headers": {
                    "Content-Type":"application/json",
                    "Cookie": "${my_cookie}"
                },
                "path": {
                    "id": 0
                },
                "data": {
                    "Name": "Supervisor",
                    "UserID": "Supervisor"
                },
                "exportVariables": {
                    "effective_caller_id_name": "callerIdName",
                    "owner_caller_id_number": "callerIdOwner"
                }
        }
    },{
      "httpRequest": {
         "url": "http://10.10.10.25/tst2.xml",
         "method": "GET",
         "timeout": 5000,
         "headers": {
            "Content-Type": "text/xml; charset=utf-8",
            "SOAPAction": "http://web.cbr.ru/AllDataInfoXML"
         },
         "data": "<?xml version=\"1.0\" encoding=\"utf-8\"?><soap:Envelope xmlns:xsi=\"http://www.w3.org/2001/XMLSchema-instance\" xmlns:xsd=\"http://www.w3.org/2001/XMLSchema\" xmlns:soap=\"http://schemas.xmlsoap.org/soap/envelope/\"><soap:Body><AllDataInfoXML xmlns=\"http://web.cbr.ru/\" /></soap:Body></soap:Envelope>",
         "exportVariables": {
            "effective_caller_id_name": "Envelope/Body/AuthorizationResponse/AuthorizationResult/ResultCode/@asd",
            "owner_caller_id_number": "Envelope/Body/AuthorizationResponse/AuthorizationResult/ResultCode/text()"
         }
       }
     }
    ]

`XML XPath specification <https://godoc.org/gopkg.in/xmlpath.v2>`_


log
---

.. py:module:: log

Logs a string of text to the console.

.. code-block:: json

    {
        "log": "my log message"
    }


math
----

.. py:module:: math

Math application allows you to perform mathematical tasks on numbers.

.. code-block:: json

    {
    "math": {
        "data": "${caller_id_array}",
        "setVar": "new_random_caller_id",
        "fn": "random"
        }
    }

- ``data``: input variable, array or string
- ``setVar``: assign the output of a function to a variable
- ``fn``: JavaScript function

fn
++

- ``random``: returns a random number from array
- ``min`` and ``max``: can be used to find the lowest or highest value in a list of arguments
- ``round``: rounds a number to the nearest integer
- ``ceil``: rounds a number up to the nearest integer
- ``floor``: rounds a number down to the nearest integer

`JavaScript Math <http://www.w3schools.com/js/js_math.asp>`_


member
------

.. py:module:: member

Add new member to the dilaer.

.. code-block:: json

    {
    "member": {
        "dialer": "57a77ecbe5440b0c002ca16d",
        "name": "${effective_caller_id_name}",
        "priority": 10,
        "variables": {
            "DID": "380322530550"
        },
        "communications": [
            {
                "number": "380442228392",
                "priority": 5,
                "type": "1",
                "description": "call was missed"
            }
        ]
	    }
    }

originate
---------

.. py:module:: originate

Originate a new call.

.. code-block:: json

    {
        "originate": {
            "uuid": "${new_uuid}",
            "delay": 2,
            "timeout": 40,
            "cid_num": "${caller_id_number}",
            "cid_name": "${caller_id_name}",
            "exportVar": {
                "other_uuid": "${uuid}",
                "new_uuid": "${new_uuid}"
            },
            "endpoint": {
                "name": "gw_name1",
                "type": "sipGateway",
                "dialString": "${caller_id2}",
                "parameters": [ "ignore_early_media=true" ]
            },
            "actions": [
            {
                "playback": {
                    "name": "my.mp3",
                    "type": "mp3"
                }
            },
            {
                "bridge": {
                    "uuid": "${new_uuid}",
                    "other_uuid": "${other_uuid}"
                }
            }
            ]
        }
    }

park
----

.. py:module:: park

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


pickup
------

.. py:module:: pickup

Permits proper answering of multiple simultaneous calls to the same pickup group.

.. code-block:: json

    {
        "pickup": "mygroup"
    }

playback
--------

.. py:module:: playback

Play an audio file or tone stream.

.. code-block:: json

    [{
      "playback": {
        "name": "my.mp3",
        "type": "mp3"
        }
    },
    {
      "playback": {
        "name": "L=100;%(100,100,350,440)",
        "type": "tone"
        }
    },
    {
        "playback": {
          "files": [
            {
              "name": "welcome-rus.wav",
              "type": "wav"
            },
            {
              "name": "2000",
              "type": "silence"
            },
            {
              "name": "ivr/ivr-you_are_number.wav",
              "type": "local"
            },
            {
              "name": "${cc_my_position}",
              "type": "say",
              "lang": "en",
              "method": "NUMBER pronounced"
            }
          ]
        }
    }]

mp3 and wav
+++++++++++

An any mp3 or wav file uploaded as a **media**.

say
+++

The say type will use the pre-recorded sound files to read or say various things like dates, times, digits, etc. The say application can read digits and numbers as well as dollar amounts, date/time values and IP addresses. It can also spell out alpha-numeric text, including punctuation marks.

**lang**:

- ``en`` - English sound files;
- ``ru`` - Russian sound files.

**method**:

An example: "NUMBER pronounced"

Can be one of the following: NUMBER, ITEMS, CURRENCY, TIME_MEASUREMENT, CURRENT_DATE, CURRENT_TIME, CURRENT_DATE_TIME, TELEPHONE_NUMBER, TELEPHONE_EXTENSION, URL, IP_ADDRESS, EMAIL_ADDRESS, ACCOUNT_NUMBER, NAME_SPELLED, NAME_PHONETIC, SHORT_DATE_TIME

And method is one of the following (for example, passing a value of "42"):

- ``pronounced`` - cardinal number, e.g. "forty two";
- ``iterated`` - nominal number, e.g. "four two";
- ``counted`` - ordinal number, e.g. "forty second".

silence
+++++++

Silence in millisecond.

shout
+++++

Can play remote media stream.

tone
++++

Generate tone. [L=x;][v=y;]%(<on-duration>, <off-duration>, <freq-1> [, freq-2] [, freq-3] [, freq-n] [;loops=x])

- Durations are specified in milliseconds
- Frequencies are specified in Hz

**L=x;** create x copies of the specified tone stream in memory before playing. Note that L=-1 is not valid, use loops=-1 to loop continuously. Specify L= at the beginning of the tone definition string.

**;loops=x** Loop x times, use ;loops=-1 for endless loop. This generates the tone, then repeats the generation process so it presumably consumers less cpu and memory than the L= parameter. Note that ;loops=x is postfix notation so it should appear at the end of the tone definition string.

**v=y** Volume of tones expressed as the equivalent in dB (deciBels) in a PCM waveform. 0 = maximum volume, negative integers represent softer volume (loudness). Do not enter positive values greater than zero! Note that non-linear formats such as G.711 and G.723 will offer slightly lower amplitudes as an artifact of their algorithms.

See :ref:`TGML` complete listing of capabilities and syntax.

play and get digits
+++++++++++++++++++

.. code-block:: json

    {
      "playback": {
                "name": "enter_ext.wav",
                "type": "wav",
                "getDigits": {
                  "setVar": "getIvrDigit",
                  "min": 3,
                  "max": 4,
                  "tries": 1,
                  "timeout": 2000,
                  "flushDTMF": true
                }
      }
    }

+---------------+------------------------------------------------------------------------------------+
| ``setVar``    | Channel variable into which digits should be placed.                               |
+---------------+------------------------------------------------------------------------------------+
| ``min``       | Minimum number of digits to fetch (minimum value of 0).                            |
+---------------+------------------------------------------------------------------------------------+
| ``max``       | Maximum number of digits to fetch (maximum value of 128).                          |
+---------------+------------------------------------------------------------------------------------+
| ``tries``     | Numbers of tries for the sound to play.                                            |
+---------------+------------------------------------------------------------------------------------+
| ``timeout``   | Number of milliseconds to wait for a dialed response after the file playback ends. |
+---------------+------------------------------------------------------------------------------------+
| ``flushDTMF`` | Flushes DTMFs received on a channel. Default is `true`.                            |
+---------------+------------------------------------------------------------------------------------+

queue
-----

.. py:module:: queue

An inbound call queuing application that can be used for call center needs.

.. code-block:: json

    {
        "queue": {
          "name": "myQueueName",
          "transferAfterBridge": "public:feedback_ivr_menu",
          "timer": {
            "interval": 90,
            "tries": 1,
            "actions": [
              {
                "ccPosition": {
                  "var": "cc_my_position"
                }
              },
              {
                "playback": {
                  "files": [
                    {
                        "name": "ivr/ivr-you_are_number.wav",
                        "type": "local"
                    },
                    {
                        "name": "${cc_my_position}",
                        "type": "say",
                        "lang": "en",
                        "method": "number pronounced"
                    }
                  ]
                }
              }
            ]
          }
        }
    }

+-------------------------+--------------------------------------------------------------------+
| ``name``                | The queue name.                                                    |
+-------------------------+--------------------------------------------------------------------+
| ``transferAfterBridge`` | The name of the callflow, where to transfer a success calls.       |
|                         | Please notice, that `hangup_after_bridge` variable must be `false` |
+-------------------------+--------------------------------------------------------------------+

timer
+++++

+----------------+------------------------------------------------------------+
| ``actions``    | Execute some set of actions.                               |
+----------------+------------------------------------------------------------+
| ``interval``   | How periodically to execute actions in seconds.            |
+----------------+------------------------------------------------------------+
| ``tries``      | Numbers of tries to execute actions                        |
+----------------+------------------------------------------------------------+
| ``ccPosition`` | Set current position in a variable.                        |
+----------------+------------------------------------------------------------+

Recording
---------

recordFile
++++++++++

.. py:module:: recordFile

Record to a file from the channel's input media stream.

.. code-block:: json


    {
        "recordFile": {
            "name": "MySuperFile",
            "terminators": "#",
            "type": "mp3",
            "maxSec": 60,
            "silenceHits": 5,
            "email": ["office@webitel.com", "admin@webitel.com"],
            "emailSubject": "You have a new message!",
            "emailBody": "Message fom ${caller_id_number}"
        }
    }

+--------------------+------------------------------------------------------------------------------------------+
| ``name``           | Recorded file name.                                                                      |
+--------------------+------------------------------------------------------------------------------------------+
| ``type``           | File format: mp3 for an audio or mp4 for a video calls.                                  |
+--------------------+------------------------------------------------------------------------------------------+
| ``terminators``    | Will set # as recording session terminator.                                              |
+--------------------+------------------------------------------------------------------------------------------+
| ``maxSec``         | The maximum duration of the recording in seconds.                                        |
+--------------------+------------------------------------------------------------------------------------------+
| ``silenceHits``    | How many seconds of silence will be tolerated before the recording stops.                |
+--------------------+------------------------------------------------------------------------------------------+
| ``email``          | Send recorded file to the Email *(optional)*. :ref:`restful-http-api-email` is required. |
+--------------------+------------------------------------------------------------------------------------------+
| ``emailSubject``   | Email subject *(optional)*. Can contain any channel variables.                           |
+--------------------+------------------------------------------------------------------------------------------+
| ``emailBody``      | Email body *(optional)*. Can contain any channel variables.                              |
+--------------------+------------------------------------------------------------------------------------------+

recordSession
+++++++++++++

.. py:module:: recordSession

Records an entire phone call or session.

.. code-block:: json

    {
        "recordSession": {
            "action": "start",
            "type": "mp3",
            "stereo": true,
            "bridged": true,
            "minSec": 2,
            "followTransfer": true,
            "email": ["office@webitel.com", "admin@webitel.com"],
            "emailSubject": "You have a new message!",
            "emailBody": "Message fom ${caller_id_number}"
        }
    }

+--------------------+------------------------------------------------------------------------------------------+
| ``action``         | start or stop record session.                                                            |
+--------------------+------------------------------------------------------------------------------------------+
| ``type``           | File format: mp3 for an audio or mp4 for a video calls.                                  |
+--------------------+------------------------------------------------------------------------------------------+
| ``stereo``         | Record leg A and leg B streams (i.e. the caller is recorded to the left channel and the  |
|                    | reciever is recorded on right channel) into different channel in a stereo file.          |
+--------------------+------------------------------------------------------------------------------------------+
| ``bridged``        | Record session only when the channel is bridged.                                         |
+--------------------+------------------------------------------------------------------------------------------+
| ``minSec``         | Sets the minimum recording length. Normally a recording must be at least 3 seconds long. |
|                    | If a recording does not meet the minimum length, it is deleted after being recorded.     |
+--------------------+------------------------------------------------------------------------------------------+
| ``followTransfer`` | If you want the call recording to continue after transferring, set variable to **true**. |
+--------------------+------------------------------------------------------------------------------------------+
| ``email``          | Send recorded file to the Email *(optional)*. :ref:`restful-http-api-email` is required. |
+--------------------+------------------------------------------------------------------------------------------+
| ``emailSubject``   | Email subject *(optional)*. Can contain any channel variables.                           |
+--------------------+------------------------------------------------------------------------------------------+
| ``emailBody``      | Email body *(optional)*. Can contain any channel variables.                              |
+--------------------+------------------------------------------------------------------------------------------+

ringback
--------

.. py:module:: ringback

- **ringback call** lets you set artificial ringback on a channel that is waiting for an originated call to be answered.
- **ringback transfer** - set the sound that will play if a call has already been answered, and it is then transferred to another endpoint.
- **hold** - set music or tone on hold.

.. code-block:: json

    {
      "ringback": {
        "call": {
            "name": "my.mp3",
            "type": "mp3"
        },
        "hold": {
            "type": "silence"
        },
        "transfer": {
            "name": "$${us-ring}",
            "type": "tone"
        }
      }
    }

mp3 and wav
+++++++++++

An any mp3 or wav file uploaded as a **media**.

silence
+++++++

Disable music on hold.

shout
+++++

Can play remote stream. You can set internet radio as Your ringback tone, just set URL as a value of the **name** field: http://online-radioroks.tavrmedia.ua/RadioROKS_32

tone
++++

Generate tone. You may set **$${ru-ring}** in the name for a russian ringback tone. See :ref:`TGML` complete listing of capabilities and syntax.

schedule
--------

.. py:module:: schedule

Schedule a :py:mod:`hangup` or :py:mod:`goto` in the future. Also, you can schedule a callback:

.. code-block:: json


    [{
    "schedule": {
        "action": "goto",
        "seconds": 240,
        "data": "default:1000"
        }
    },
    {
        "schedule": {
            "action": "hangup",
            "seconds": 360,
            "data": "ALLOTTED_TIMEOUT"
        }
    },
    {
        "schedule": {
            "action": "callback",
            "seconds": 5,
            "number": "${caller_id_number}",
            "destination": "380891205014"
        }
    }]

sipRedirect
-----------

.. py:module:: sipRedirect

Can redirect a SIP channel to another endpoint.

.. code-block:: json

    [{
        "sipRedirect": "sip:foo@end.com"
    },
    {
        "sipRedirect": ["sip:foo@bar.com", "sip:foo@end.com"]
    }]

setSounds
---------

.. py:module:: setSounds

Set sound file package. There are a number of sound file packages available.

.. code-block:: json

    {
        "setSounds": {
            "voice": "elena",
            "lang": "ru_RU"
        }
    }

+-------------+---------------------------------------------------+
| English     | "voice": "callie", "lang": "en_US" *(default)*    |
+-------------+---------------------------------------------------+
| Russian     | "voice": "elena", "lang": "ru_RU"                 |
+-------------+---------------------------------------------------+

sleep
-----

.. py:module:: sleep

Pause the channel for a given number of milliseconds, consuming the audio for that period of time. Calling sleep also will consume any outstanding RTP on the operating system's input queue, which can be very useful in situations where audio becomes backlogged.

.. code-block:: json

    {
        "sleep": 1000
    }

script
------

.. py:module:: script

Execute `Lua Script`. Scripts must be placed in the **/scripts/lua** directory inside `FreeSWITCH <https://hub.docker.com/r/webitel/freeswitch/>`_ docker container.

.. code-block:: json

    {
        "script": {
            "name": "MyLuaScript.lua",
            "parameters": ["a=Alex", "b=1001"]
        }
    }

string
------

.. py:module:: string

String application help you to work with strings.

.. code-block:: json

    [{
        "string": {
            "data": "${destination_number}",
            "setVar": "myVar",
            "fn": "slice",
            "args": "-3"
        }
     },
     {
        "string": {
            "data": "${caller_id_number}",
            "fn": "replace",
            "setVar": "effective_caller_id_number",
            "args": [
                "/^0/",
                "+84"
            ]
        }
    }]

- ``data``: input variable or string
- ``setVar``: assign the output of a function to a variable
- ``fn``: JavaScript function
- ``args``: function arguments

fn
++

- ``length``: returns the length of a string
- ``indexOf`` and ``lastIndexOf``: returns the index of (the position of) the first or last occurrence of a specified text in a string
- ``search``: searches a string for a specified value and returns the position of the match
- ``slice``: extracts a part of a string and returns the extracted part in a new string
- ``substring``: is similar to slice. The difference is that ``substring`` cannot accept negative indexes.
- ``substr``: is similar to slice. The difference is that the second parameter specifies the length of the extracted part.
- ``replace``: replaces a specified value with another value in a string
- ``toUpperCase`` or ``toLowerCase``: A string is converted to upper case or to lower case
- ``charAt``: returns the character at a specified index (position) in a string
- ``charCodeAt``: returns the unicode of the character at a specified index in a string
- ``split``: A string can be converted to an array with the ``split`` function
- ``reverse``: Reverse the provided string

`JavaScript String <http://www.w3schools.com/js/js_string_methods.asp>`_

stt
---

.. py:module:: stt

Speech-To-Text.

.. code-block:: json

    {
        "stt": {
            "lang": "uk-UA",
            "maxSec": 15,
            "silenceThresh": 200,
            "silenceHits": 3,
            "setVar": "myTextVar"
        }
    }

tts
---

.. py:module:: tts

Text-To-Speech.

.. code-block:: json

    [{
        "tts": {
            "provider": "polly",
            "accessKey": "GDNYEHJWNNYYWBJNOZA",
            "accessToken": "c1j5QSPx9H63jmwtwMojSZiQ9QeO+3v",
            "voice": "Maxim",
            "textType": "ssml",
            "text": "<speak><amazon:effect name=\"whispered\">If you make any noise, </amazon:effect> she said, <amazon:effect name=\"whispered\">they will hear us.</amazon:effect></speak>"
        }
    },
    {
        "tts": {
            "provider": "microsoft",
            "accessKey": "cf62f9392773hyyhjkk3aa99cc9fd36f87",
            "accessToken": "6772cff3f8d740fd91d345dsfj987309",
            "voice": {
                "language": "ru-RU",
                "gender": "Male"
            },
            "text": "Привет, меня зовут Егор!"
        }
    }]

*Polly*: ``textType`` specifies whether the input text is plain **text** or **ssml**. The default value is plain **text**. For more information, see `Using SSML <http://docs.aws.amazon.com/polly/latest/dg/supported-ssml.html>`_


Users
-----

setUser
+++++++

.. py:module:: setUser

Pulls all of the channel variables defined for a user as if the user had auth'd.

.. code-block:: json

    {
      "setUser": {
          "name": "102"
      }
    }

findUser
++++++++

.. py:module:: findUser

Find an user by variables or parameters.

.. code-block:: json

    {
      "findUser": {
        "filter": {
          "vm-password": "${userPIN}"
        },
        "columns": [
          "id",
          "effective_caller_id_name"
        ],
        "exportVariables": {
          "ext_id": "0.id",
          "effective_caller_id_name": "0.effective_caller_id_name"
        }
      }
    }

userData
++++++++

.. py:module:: userData

Retrieves user variables as defined in the directory.

.. code-block:: json

    {
      "userData": {
          "name": "102",
          "var": "account_state",
          "setVar": "acc_state"
      }
    }

Variables
---------

Additionally to the build-in :ref:`channel-variables`, You may set any number of unique channel variables for your own purposes and even elect to log them to the CDR.

setVar
++++++

.. py:module:: setVar

Set a channel variable.

.. code-block:: json

    [{
        "setVar": "a=1"
    },
    {
        "setVar": ["a=1", "b=2", "c=3"]
    },
    {
        "setVar": "all:a=1"
    },
    {
        "setVar": "nolocal:a=1"
    }]

- **all** - Exports a channel variable for the A leg and the B leg.
- **nolocal** - Exports a channel variable only for the B leg.

setArray
++++++++

.. py:module:: setArray

.. code-block:: json

  {
    "setArray": {
      "myArray": [
        "val1", "val2", "val3"
      ]
    }
  }

Referencing an array element: `${myArray[0]}`, `${myArray[1]}`, `${myArray[2]}`.

exportVars
++++++++++

.. py:module:: exportVars

`exportVars` lists variables to be exported to the webitel client side upon JavaScript library.

.. code-block:: json

  {
    "exportVars": [
      "ivrLang",
      "mainMenuAction",
      "subMenuAction"
    ]
  }

unSet
+++++

.. py:module:: unSet

Clears out a channel variable.

.. code-block:: json

    {
        "unSet": "sip_h_call-info"
    }

voicemail
---------

.. py:module:: voicemail

Voicemail application lets you send calls to voicemail, which allows callers to leave messages for users and allows users to retrieve and manage any messages left by callers.

leave a voicemail message
+++++++++++++++++++++++++

.. code-block:: json

   {
      "voicemail": {
          "user": "100",
          "skip_greeting": true,
          "skip_instructions": true,
          "cc": [
            "1001",
            "1002"
          ]
      }
    }

+-----------------------+------------------------------------------------------------------------+
| ``user``              | Webitel User ID.                                                       |
+-----------------------+------------------------------------------------------------------------+
| ``skip_greeting``     | Skips playback of greeting message when leaving messages.              |
+-----------------------+------------------------------------------------------------------------+
| ``skip_instructions`` | Skips playback of instructions when leaving messages.                  |
+-----------------------+------------------------------------------------------------------------+
| ``cc``                | Inject the message into the specified voicemail mailbox.               |
+-----------------------+------------------------------------------------------------------------+

check a voicemail message
+++++++++++++++++++++++++

.. code-block:: json

   {
      "voicemail": {
          "user": "1000",
          "check": true,
          "auth": true
      }
   }

+-----------------------+------------------------------------------------------------------------+
| ``user``              | Webitel User ID.                                                       |
+-----------------------+------------------------------------------------------------------------+
| ``check``             | Will allow the user to check voicemail if is set to the **true**.      |
+-----------------------+------------------------------------------------------------------------+
| ``auth``              | Will prompt for PIN if is set to the **true**.                         |
+-----------------------+------------------------------------------------------------------------+
