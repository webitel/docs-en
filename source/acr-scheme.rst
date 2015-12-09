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


For more information go to the :ref:`acr-applications` page.
