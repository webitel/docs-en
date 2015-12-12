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
      "order": 1,
      "name": "Kyiv",
      "domain": "webitel.ua",
      "fs_timezone" : "Europe/Kiev",
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
      "fs_timezone" : "Europe/Kiev",
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

.. _tod:

Time of Day Routing
-------------------

Time of day routing allows calls to be executed different applications based upon the time of day, day of week. You can use it in the different :ref:`Conditional Statements`.

By default, time-based routing uses the UTC timezone. *See:* :ref:`tz-table`.


.. js:function:: &minute_of_day(minutes)
    
    :param string minutes: Minute of the day, (1-1440) (midnight = 1, 1am = 60, noon = 720, etc.). 
    :returns: true, false.

.. js:function:: &time_of_day(08:00-17:00)
    
    :param string time: Time range formatted: hh:mm[:ss]-hh:mm[:ss] (seconds optional).
    :returns: true, false.

.. js:function:: &minute(minutes)
    
    :param string minutes: Minute (of the hour), 0-59.
    :returns: true, false.

.. js:function:: &hour(houres)
    
    :param string houres: Hour, 0-23.
    :returns: true, false.

.. js:function:: &wday(wdays)
    
    :param string wdays: Day of week, 1-7 (Sun = 1, Mon = 2, etc.) or “sun”, “mon”, “tue”, etc.
    :returns: true, false.

.. js:function:: &mweek(mweeks)
    
    :param string mweeks: Week of month, 1-6.
    :returns: true, false.

.. js:function:: &week(weeks)
    
    :param string weeks: Week of year, 1-53.
    :returns: true, false.

.. js:function:: &mday(mdays)
    
    :param string mdays: Day of month, 1-31.
    :returns: true, false.

.. js:function:: &mon(m)
    
    :param string m: Month, 1-12 (Jan = 1, etc.).
    :returns: true, false.

.. js:function:: &yday(d)
    
    :param string d: Day of year, 1-366.
    :returns: true, false.

.. js:function:: &year(y)
    
    :param string y: Calendar year, 0-9999.
    :returns: true, false.

**Example code:**

.. code-block:: json 

  {
    "if": {
      "expression": "&hour(18-20) && &wday(2-6)",
      "then": []
    }
  }


.. _Conditional Statements:

Conditional Statements
----------------------

In the ACR Scheme we have the following conditional statements:

- Use **if ... then** to specify a block of code to be executed, if a specified condition is true
- Use **else** to specify a block of code to be executed, if the same condition is false
- Use **switch** to specify many alternative blocks of code to be executed

You may use any variable setted by :py:mod:`setVar` application, :ref:`tod` or build-in :ref:`channel-variables`.

if
++

.. py:module:: if

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

.. py:module:: switch

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
