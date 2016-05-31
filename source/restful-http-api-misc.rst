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

   .. sourcecode:: http

      HTTP/1.1 200 OK

      {
        "Version": "3.3.0-sha1:73b7f480dcf48e52b87e4dad6af38550d6a3690e",
        "Node memory": {
          "rss": "58.4 MB",
          "heapTotal": "35.8 MB",
          "heapUsed": "28.6 MB"
        },
        "Process ID": 11,
        "Socket sessions": 200,
        "Process up time": "144:34:32",
        "OS": {
          "Total memory": "7.7 GB",
          "Free memory": "5.2 GB",
          "Platform": "linux",
          "Name": "Linux",
          "Architecture": "x64"
        },
        "Users session": 50,
        "Max users session": 100,
        "Domain session": 10,
        "Webitel": {
          "Status": "Connected",
          "ApiQueue": 0,
          "CmdQueue": 0,
          "Version": "3.3.0",
          "Sid": "00aa0000-0000-000a-0a00-aa0000000000\n"
        },
        "CRASH_WORKER_COUNT": "0",
        "freeSWITCH": "UP 0 years, 0 days, 4 hours, 34 minutes, 30 seconds, 956 milliseconds, 139 microseconds\nFreeSWITCH (Version 1.6.8 git 99de0ad 2016-05-05 15:38:32Z 64bit) is ready\n11893 session(s) since startup\n10 session(s) - peak 20, last 5min 10 \n0 session(s) per Sec out of max 30, peak 37, last 5min 0 \n1000 session(s) max\nmin idle cpu 0.00/95.93\nCurrent Stack Size/Max 240K/240K\n",
        "Node version": "v6.2.0"
      }

   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :statuscode 200: No error
   :statuscode 401: Invalid credentials

   **CURL example**:

   ::

    curl -X GET -H 'X-Access-Token: yJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDUzOTY0ODh9.xCf6fbvOPc-CkYdD9MPxLXBEukHm1KX6w5zN5q55OBQ' -H 'X-Key: c1d19874-f2bb-4284-94ac-043cb97288fe' "https://app.webitel.com/api/v2/status"
