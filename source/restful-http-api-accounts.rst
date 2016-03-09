.. _restful-http-api-accounts:

Accounts
========

Getting accounts list
+++++++++++++++++++++

.. http:get:: /api/v2/accounts 

   **Example request**:

   .. sourcecode:: http

      GET /api/v2/accounts HTTP/1.1
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

      {
        "status": "OK",
        "data": {
            "100": {
                "id": "100",
                "domain": "10.10.10.144",
                "scheme": "account",
                "online": false,
                "state": "nonreg"
            },
            "101": {
                "id": "101",
                "domain": "10.10.10.144",
                "scheme": "account",
                "online": false,
                "state": "nonreg"
            }
         }
      }


   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :statuscode 200: No error
   :statuscode 400: Bad request

   **CURL example**:

   ::

    curl -XGET -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIxNzA0NDk2NTB9.WqTx_dpbuTyp-l8w6rmQhzoatI-qPRkoM-hmxXTAzaU' -H 'X-Key: bed5ea60-84e7-4eba-b6ad-e3a23f220be1'  "https://cloud.webitel.com/engine/api/v2/accounts"

Get an account info
+++++++++++++++++++

.. http:get:: /api/v2/accounts/(account_id) 

   **Example request**:

   .. sourcecode:: http

      GET /api/v2/accounts/100 HTTP/1.1
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

      {
        "status":"OK",
        "data":{
            "a1-hash":"dbe77b19c3d79717d910900a2595bed7",
            "dial-string":"{webitel_call_uuid=${create_uuid()},sip_invite_domain=10.10.10.144}${sofia_contact(\*/100@10.10.10.144)},${verto_contact(100@10.10.10.144)}",
            "jsonrpc-allowed-event-channels":"demo,conference,presence",
            "jsonrpc-allowed-methods":"verto,fsapi",
            "jsonrpc-password":"100",
            "jsonrpc-allowed-fsapi":"version",
            "cc-agent":"true",
            "cc-agent-type":"callback",
            "vm-enabled":"true",
            "vm-password":"1234",
            "cc-agent-contact":"{presence_id=100@10.10.10.144}{webitel_call_uuid=${create_uuid()},sip_invite_domain=10.10.10.144}${sofia_contact(\*/100@10.10.10.144)},${verto_contact(100@10.10.10.144)}",
            "cc-agent-max-no-answer":"3",
            "webitel-extensions":"100",
            "http-allowed-api":"voicemail",
            "webitel-admin":"true",
            "variable_w_domain":"10.10.10.144",
            "variable_user_scheme":"account",
            "variable_user_context":"default",
            "variable_effective_caller_id_name":"Igor",
            "variable_outbound_caller_id_name":"100",
            "variable_account_role":"admin",
            "variable_default_language":"ru"
            }
      }


   :param string account_id: Webitel Account ID
   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :statuscode 200: No error
   :statuscode 400: Bad request
   :statuscode 404: Not found

   **CURL example**:

   ::

    curl -XGET -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIxNzA0NDk2NTB9.WqTx_dpbuTyp-l8w6rmQhzoatI-qPRkoM-hmxXTAzaU' -H 'X-Key: bed5ea60-84e7-4eba-b6ad-e3a23f220be1' "https://cloud.webitel.com/engine/api/v2/accounts/100"

Creat an account
++++++++++++++++

.. http:post:: /api/v2/accounts 

   **Example request**:

   .. sourcecode:: http

      POST /api/v2/accounts HTTP/1.1
      Content-Type: application/json
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

      {
        "login": "109",
        "password": "109",
        "role": "user",
        "domain": "10.10.10.144",
        "parameters": ["vm-enabled=true", "webitel-extensions=109"],
        "variables": ["default_language=ru"]
      }

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

      {
        "status": "OK",
        "data": {
            "a1-hash":"5a3b8a1408181a5a9613b639cf2f65f6",
            "dial-string":"{webitel_call_uuid=${create_uuid()},sip_invite_domain=10.10.10.144}${sofia_contact(\*/109@10.10.10.144)},${verto_contact(109@10.10.10.144)}",
            "webitel-admin":"true",
            "jsonrpc-allowed-event-channels":"demo,conference,presence",
            "jsonrpc-allowed-methods":"verto",
            "jsonrpc-password":"109",
            "cc-agent":"true",
            "webitel-extensions":"109",
            "vm-enabled":"false",
            "variable_w_domain":"10.10.10.144",
            "variable_user_scheme":"account",
            "variable_user_context":"default",
            "variable_effective_caller_id_name":"109",
            "variable_outbound_caller_id_name":"109",
            "variable_account_role":"admin",
            "variable_default_language":"ru"
         }
      }


   :<json string login: Webitel User ID
   :<json string password: User password
   :<json string role: **admin** or **user** role
   :<json string domain: The domain name
   :<json array variables: Additional variables
   :<json array parameters: Additional parameters
   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :reqheader Content-Type: `application/json`
   :statuscode 200: No error
   :statuscode 400: Bad request

   **CURL example**:

   ::

    curl -XPOST -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIxNzA0NDk2NTB9.WqTx_dpbuTyp-l8w6rmQhzoatI-qPRkoM-hmxXTAzaU' -H 'X-Key: bed5ea60-84e7-4eba-b6ad-e3a23f220be1'  -H 'Content-Type: application/json' -d '{"login": "109","password": "109","role": "user","domain": "10.10.10.144", "parameters": ["vm-enabled=true", "webitel-extensions=109"], "variables": ["default_language=ru"]}' "https://cloud.webitel.com/engine/api/v2/accounts"

Updating accounts
+++++++++++++++++

.. http:put:: /api/v2/accounts/(account_id) 

   **Example request**:

   .. sourcecode:: http

      PUT /api/v2/accounts/103 HTTP/1.1
      Content-Type: application/json
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c
      
      {
        "password": "103",
        "variables": ["default_language=ru"]
      } 


   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

      {
        "status":"OK",
        "info":{
            "a1-hash":"5a3b8a1408181a5a9613b639cf2f65f6",
            "dial-string":"{webitel_call_uuid=${create_uuid()},sip_invite_domain=10.10.10.144}${sofia_contact(\*/103@10.10.10.144)},${verto_contact(103@10.10.10.144)}",
            "webitel-admin":"true",
            "jsonrpc-allowed-event-channels":"demo,conference,presence",
            "jsonrpc-allowed-methods":"verto",
            "jsonrpc-password":"103",
            "cc-agent":"true",
            "webitel-extensions":"103",
            "vm-enabled":"false",
            "variable_w_domain":"10.10.10.144",
            "variable_user_scheme":"account",
            "variable_user_context":"default",
            "variable_effective_caller_id_name":"103",
            "variable_outbound_caller_id_name":"103",
            "variable_account_role":"admin",
            "variable_default_language":"ru"
        }
      }


   :param string account_id: Webitel Account ID
   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :reqheader Content-Type: `application/json`
   :statuscode 200: No error
   :statuscode 400: Bad request
   :statuscode 404: Not found

   ::

    curl -XPUT -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIxNzA0NDk2NTB9.WqTx_dpbuTyp-l8w6rmQhzoatI-qPRkoM-hmxXTAzaU' -H 'X-Key: bed5ea60-84e7-4eba-b6ad-e3a23f220be1' -H 'Content-Type: application/json' -d '{"password": "103","variables": ["default_language=ru"]}' "https://cloud.webitel.com/engine/api/v2/accounts/103"

Deleting accounts
+++++++++++++++++

.. http:delete:: /api/v2/accounts/(account_id) 

   **Example request**:

   .. sourcecode:: http

      DELETE /api/v2/accounts/109 HTTP/1.1
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK
      
      {
         "status":"OK",
         "info":"+OK destroyed!\n"
      }
       

   :param string account_id: Webitel Account ID
   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :statuscode 200: No error
   :statuscode 400: Bad request

   ::

    curl -XDELETE -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIxNzA0NDk2NTB9.WqTx_dpbuTyp-l8w6rmQhzoatI-qPRkoM-hmxXTAzaU' -H 'X-Key: bed5ea60-84e7-4eba-b6ad-e3a23f220be1' "https://cloud.webitel.com/engine/api/v2/accounts/109"

