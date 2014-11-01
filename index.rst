.. Hilenium Api Documentation documentation master file, created by
   sphinx-quickstart on Thu Oct 30 16:03:21 2014.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Introduction
============

.. toctree::
   :hidden:

   self

The `Hilenium`_ public API follows REST conventions and uses HTTP verbs and response codes to ensure you can securely access resources without requiring complex libraries. Cross-origin resource sharing is supported. All responses are in JSON format.

Authentication
_______________

Authentication is conducted using **HTTP Basic** over **HTTPS**. You must provide a valid API key as the username for each request. A password is not required. Api Keys are available via your account page. Api keys should be kept private and should **never** be published in client side code.

**Example cURL request**

   .. sourcecode:: bash

     curl https://www.hilenium.com/public/api/users.json -u yoursecureapikey:

**Example HTTP request**

   .. sourcecode:: http

      GET public/api/users.json HTTP/1.1
      Host: https://www.hilenium.com/
      Authorization: Basic yoursecureapikey
      Accept: application/json

.. note::

   An API key is associated with an individual user and it only provides access to resources and actions the user is permitted to perform. In most cases you should ensure the API key for your integration is associated with a user with administrator access to your account.


Rate Limits
___________

While we do keep track of requests made with each Api key, we do not *currently* impose any rate limits or restrictions on the number of requests that can be made. This may change in the future.

Response Codes
______________

Standard HTTP response codes are used. Anything in the 2XX range indicates a successful response and the 4XX range indicates there is a problem with your request. Common response codes used in the Api are:

**Success Codes**

- 200: Generic successful response
- 201: Resource created successfully
- 204: Resource updated successfully, no content is included in the response.

**Failure Codes**

- 401: The request requires authentication
- 403: The user is not permitted to perform the action
- 404: Resource could not be found.

HTTP Methods
____________

The following HTTP methods available via the Api are:

- GET: Request a resource or array of resources
- PATCH: Modify an existing resource (PUT is not used).
- POST: Create a new resource
- DELETE: Delete a resource.

.. note:: Not all methods are permitted or are available for all resources.

Resources
_________

For detailed information about the api resources please see the following sections.

.. toctree::
   :maxdepth: 2

   resources/index

.. _Hilenium: http://www.hilenium.com