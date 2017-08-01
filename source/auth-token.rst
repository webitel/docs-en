.. _auth-token:

Auth Token
**********

You can use static domain token or generate user token by login command.

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
          "key": "7db2665d-1e59-4f80-b65c-2372f32d678d",
          "username": "root",
          "expires": 1464587176910,
          "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NjQ1ODcxNzY5MTAsImFjbCI6eyJjZHIiOlsiKiJdLCJjZHIvZmlsZXMiOlsiKiJdLCJjZHIvbWVkaWEiOlsiKiJdfX0.VuQ4Ql7Yq8112E63l3vAnS_ZRzPGMdH_GWiJYh8-p_Y",
          "role": 2,
          "roleName": "root",
          "acl": {
            "license": [
              "*"
            ],
            "system/reload": [
              "*"
            ],
            "account": [
              "*"
            ],
            "domain/item": [
              "*"
            ],
            "domain": [
              "*"
            ],
            "gateway/profile": [
              "*"
            ],
            "gateway": [
              "*"
            ],
            "outbound/list": [
              "*"
            ],
            "cdr/media": [
              "*"
            ],
            "cdr/files": [
              "*"
            ],
            "cdr": [
              "*"
            ],
            "hook": [
              "*"
            ],
            "book": [
              "*"
            ],
            "dialer/members": [
              "*"
            ],
            "dialer": [
              "*"
            ],
            "cc/queue": [
              "*"
            ],
            "cc/members": [
              "*"
            ],
            "cc/tiers": [
              "*"
            ],
            "channels": [
              "*"
            ],
            "rotes/domain": [
              "*"
            ],
            "rotes/extension": [
              "*"
            ],
            "rotes/public": [
              "*"
            ],
            "rotes/default": [
              "*"
            ],
            "calendar": [
              "*"
            ],
            "blacklist": [
              "*"
            ],
            "acl/resource": [
              "*"
            ],
            "acl/roles": [
              "*"
            ]
          },
          "cdr": {
            "host": "http://cdr:10023",
            "useProxy": "true"
          }
      }
        
   :reqheader Content-Type: `application/json`
   :<json string username: User name with domain
   :<json string password: User password
   :>json string key: Token key
   :>json string token: Token secret
   :>json int expires: Token time to live
   :statuscode 200: No error
   :statuscode 400: User name is required
   :statuscode 401: Invalid credentials
   :statuscode 404: User not found

   **CURL example**:

   ::

    curl -X POST -H 'Content-Type: application/json' -d '{"username":"100@mydomain.com","password":"secret"}' "https://api.webitel.com/login"

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

   **CURL example**:

   ::

    curl -X POST -H 'X-Access-Token: yJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDUzOTY0ODh9.xCf6fbvOPc-CkYdD9MPxLXBEukHm1KX6w5zN5q55OBQ' -H 'X-Key: c1d19874-f2bb-4284-94ac-043cb97288fe' "https://api.webitel.com/logout"

