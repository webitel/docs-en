.. _restful-http-api:

RESTful HTTP API
****************

Webitel Status
==============

.. http:get:: /api/v2/status 

   **Example request**:

   .. sourcecode:: http

      GET /api/v2/status HTTP/1.1
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

        {
          "Version": "3.1#9-sha1:4d2ab1a",
          "Node memory": {
            "rss": "87.5 MB",
            "heapTotal": "32.4 MB",
            "heapUsed": "27 MB"
          },
          "Process ID": 20,
          "Process up time": "142:33:17",
          "OS": {
            "Total memory": "15.6 GB",
            "Free memory": "211.7 MB",
            "Platform": "linux",
            "Name": "Linux",
            "Architecture": "x64"
          },
          "Users_Session": 2,
          "Domain_Session": 2,
          "CRASH_WORKER_COUNT": 0,
          "Webitel": {
            "Status": "Connected",
            "ApiQueue": 0,
            "CmdQueue": 0
          },
          "freeSWITCH": "UP 0 years, 13 days, 17 hours, 50 minutes, 22 seconds, 52 milliseconds, 839 microseconds\nFreeSWITCH (Version 1.6.5 git d5520a6 2015-11-19 20:27:21Z 64bit) is ready\n58619 session(s) since startup\n0 session(s) - peak 69, last 5min 0 \n0 session(s) per Sec out of max 30, peak 16, last 5min 0 \n1000 session(s) max\nmin idle cpu 0.00/98.73\nCurrent Stack Size/Max 240K/240K\n"
        }

   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :statuscode 200: No error
   :statuscode 401: Invalid credentials

   ::

    curl -X GET -H 'X-Access-Token: yJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDUzOTY0ODh9.xCf6fbvOPc-CkYdD9MPxLXBEukHm1KX6w5zN5q55OBQ' -H 'X-Key: c1d19874-f2bb-4284-94ac-043cb97288fe' "https://api.webitel.com:10022/api/v2/status"

Domains
=======

Get domains list
++++++++++++++++

.. http:get:: /api/v2/domains 

   **Example request**:

   .. sourcecode:: http

      GET /api/v2/domains HTTP/1.1
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

        {
            "status":"OK",
            "data":{
                "777":{
                    "id":"777",
                    "domain":"d1.webitel.com",
                    "user":"7",
                    "acc/dvc":"7/0"
                },
                "demo.webitel.com":{
                    "id":"demo.webitel.com",
                    "domain":"demo.webitel.com",
                    "user":"30",
                    "acc/dvc":"30/0"
                },
                "webitel.com":{
                    "id":"webitel.com",
                    "domain":"webitel.com",
                    "user":"25",
                    "acc/dvc":"25/0"
                }
            }
        }

   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :statuscode 200: No error
   :statuscode 400: Bad request

   ::

    curl -XGET -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDY1MTUxNzB9.3L4D21aMdNxnm9lZTklt6EvjeNP9RLLKLJtFqVLnSCs' -H 'X-Key: eb76bb9f-6366-4168-b0f1-dac6f15adceb' "https://api.webitel.com:10022/api/v2/domains"

Create a new domain
+++++++++++++++++++

.. http:post:: /api/v2/domains 

   **Example request**:

   .. sourcecode:: http

      POST /api/v2/domains HTTP/1.1
      Content-Type: application/json
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

      {
          "domain_name": "mydomain.com",
          "customer_id": "20150909",
          "variables": ["default_language=ru"],
          "parameters": []
      }

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

      {
         "status":"OK",
         "info":"+OK [mydomain.com] created !\n",
         "more info":""
      }

   :<json string domain_name: The domain name
   :<json string customer_id: The customer license ID
   :<json array variables: Additional variables
   :<json array parameters: Additional parameters
   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :reqheader Content-Type: `application/json`
   :statuscode 200: No error
   :statuscode 400: Bad request

   ::

    curl -XPOST -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDY1MTUxNzB9.3L4D21aMdNxnm9lZTklt6EvjeNP9RLLKLJtFqVLnSCs' -H 'X-Key:eb76bb9f-6366-4168-b0f1-dac6f15adceb' -H 'Content-Type: application/json' -d '{"domain_name": "mydomain.com","customer_id": "20150909","variables": ["default_language=ru"],"parameters": []}' "https://api.webitel.com:10022/api/v2/domains"

Delete the domain
+++++++++++++++++

.. http:delete:: /api/v2/domains/(domain_name) 

   **Example request**:

   .. sourcecode:: http

      DELETE /api/v2/domains/mydomain.com HTTP/1.1
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

      {
         "status":"OK",
         "info":"+OK [mydomain.com] destroy !\n",
         "more info":""
      }

   :param string domain_name: The domain name
   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :statuscode 200: No error
   :statuscode 400: Bad request

   ::

    curl -XDELETE -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDY1MTUxNzB9.3L4D21aMdNxnm9lZTklt6EvjeNP9RLLKLJtFqVLnSCs' -H 'X-Key:eb76bb9f-6366-4168-b0f1-dac6f15adceb' "https://api.webitel.com:10022/api/v2/domains/mydomain.com"

