Authentication
==============

Authentication is conducted using **HTTP Basic** over **HTTPS**. You must provide a valid API key as the username
for each request. A password is not required. API keys are available via your account page.

.. tip::

    API keys are **private** and should never be published in client side code.

**Example cURL request**

   .. sourcecode:: bash

     curl :api_url:public/api/users.json -u yoursecureapikey:

**Example HTTP request**

   .. sourcecode:: http

      GET public/api/users.json HTTP/1.1
      Host: :api_url:
      Authorization: Basic yoursecureapikey
      Accept: application/json

.. note::

   An API key is associated with an individual user and it only provides access to resources and actions
   the user is permitted to perform. In most cases the API key for your integration should be associated
   with a user with administrator access to your account.

