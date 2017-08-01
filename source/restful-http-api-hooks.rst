.. _restful-http-api-hooks:

Hooks
*****

Getting hooks list
==================

.. http:get:: /api/v2/hooks?domain=(domain_name)

   **Example request**:

   .. sourcecode:: http

      GET /api/v2/hooks?domain=demo.domain.com
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6ImUyNjU2OWQ1LWJlMjYtNDg2Yy05ZDY1LWMwMGU2MWQ2OTNjNSIsImV4cCI6MTUwMTg4MDQwMDAwMCwiZCI6ImRlbW8ud2ViaXRlbC5jb20iLCJ0IjoiZG9tYWluIiwidiI6Mn0.nqUnTAi-L_VTxUYDoK8QqSYkclDST5PRMaRlBg8M3hQ

   **Example response**:

   .. sourcecode:: http

        {
        "status": "OK",
        "data": [
            {
            "_id": "59802a53a7ec15000c40926a",
            "domain": "demo.webitel.com",
            "event": "CHANNEL_CREATE",
            "enable": true,
            "description": "",
            "action": {
                "type": "web",
                "method": "POST",
                "url": "https://requestb.in/yoe4hwyo"
            },
            "fields": [],
            "map": {},
            "filter": {},
            "headers": {},
            "auth": {
                "headers": {},
                "map": {},
                "enabled": false
            },
            "customBody": false,
            "rawBody": ""
            }
        ]
        }

   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :param string domain_name: Domain name is required
   :statuscode 200: No error
   :statuscode 400: Bad request

   **CURL example**:

   ::

    curl -XGET -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6ImUyNjU2OWQ1LWJlMjYtNDg2Yy05ZDY1LWMwMGU2MWQ2OTNjNSIsImV4cCI6MTUwMTg4MDQwMDAwMCwiZCI6ImRlbW8ud2ViaXRlbC5jb20iLCJ0IjoiZG9tYWluIiwidiI6Mn0.nqUnTAi-L_VTxUYDoK8QqSYkclDST5PRMaRlBg8M3hQ' "https://pre.webitel.com/engine/api/v2/hooks?domain=demo.domain.com"
    