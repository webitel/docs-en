.. _restful-http-api-channels:

Channels
========

Getting active channel list
+++++++++++++++++++++++++++

.. http:get:: /api/v2/channels 

   **Example request**:

   .. sourcecode:: http

      GET /api/v2/channels HTTP/1.1
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

        {
        "status":"OK",
        "data":{
            "row_count":1,
            "rows":[{
                "uuid":"d16592f8-e9c2-409d-a994-13c033b282ab",
                "direction":"inbound",
                "created":"2015-09-06 20:05:11",
                "created_epoch":"1441569911",
                "name":"sofia/internal/201@10.10.10.144",
                "state":"CS_EXECUTE",
                "cid_name":"201",
                "cid_num":"201",
                "ip_addr":"93.75.208.227",
                "dest":"00",
                "application":"conference",
                "application_data":"10.10.10.144@video-mcu-stereo",
                "dialplan":"XML",
                "context":"default",
                "read_codec":"L16","read_rate":"48000",
                "read_bit_rate":"768000",
                "write_codec":"opus",
                "write_rate":"48000",
                "write_bit_rate":"0",
                "secure":"",
                "hostname":"webitel",
                "presence_id":"201@10.10.10.144",
                "presence_data":"",
                "callstate":"ACTIVE",
                "callee_name":"",
                "callee_num":"",
                "callee_direction":"",
                "call_uuid":"",
                "sent_callee_name":"",
                "sent_callee_num":"",
                "initial_cid_name":"201",
                "initial_cid_num":"201",
                "initial_ip_addr":"93.75.208.227",
                "initial_dest":"00",
                "initial_dialplan":"XML",
                "initial_context":"default"}]
            }
        }

   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :statuscode 200: No error

   ::

    curl -XGET -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIxNzA0NDk2NTB9.WqTx_dpbuTyp-l8w6rmQhzoatI-qPRkoM-hmxXTAzaU' -H 'X-Key: bed5ea60-84e7-4eba-b6ad-e3a23f220be1' "https://api.webitel.com:10022/api/v2/channels"

Originating a new call
++++++++++++++++++++++

.. http:post:: /api/v2/channels 

   **Example request**:

   .. sourcecode:: http

      POST /api/v2/channels HTTP/1.1
      Content-Type: application/json
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

        {
            "calledId":"00",
            "callerId": "201@10.10.10.144",
            "auto_answer_param": "sip_h_Call-Info=answer-after=0"
        }

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

        {
            "status":"OK",
            "info":"+OK d917a647-7378-4b02-a3e6-0c24cc7feeac\n",
        }


   :<json string calledId: Destination number.
   :<json string callerId: Call from user.
   :<json string auto_answer_param: SIP auto answer header.
   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :reqheader Content-Type: `application/json`
   :statuscode 200: No error
   :statuscode 400: Bad request

   ::

    curl -XPOST -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIxNzUxMjk5ODF9.DFtcez2ntKLsTsQ5SHYtlwXLf9UC3UbxfMIFRZlCgOE' -H 'X-Key: 1809dfa7-243c-49a6-a5ef-67f9d9565f3f'  -H 'Content-Type: application/json' -d '{"calledId":"00","callerId": "201@10.10.10.144","auto_answer_param": "sip_h_Call-Info=answer-after=0"}' "https://api.webitel.com:10022/api/v2/channels"

Updating channel state
++++++++++++++++++++++

.. http:put:: /api/v2/channels/(channel_id)

   **Example request**:

   .. sourcecode:: http

      PUT /api/v2/channels/6efeb018-7356-4a2b-9ffc-78e78a9b8c47 HTTP/1.1
      Content-Type: application/json
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

        {
            "state": "hold"
        }

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

        {
            "status":"OK",
            "info":"+OK Success\n",
        }

   :param uuid channel_id: The channel uuid.
   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :reqheader Content-Type: `application/json`
   :<json string state: hold or unhold active channel.
   :statuscode 200: No error
   :statuscode 400: Bad request

   ::

    curl -XPUT  -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIxNzUxMjk5ODF9.DFtcez2ntKLsTsQ5SHYtlwXLf9UC3UbxfMIFRZlCgOE' -H 'X-Key: 1809dfa7-243c-49a6-a5ef-67f9d9565f3f'  -H 'Content-Type: application/json' -d '{"state": "hold"}'  "https://api.webitel.com:10022/api/v2/channels/6efeb018-7356-4a2b-9ffc-78e78a9b8c47"

Hanging up active channel
+++++++++++++++++++++++++

.. http:delete:: /api/v2/channels/(channel_id)

   **Example request**:

   .. sourcecode:: http

      DELETE /api/v2/channels/d917a647-7378-4b02-a3e6-0c24cc7feeac HTTP/1.1
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

        {
            "status":"OK",
            "info":"+OK\n",
        }

   :param uuid channel_id: The channel uuid.
   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :statuscode 200: No error
   :statuscode 400: Bad request

   ::

    curl -XDELETE  -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIxNzUxMjk5ODF9.DFtcez2ntKLsTsQ5SHYtlwXLf9UC3UbxfMIFRZlCgOE' -H 'X-Key: 1809dfa7-243c-49a6-a5ef-67f9d9565f3f'  "https://api.webitel.com:10022/api/v2/channels/d917a647-7378-4b02-a3e6-0c24cc7feeac"

Eavesdropping active channel
++++++++++++++++++++++++++++

.. http:post:: /api/v2/channels/(channel_id)/eavesdrop 

   **Example request**:

   .. sourcecode:: http

      POST /api/v2/channels/f09bf0d5-effe-4847-bc79-d0eb179664bc/eavesdrop HTTP/1.1
      Content-Type: application/json
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

        {
            "user":"201"
        }

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

        {
            "status":"OK",
            "info":"+OK 0dc8c0b7-7d7d-45b7-be77-2e1f95c32595\n",
        }


   :param uuid channel_id: The channel uuid.
   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :reqheader Content-Type: `application/json`
   :<json string user: Webitel user ID for callback.
   :statuscode 200: No error
   :statuscode 400: Bad request

   ::

    curl -XPOST -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIxNzUxMjk5ODF9.DFtcez2ntKLsTsQ5SHYtlwXLf9UC3UbxfMIFRZlCgOE' -H 'X-Key: 1809dfa7-243c-49a6-a5ef-67f9d9565f3f'  -H 'Content-Type: application/json' -d '{"user":"201"}' "https://api.webitel.com:10022/api/v2/channels/f09bf0d5-effe-4847-bc79-d0eb179664bc/eavesdrop"

