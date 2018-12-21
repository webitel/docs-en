.. _restful-http-api-cdr:

CDR
===

Get CDR data
++++++++++++

Webitel allows you make search request to the elasticsearch index using `request body <https://www.elastic.co/guide/en/elasticsearch/reference/current/search-request-body.html>`_.

.. http:post:: /api/v2/cdr/text

   **Example request**:

   .. sourcecode:: http

      POST /api/v2/cdr/text HTTP/1.1
      Content-Type: application/json
      X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE0NDIwMDIxNzkzNTh9
      X-Key: 8fd26a17-eb28-4c74-aa6f-a3794f4f466c

      {
          "columns": [
              "created_time",
              "caller_id_number",
              "extension",
              "duration",
              "hangup_cause"
          ],
          "filter": [
              {
                  "bool": {
                      "must": [
                          {
                              "range": {
                                  "created_time": {
                                      "gte": "now-2h/h",
                                      "lte": "now"
                                  }
                              }
                          },
                          {
                              "query_string": {
                                  "analyze_wildcard": true,
                                  "default_field": "*",
                                  "query": "caller_id_number:/0[679]3.*/"
                              }
                          }
                      ],
                      "must_not": []
                  }
              }
          ],
          "index": "cdr-a",
          "limit": 10,
          "query": "*",
          "sort": {
              "created_time": {
                  "order": "desc",
                  "unmapped_type": "boolean"
              }
          }
      }


   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK

      {
        "took": 7,
        "timed_out": false,
        "_shards": {
          "total": 5,
          "successful": 5,
          "skipped": 0,
          "failed": 0
        },
        "hits": {
          "total": 4,
          "max_score": null,
          "hits": [
            {
              "_index": "cdr-a-2018-test-domain.webitel.com",
              "_type": "cdr",
              "_id": "8161b3e0-6c3e-4421-bfea-eb174941c7d7",
              "_score": null,
              "fields": {
                "duration": [
                  48
                ],
                "created_time": [
                  "2018-12-01T12:39:13.750Z"
                ],
                "caller_id_number": [
                  "0636499995"
                ],
                "hangup_cause": [
                  "NORMAL_CLEARING"
                ]
              },
              "sort": [
                1543667953750
              ]
            },
            {
              "_index": "cdr-a-2018-test-domain.webitel.com",
              "_type": "cdr",
              "_id": "74567f94-bfea-4a91-9f23-7ed0ea93c6f4",
              "_score": null,
              "fields": {
                "duration": [
                  17
                ],
                "created_time": [
                  "2018-12-01T12:37:57.950Z"
                ],
                "caller_id_number": [
                  "0939358555"
                ],
                "hangup_cause": [
                  "NO_ROUTE_DESTINATION"
                ]
              },
              "sort": [
                1543667877950
              ]
            },
            {
              "_index": "cdr-a-2018-test-domain.webitel.com",
              "_type": "cdr",
              "_id": "00de4e45-00ae-444a-9e85-b94fbbaf992a",
              "_score": null,
              "fields": {
                "duration": [
                  2
                ],
                "created_time": [
                  "2018-12-01T12:37:33.690Z"
                ],
                "caller_id_number": [
                  "0636444445"
                ],
                "hangup_cause": [
                  "NORMAL_CLEARING"
                ]
              },
              "sort": [
                1543667853690
              ]
            },
            {
              "_index": "cdr-a-2018-test-domain.webitel.com",
              "_type": "cdr",
              "_id": "3d21e501-256f-4fd9-b160-62a7c21f576b",
              "_score": null,
              "fields": {
                "duration": [
                  1
                ],
                "created_time": [
                  "2018-12-01T12:37:26.030Z"
                ],
                "caller_id_number": [
                  "0939333333"
                ],
                "hangup_cause": [
                  "NO_ROUTE_DESTINATION"
                ]
              },
              "sort": [
                1543667846030
              ]
            }
          ]
        }
      }


   :reqheader Content-Type: `application/json`
   :reqheader X-Key and X-Access-Token: :ref:`auth-token`
   :statuscode 200: No error
   :statuscode 400: Bad request
   :statuscode 404: Not found

   **CURL example**:

   ::

      curl -XPOST -H 'Content-Type: application/json' \
      -H 'X-Access-Token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9i'\
      "https://cloud.webitel.com/engine/api/v2/cdr/text" \
      -d '{\
          "columns": [\
              "created_time",\
              "caller_id_number",\
              "extension",\
              "duration",\
              "hangup_cause"\
          ],\
          "filter": [\
              {\
                  "bool": {\
                      "must": [\
                          {\
                              "range": {\
                                  "created_time": {\
                                      "gte": "now-2h/h",\
                                      "lte": "now"\
                                  }\
                              }\
                          },\
                          {\
                              "query_string": {\
                                  "analyze_wildcard": true,\
                                  "default_field": "*",\
                                  "query": "caller_id_number:/0[679]3.*/"\
                              }\
                          }\
                      ],\
                      "must_not": []\
                  }\
              }\
          ],\
          "index": "cdr-a",\
          "limit": 10,\
          "query": "*",\
          "sort": {\
              "created_time": {\
                  "order": "desc",\
                  "unmapped_type": "boolean"\
              }\
          }\
      }'
