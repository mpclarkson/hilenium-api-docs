Organizations
=============

.. toctree::
   :maxdepth: 2

.. note::

   You can only access your own organization. Organizations cannot be deleted or created.

====================  ========  ===============
Property              Type      Description
====================  ========  ===============
name                  string    Name
address.street        string    Street Line 1
address.street2       string    Street Line 2
address.city          string    City
address.region_name   string    State, Province or Region
address.postal_code   string    Zip / Post Code
address.country       string    Two letter ISO country code
website               string    Valid URL
phone                 string    Primary telephone number
email                 string    Primary email address
email_billing         string    Billing email address. Defaults to primary email.
created               datetime  Date created
modified              datetime  Date last modified
====================  ========  ===============

Retrieve your Organization
__________________________

.. http:get:: /organizations.json

   Returns the user's organization.

   **Example Response**

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Content-Type: application/json

          {
              "name": "My Organization Name",
              "address": {
                "street": "Street 1",
                "street2": "Street 2",
                "city": "City",
                "region_name": "Region name",
                "postal_code": "Zip code",
                "country": "US"
              },
              "website": "http://www.myorganizationname.com",
              "phone": "555-5555",
              "email": "admin@myorganizationname.com",
              "email_billing": "billing@myorganizationname.com"
          }


Update your Organization
________________________

.. http:patch:: /organizations.json

   Updates the user's organization. Only include the properties you wish to update in the JSON object.

   **Example Response**

   .. sourcecode:: http

      HTTP/1.1 204 OK

.. note::

   You must be a company administrator to update your organization.

