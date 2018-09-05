.. _restful-http-api-media:

Calls
=====

Get call recording
++++++++++++++++++

.. http:get:: /cdr/api/v2/files/(uuid)?file_name=(file_name)

   **Example request**:

   .. sourcecode:: http

      GET /cdr/api/v2/files/e391399f-7424-4eb3-9eef-2b884868b372?file_name=recordSession.mp3 HTTP/1.1
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9.pKXWfzXqbp8FMbOKocNaSlT1bYq4Xqzol-0kEXOY0_s
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK


   :param string uuid: The uuid of the call
   :param string file_name: The new file name
   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :statuscode 200: No error
   :statuscode 400: Bad request
   :statuscode 404: Not found

   **CURL example**:

   ::

    curl -XGET -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIxNzA0NDk2NTB9.WqTx_dpbuTyp-l8w6rmQhzoatI-qPRkoM-hmxXTAzaU' -H 'X-Key: bed5ea60-84e7-4eba-b6ad-e3a23f220be1' "https://cloud.webitel.com/cdr/api/v2/e391399f-7424-4eb3-9eef-2b884868b372?file_name=recordSession.mp3"

