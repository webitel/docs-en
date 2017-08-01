.. _restful-http-api-misc:

Webitel Status
==============

.. http:get:: /api/v2/status 

   **Example request**:

   .. sourcecode:: http

      GET /api/v2/status HTTP/1.1
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

   **Example response**:

   .. sourcecode:: json

      {
        "version": "master#261-sha1:4a6ad8b564724c60afb52fef48b6621330d4339f",
        "nodeMemory": {
          "rss": 66199552,
          "heapTotal": 49872896,
          "heapUsed": 42046536
        },
        "processId": 12,
        "socketSessions": 9,
        "userSessions": 6,
        "maxUserSessions": 6,
        "domainSessions": 4,
        "processUpTimeSec": 69864.091,
        "wConsole": {
          "status": "Connected",
          "apiQueue": 0,
          "cmdQueue": 0,
          "version": "3.2.0",
          "sid": "29e1b260-d7da-11dd-829b-54a05079cad2\n"
        },
        "system": {
          "totalMemory": 16731197440,
          "freeMemory": 1578758144,
          "platform": "linux",
          "name": "Linux",
          "architecture": "x64"
        },
        "crashCount": "0",
        "freeSWITCH": "UP 0 years, 0 days, 19 hours, 23 minutes, 56 seconds, 830 milliseconds, 520 microseconds\nFreeSWITCH (Version 1.6.19 git e61ee1a 2017-07-25 21:08:52Z 64bit) is ready\n7629 session(s) since startup\n5 session(s) - peak 124, last 5min 5 \n3 session(s) per Sec out of max 30, peak 54, last 5min 3 \n1000 session(s) max\nmin idle cpu 0.00/92.40\nCurrent Stack Size/Max 240K/240K\n",
        "nodeVersion": "v8.2.1"
      }

   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :statuscode 200: No error
   :statuscode 401: Invalid credentials

   **CURL example**:

   ::

    curl -X GET -H 'X-Access-Token: yJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDUzOTY0ODh9.xCf6fbvOPc-CkYdD9MPxLXBEukHm1KX6w5zN5q55OBQ' -H 'X-Key: c1d19874-f2bb-4284-94ac-043cb97288fe' "https://app.webitel.com/api/v2/status"
