.. _acr-scheme:

ACR Scheme
==========

`ACR 
<https://github.com/webitel/acr>`_ (Advanced Call Routing) JSON Scheme - routes call that match configured rules. ACR Schemes are separated in two different route for different kinds of calls:

* **Default Route** handles calls originating from internal extensions.
* **Public Route** handles calls originating from the public phone network (`PSTN
  <http://en.wikipedia.org/wiki/Public_switched_telephone_network>`_).

Default Route 
-------------

.. code-block:: json 
   :caption: Default route example JSON scheme

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

Public Route 
-------------

.. code-block:: json 
   :caption: Public route example JSON scheme

    {
      "destination_number": [
        "442228392",
        "74997045627"
      ],
      "domain": "webitel.ua",
      "callflow": [
        {
          "httpRequest": {
            "url": "https://sales.it-sfera.com/0/ServiceModel/GetCallerOwnerService.svc/GetCallerOwner"
          }
        },
        {
          "if": {
            "expression": "${owner_caller_id_number}",
            "then": [
              {
                "answer": "183"
              },
              {
                "recordSession": "start"
              },
              {
                "bridge": {
                  "endpoints": [
                    {
                      "name": "${owner_caller_id_number}",
                      "type": "user",
                      "parameters": [
                        "leg_timeout=10"
                      ]
                    }
                  ]
                }
              }
            ]
          }
        },
        {
          "goto": "default:100"
        }
      ]
    }


Time of Day Routing
-------------------

Time of day routing allows calls to be executed different applications based upon the time of day, day of week. You can use it in the different :ref:`Conditional Statements`.

By default, time-based routing uses the UTC timezone.

.. code-block:: json 

  {
    "if": {
      "expression": "&hour(18-20) && &wday(2-6)",
      "then": []
    }
  }

+----------------------+----------------------------------------------------------------------------------------+
| ``&minute_of_day()`` | Minute of the day, (1-1440) (midnight = 1, 1am = 60, noon = 720, etc.).                |
+----------------------+----------------------------------------------------------------------------------------+
| ``&time_of_day()``   | Time range formatted: hh:mm[:ss]-hh:mm[:ss] (seconds optional) Example: "08:00-17:00". |
+----------------------+----------------------------------------------------------------------------------------+
| ``&minute()``        | Minute (of the hour), 0-59.                                                            |
+----------------------+----------------------------------------------------------------------------------------+
| ``&hour()``          | Hour, 0-23.                                                                            |
+----------------------+----------------------------------------------------------------------------------------+
| ``&wday()``          | Day of week, 1-7 (Sun = 1, Mon = 2, etc.) or "sun", "mon", "tue", etc.                 |
+----------------------+----------------------------------------------------------------------------------------+
| ``&mweek()``         | Week of month, 1-6.                                                                    |
+----------------------+----------------------------------------------------------------------------------------+
| ``&week()``          | Week of year, 1-53.                                                                    |
+----------------------+----------------------------------------------------------------------------------------+
| ``&mday()``          | Day of month, 1-31.                                                                    |
+----------------------+----------------------------------------------------------------------------------------+
| ``&mon()``           | Month, 1-12 (Jan = 1, etc.).                                                           |
+----------------------+----------------------------------------------------------------------------------------+
| ``&yday()``          | Day of year, 1-366.                                                                    |
+----------------------+----------------------------------------------------------------------------------------+
| ``&year()``          | Calendar year, 0-9999.                                                                 |
+----------------------+----------------------------------------------------------------------------------------+

.. _Conditional Statements:

Conditional Statements
----------------------

In ACR Scheme we have the following conditional statements:

- Use **if ... then** to specify a block of code to be executed, if a specified condition is true
- Use **else** to specify a block of code to be executed, if the same condition is false
- Use **switch** to specify many alternative blocks of code to be executed

if
++

.. code-block:: json 

  {
    "if": {
      "expression": "${myVar} != ''",
      "then": [],
      "else": []
    }
  }


- ``expression`` - The condition of if statements should always result in either **true** or **false**.
- ``then`` - If the result is **true**, immediate **then** block would be executed.
- ``else`` - If the result is **false**, immediate **else** block would be executed.

switch
++++++

.. code-block:: json 

    [
      {
        "switch": {
          "variable": "${IVR}",
          "case": {
            "1": [],
            "2": [],
            "3": [],
            "default": []
          }
        }
      }
    ]


- ``variable`` - Variable for cases.
- ``case`` - The value of the variable is compared with the values of each case.
- ``default`` - The block of the applications that would be executed if the given value is not matched with any of the pre-defined values.

For more information go to the :ref:`acr-applications` page.
