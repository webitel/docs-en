.. _restful-http-api:

Abount REST API
***************

The Webitel REST API allows you to manage Webitel Engine and resources within the Webitel in a simple, programmatic way using conventional HTTP requests. The endpoints are intuitive and powerful, allowing you to easily make calls to retrieve information or to execute actions.

Requests
========

Any tool that is fluent in HTTP can communicate with the API simply by requesting the correct URI. Requests should be made using the HTTPS protocol so that traffic is encrypted. The interface responds to different methods depending on the action required.

HTTP Statuses
=============

Along with the HTTP methods that the API responds to, it will also return standard HTTP statuses, including error codes.

In general, if the status returned is in the 200 range, it indicates that the request was fulfilled successfully and that no error was encountered.

Return codes in the 400 range typically indicate that there was an issue with the request that was sent. Among other things, this could mean that you did not authenticate correctly, that you are requesting an action that you do not have authorization for, that the object you are requesting does not exist, or that your request is malformed.

If you receive a status in the 500 range, this generally indicates a server-side problem. This means that we are having an issue on our end and cannot fulfill your request currently.

Responses
=========

When a request is successful, a response body will typically be sent back in the form of a JSON object.

