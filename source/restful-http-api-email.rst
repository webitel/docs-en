.. _restful-http-api-email:

Email settings
==============

Get email settings
++++++++++++++++++

.. http:get:: /api/v2/email/settings?domain=(domain_name)

   **Example request**:

   .. sourcecode:: http

      GET /api/v2/email/settings?domain=my.webitel.com HTTP/1.1
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

        {
            "_id": "566999b271e0c652ea5da98e",
            "provider": "smtp",
            "description": "My PBX Email Settings",
            "from": "my@webitel.com",
            "options": {
                "host": "m.webitel.com",
                "port": 465,
                "secure": true,
                "debug": false,
                "tls": {
                    "rejectUnauthorized": false
                },
                "auth": {
                    "user": "my@webitel.com",
                    "pass": "b271e0c652eaa98e"
                }
            },
            "domain": "my.webitel.com"
         }

   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :param string domain_name: Domain name is required
   :statuscode 200: No error

   **CURL example**:

   ::

    curl -XGET -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIxNzA0NDk2NTB9.WqTx_dpbuTyp-l8w6rmQhzoatI-qPRkoM-hmxXTAzaU' -H 'X-Key: bed5ea60-84e7-4eba-b6ad-e3a23f220be1' "https://app.webitel.com/engine/api/v2/email/settings?domain=my.webitel.com"

Create email settings
+++++++++++++++++++++

.. http:post:: /api/v2/email/settings?domain=(domain_name) 

   **Example request**:

   .. sourcecode:: http

      POST /api/v2/email/settings?domain=my.webitel.com HTTP/1.1
      Content-Type: application/json
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

        {
            "provider": "smtp",
            "description": "My Setting",
            "from": "my@webitel.com",
            "options": {
                "host": "m.webitel.com",
                "port": 465,
                "secure": true,
                "debug": false,
                "tls": {
                    "rejectUnauthorized": false
                },
                "auth": {
                    "user": "my@webitel.com",
                    "pass": "itte574dsts485"
                }
            }
         }

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

        {
            "_id": "574d241a821e7655f78a40f4",
            "provider": "smtp",
            "description": "My Setting",
            "from": "my@webitel.com",
            "options": {
                "host": "m.webitel.com",
                "port": 465,
                "secure": true,
                "debug": false,
                "tls": {
                    "rejectUnauthorized": false
                },
                "auth": {
                    "user": "my@webitel.com",
                    "pass": "241a821e7655fss"
                }
            },
            "domain": "my.webitel.com"
        }

   :<json string provider: smtp.
   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :reqheader Content-Type: `application/json`
   :param string domain_name: Domain name is required
   :statuscode 200: No error
   :statuscode 400: Bad request

   **CURL example**:

   ::

    curl -XPOST -H 'X-Key: 3f568b08-c691-4cf9-976e-28164360cf1c' -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NjUyNzY2NDgzMTQsImFjbCI6eyJjZHIiOlsiKiJdLCJjZHIvZmlsZXMiOlsiKiJdLCJjZHIvbWVkaWEiOlsiKiJdfX0.o2cYje_JwCWpa3lMV0Iq6tdv4xJmmuP210HA-mlo_30' -H 'Content-Type: application/json' -d '{ "provider": "smtp", "description": "My Setting", "from": "my@webitel.com", "options": { "host": "m.webitel.com", "port": 465, "secure": true, "debug": false, "tls": { "rejectUnauthorized": false }, "auth": { "user": "my@webitel.com", "pass": "241a821e7655fss" } } }' "https://app.webitel.com/engine/api/v2/email/settings?domain=my.webitel.com"

Update email settings
+++++++++++++++++++++

.. http:put:: /api/v2/email/settings?domain=(domain_name)

   **Example request**:

   .. sourcecode:: http

      PUT /api/v2/email/settings?domain=my.webitel.com HTTP/1.1
      Content-Type: application/json
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

        {
            "provider": "smtp",
            "description": "My updated setting",
            "from": "my@webitel.com",
            "options": {
                "host": "m.webitel.com",
                "port": 465,
                "secure": true,
                "debug": false,
                "tls": {
                    "rejectUnauthorized": false
                },
                "auth": {
                    "user": "my@webitel.com",
                    "pass": "itte574dsts485"
                }
            }
         }

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

        {
            "_id": "574d241a821e7655f78a40f4",
            "provider": "smtp",
            "description": "My updated setting",
            "from": "my@webitel.com",
            "options": {
                "host": "m.webitel.com",
                "port": 465,
                "secure": true,
                "debug": false,
                "tls": {
                "rejectUnauthorized": false
                },
                "auth": {
                "user": "my@webitel.com",
                "pass": "itte574dsts485"
                }
            },
            "domain": "my.webitel.com"
        }

   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :reqheader Content-Type: `application/json`
   :param string domain_name: Domain name is required
   :statuscode 200: No error
   :statuscode 400: Bad request

   **CURL example**:

   ::

    curl -XPOST -H 'X-Key: 3f568b08-c691-4cf9-976e-28164360cf1c' -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NjUyNzY2NDgzMTQsImFjbCI6eyJjZHIiOlsiKiJdLCJjZHIvZmlsZXMiOlsiKiJdLCJjZHIvbWVkaWEiOlsiKiJdfX0.o2cYje_JwCWpa3lMV0Iq6tdv4xJmmuP210HA-mlo_30' -H 'Content-Type: application/json' -d '{ "provider": "smtp", "description": "My updated setting", "from": "my@webitel.com", "options": { "host": "m.webitel.com", "port": 465, "secure": true, "debug": false, "tls": { "rejectUnauthorized": false }, "auth": { "user": "my@webitel.com", "pass": "241a821e7655fss" } } }' "https://app.webitel.com/engine/api/v2/email/settings?domain=my.webitel.com"

Delete email settings
+++++++++++++++++++++

.. http:delete:: /api/v2/email/settings?domain=(domain_name)

   **Example request**:

   .. sourcecode:: http

      DELETE /api/v2/email/settings?domain=my.webitel.com HTTP/1.1
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

       { 
         "status": "OK",
         "Info": "Removed 1 record."
       }

   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :param string domain_name: Domain name is required
   :statuscode 200: No error
   :statuscode 400: Bad request

   **CURL example**:

   ::

    curl -XDELETE  -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIxNzUxMjk5ODF9.DFtcez2ntKLsTsQ5SHYtlwXLf9UC3UbxfMIFRZlCgOE' -H 'X-Key: 1809dfa7-243c-49a6-a5ef-67f9d9565f3f'  "https://app.webitel.com/api/v2/email/settings?domain=my.webitel.com"
