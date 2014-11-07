Groups
======

.. toctree::
  :maxdepth: 2

.. note::

   This is a read-only resource. You cannot create or edit groups.

Groups define the permissions user's have in your system.

====================  =======  ===============
Property              Type     Description
====================  =======  ===============
id                    int      Unique identifier
name                  string   Name of the group
description           string   Short description of the permissions available to the user
====================  =======  ===============

List Groups
___________

.. http:get:: /groups.json

   Returns all groups.

   **Example Response**

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Content-Type: application/json

        [
          {
            "id": 1,
            "name": "Administrator",
            "description": "Full system access"
          }
        ]


Retrieve a Group
________________

.. http:get:: /groups/[id].json

   Returns a single group by its id.

   **Example Response**

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Content-Type: application/json

          {
            "id": 1,
            "name": "Administrator",
            "description": "Full system access"
          }

