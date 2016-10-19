.. _restful-http-api-blacklists:

Blacklists
==========

Get blacklists
++++++++++++++

.. http:get:: /api/v2/routes/blacklists?domain=(domain_name)

   **Example request**:

   .. sourcecode:: http

      GET /api/v2/routes/blacklists?domain=my.webitel.com HTTP/1.1
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

        [
            {
                "name": "my_list2"
            },
            {
                "name": "my_list1"
            }
        ]

   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :param string domain_name: Domain name is required
   :statuscode 200: No error

   **CURL example**:

   ::

    curl -XGET -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0ODQ5MDQ3MDU3NjIsImFjbCI6eyJjZHIiOlsiKiJdLCJjZHIvZmlsZXMiOlsiKiJdLCJjZHIvbWVkaWEiOlsiKiJdfX0.XnP93LWRYpgXHH3vQ7YQ4Birdq-VSx4t0m8-iPhrvO4' -H 'X-Key: 0158162b-5d7f-498a-b9bb-0dd82b90f521' "https://api.webitel.com/engine/api/v2/routes/blacklists?domain=my.webitel.com"

Get numbers by blacklist name
+++++++++++++++++++++++++++++

.. http:get:: /api/v2/routes/blacklists/(blacklist_name)?domain=(domain_name)

   **Example request**:

   .. sourcecode:: http

      GET /api/v2/routes/blacklists/my_list2?domain=my.webitel.com HTTP/1.1
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

        [
            {
                "_id": "57fe05554a68369fc7588212",
                "number": "0000",
                "name": "my_list2",
                "domain": "my.webitel.com"
            },
            {
                "_id": "57fe04f74a68369fc7588211",
                "number": "911",
                "name": "my_list2",
                "domain": "my.webitel.com"
            }
        ]

   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :param string domain_name: Domain name is required
   :param string blacklist_name: Blacklist name is required
   :statuscode 200: No error

   **CURL example**:

   ::

    curl -XGET -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0ODQ5MDQ3MDU3NjIsImFjbCI6eyJjZHIiOlsiKiJdLCJjZHIvZmlsZXMiOlsiKiJdLCJjZHIvbWVkaWEiOlsiKiJdfX0.XnP93LWRYpgXHH3vQ7YQ4Birdq-VSx4t0m8-iPhrvO4' -H 'X-Key: 0158162b-5d7f-498a-b9bb-0dd82b90f521' "https://api.webitel.com/engine/api/v2/routes/blacklists/my_list2?domain=my.webitel.com"

Add number into the blaklist
++++++++++++++++++++++++++++

.. http:post:: /api/v2/routes/blacklists/(blacklist_name)?domain=(domain_name) 

   **Example request**:

   .. sourcecode:: http

      POST /api/v2/routes/blacklists/my_list2?domain=my.webitel.com HTTP/1.1
      Content-Type: application/json
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

        {
            "number": "123456789"
         }

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

        {
            "ok": 1,
            "Modified": 1,
            "n": 1
        }

   :<json string number: phone number.
   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :reqheader Content-Type: `application/json`
   :param string domain_name: Domain name is required
   :param string blacklist_name: Blacklist name is required
   :statuscode 200: No error
   :statuscode 400: Bad request

   **CURL example**:

   ::

    curl -XPOST -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0ODQ5MDQ3MDU3NjIsImFjbCI6eyJjZHIiOlsiKiJdLCJjZHIvZmlsZXMiOlsiKiJdLCJjZHIvbWVkaWEiOlsiKiJdfX0.XnP93LWRYpgXHH3vQ7YQ4Birdq-VSx4t0m8-iPhrvO4' -H 'X-Key: 0158162b-5d7f-498a-b9bb-0dd82b90f521' -H 'Content-Type: application/json' -d ' { "number": 123456789 } ' "https://api.webitel.com/engine/api/v2/routes/blacklists/my_list2?domain=my.webitel.com"

Get number in the blaklist
++++++++++++++++++++++++++

.. http:get:: /api/v2/routes/blacklists/(blacklist_name)/(blacklist_number)?domain=(domain_name)

   **Example request**:

   .. sourcecode:: http

      GET /api/v2/routes/blacklists/my_list2/911?domain=my.webitel.com HTTP/1.1
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

        [
            {
                "_id": "57fe04f74a68369fc7588211",
                "number": "911",
                "name": "my_list2",
                "domain": "my.webitel.com"
            }
        ]

   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :param string domain_name: Domain name is required
   :param string blacklist_name: Blacklist name is required
   :param string blacklist_number: Number in the blacklist is required
   :statuscode 200: No error

   **CURL example**:

   ::

    curl -XGET -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0ODQ5MDQ3MDU3NjIsImFjbCI6eyJjZHIiOlsiKiJdLCJjZHIvZmlsZXMiOlsiKiJdLCJjZHIvbWVkaWEiOlsiKiJdfX0.XnP93LWRYpgXHH3vQ7YQ4Birdq-VSx4t0m8-iPhrvO4' -H 'X-Key: 0158162b-5d7f-498a-b9bb-0dd82b90f521' "https://api.webitel.com/engine/api/v2/routes/blacklists/my_list2/911?domain=my.webitel.com"

Delete number from the blaklist
+++++++++++++++++++++++++++++++

.. http:delete:: /api/v2/routes/blacklists/(blacklist_name)/(blacklist_number)?domain=(domain_name)

   **Example request**:

   .. sourcecode:: http

      DELETE /api/v2/routes/blacklists/my_list2/911?domain=my.webitel.com HTTP/1.1
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

       {
         "ok": 1,
         "n": 1
       }

   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :param string domain_name: Domain name is required
   :param string blacklist_name: Blacklist name is required
   :param string blacklist_number: Number in the blacklist is required
   :statuscode 200: No error
   :statuscode 400: Bad request

   **CURL example**:

   ::

    curl -XDELETE -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0ODQ5MDQ3MDU3NjIsImFjbCI6eyJjZHIiOlsiKiJdLCJjZHIvZmlsZXMiOlsiKiJdLCJjZHIvbWVkaWEiOlsiKiJdfX0.XnP93LWRYpgXHH3vQ7YQ4Birdq-VSx4t0m8-iPhrvO4' -H 'X-Key: 0158162b-5d7f-498a-b9bb-0dd82b90f521' "https://api.webitel.com/engine/api/v2/routes/blacklists/my_list2/911?domain=my.webitel.com"

Delete blaklist
+++++++++++++++

.. http:delete:: /api/v2/routes/blacklists/(blacklist_name)?domain=(domain_name)

   **Example request**:

   .. sourcecode:: http

      DELETE /api/v2/routes/blacklists/my_list2?domain=my.webitel.com HTTP/1.1
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

       {
         "ok": 1,
         "n": 1
       }

   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :param string domain_name: Domain name is required
   :param string blacklist_name: Blacklist name is required
   :statuscode 200: No error
   :statuscode 400: Bad request

   **CURL example**:

   ::

    curl -XDELETE -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0ODQ5MDQ3MDU3NjIsImFjbCI6eyJjZHIiOlsiKiJdLCJjZHIvZmlsZXMiOlsiKiJdLCJjZHIvbWVkaWEiOlsiKiJdfX0.XnP93LWRYpgXHH3vQ7YQ4Birdq-VSx4t0m8-iPhrvO4' -H 'X-Key: 0158162b-5d7f-498a-b9bb-0dd82b90f521' "https://api.webitel.com/engine/api/v2/routes/blacklists/my_list2?domain=my.webitel.com"