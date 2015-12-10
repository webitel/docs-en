.. _auth-token:

Auth Token
**********

Create an auth token
++++++++++++++++++++

.. http:post:: /login

   **Example request**:

   .. sourcecode:: http

      POST /login HTTP/1.1
      Content-Type: application/json 

      {
        "username": "100@mydomain.com",
        "password": "secret"
      }

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Content-Type: application/json 

      { 
          "key":"8fd26a17-eb28-4c74-aa6f-a3794f4f466c",
          "username":"100@mydomain.com",
          "expires":1442002179358,
          "token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s",
          "role":2
      }

   :reqheader Content-Type: `application/json`
   :<json string username: User name with domain
   :<json string password: User password
   :>json string key: Token key
   :>json string token: Token secret
   :>json int expires: Token time to live
   :>json int role: 0 = root; 1 = admin; 2 = user;
   :statuscode 200: No error
   :statuscode 400: User name is required
   :statuscode 401: Invalid credentials
   :statuscode 404: User not found

   ::

    curl -X POST -H 'Content-Type: application/json' -d '{"username":"100@mydomain.com","password":"secret"}' "https://api.webitel.com:10022/login"

Delete an auth token
++++++++++++++++++++

.. http:post:: /logout

   **Example request**:

   .. sourcecode:: http

      POST /logout HTTP/1.1
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

      {
        "status":"OK",
        "info":"Successful logout."
      }

   :statuscode 200: No error
   :statuscode 401: Bad caller

   ::

    curl -X POST -H 'X-Access-Token: yJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDUzOTY0ODh9.xCf6fbvOPc-CkYdD9MPxLXBEukHm1KX6w5zN5q55OBQ' -H 'X-Key: c1d19874-f2bb-4284-94ac-043cb97288fe' "https://api.webitel.com:10022/logout"

