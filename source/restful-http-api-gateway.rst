.. _restful-http-api-gateway:

Gateway
*******

Default route
=============

Getting default route list
++++++++++++++++++++++++++

.. http:get:: /api/v2/routes/default?domain=(domain_name)

   **Example request**:

   .. sourcecode:: http

      GET /api/v2/routes/default?domain=my.domain.com HTTP/1.1
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

        [
            {
                "_id": "56e2e32c93aa980c00564670",
                "destination_number": "^1000$",
                "name": "My new route",
                "order": 0,
                "disabled": false,
                "domain": "my.domain.com",
                "fs_timezone": null,
                "callflow": [
                {
                    "answer": "200 Ok"
                },
                {
                    "queue": {
                    "name": "main"
                    },
                    "break": true
                }
                ],
                "version": 2
            }
        ]

   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :param string domain_name: Domain name is required
   :statuscode 200: No error
   :statuscode 400: Bad request

   **CURL example**:

   ::

    curl -XGET -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NjQ1ODcxNzY5MTAsImFjbCI6eyJjZHIiOlsiKiJdLCJjZHIvZmlsZXMiOlsiKiJdLCJjZHIvbWVkaWEiOlsiKiJdfX0.VuQ4Ql7Yq8112E63l3vAnS_ZRzPGMdH_GWiJYh8-p_Y' -H 'X-Key: 7db2665d-1e59-4f80-b65c-2372f32d678d' "https://app.webitel.com/engine/api/v2/routes/default?domain=my.domain.com"
    