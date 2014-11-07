Project Users
=============

.. toctree::
   :maxdepth: 2

Project users are people who have access to a project. They can be internal or external to your Hilenium account.

List Project Users
__________________

.. http:get:: /projects/[id]/users.json

   Returns an array of users who have access to a project.

   :query offset: Default is 0
   :query limit: Default is 30

   **Example Response**

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Content-Type: application/json

        [
          {
            "id": 1234,
            "email": "user1@yourorganisation.com",
            "group_name": "Administrator",
            "active": true,
            "profile": {
              "first_name": "User",
              "last_name": "One",
              "initials": "U1",
              "job_title": "Marketing Manager",
              "bio": "A passionate marketing manager who loves integrated campaigns",
              "work_phone": "555-1234",
              "mobile_phone": null
            }
          },
          {
            "id": 1235,
            "email": "user2@yourorganisation.com",
            "group_name": "Editor",
            "active": true,
            "profile": {
              "first_name": "User",
              "last_name": "Three",
              "initials": "U1",
              "job_title": "Marketing Assistant",
              "bio": "Marketing assistant who loves football",
              "work_phone": "555-1235",
              "mobile_phone": null
            }
          }
        ]

Add A User to Project
_____________________

.. http:post:: /projects/[id]/users.json

   Adds a user to a project by their email address or existing user id. Invited users receive a system generated email.

   :<json string user: A user id (preferred) OR
   :<json string email: An email address

   **Example Response**

   .. sourcecode:: http

      HTTP/1.1 201 OK
      Content-Type: application/json

.. warning:: When users are invited by email, the email address is checked to see if the account already exists. If an existing user is found, they are added
   to the project. However, if the user does not have a pre-existing account, a separate account with full administrator access is created for them.
   For this reason, it is advised that you **only invite people from other companies to collaborate on your projects by email**. Users from your organisation
   should be invited by their Hilenium user id.


Remove a User from a Project
____________________________

.. http:delete:: /projects/[id]/users/[id].json

   Removes a user from a project.

   **Example Response**

   .. sourcecode:: http

      HTTP/1.1 204 OK
      Content-Type: application/json

   .. note:: The project creator cannot be removed from a project.
