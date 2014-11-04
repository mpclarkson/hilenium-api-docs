Users
=====

.. toctree::
  :maxdepth: 2


Users are individuals who have access to Hilenium. You can only access users in your organization.

====================  =======  ===============
Property              Type     Description
====================  =======  ===============
id                    int      Unique identifier
email                 string   Email address
group_name            string   The group the user is in. This determine permissions.
active                bool     Identifies if the user is enabled or not (boolean)
profile.first_name    string   First name
profile.last_name     string   Last name
profile.initials      string   2-3 characters that identifies the user in comments
profile.job_title     string   Job title
profile.bio           string   Personal Bio
profile.work_phone    string   Work phone number
profile.mobile_phone  string   Mobile (cell) phone
====================  =======  ===============

List Users
__________

.. http:get:: /users.json

   Returns all users in the organization.

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


Create a User
_____________

.. http:post:: /users.json

   Creates a new user in the organisation.

   :<json string email: Unique email address
   :<json string group_name: Name of the group the user is in
   :<json boolean active: Active (default is true)
   :<json string profile.first_name: First name
   :<json string profile.last_name: Last name
   :<json string profile.initials: Initials/short identifier (3 char max)
   :<json string profile.job_title: Job title
   :<json string profile.work_phone: Work telephone number
   :<json string profile.mobile_phone: Mobile telephone number

   **Example Response**

   .. sourcecode:: http

      HTTP/1.1 201 OK
      Content-Type: application/json

      {
        "id": 1236,
        "email": "user2@yourorganisation.com",
        "group_name": "Editor",
        "active": true,
        "profile": {
          "first_name": "New",
          "last_name": "User",
          "initials": "NU",
          "job_title": "New User",
          "bio": null,
          "work_phone": null,
          "mobile_phone": null
        }
      }


Retrieve a User
_______________

.. http:get:: /users/[id].json

   Returns a single user by their id.

   **Example Response**

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Content-Type: application/json

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
          }


Update a User
_____________

.. http:patch:: /users/[id].json

   Updates a user.

   :<json string email: Unique email address
   :<json string group_name: Name of the group the user is in
   :<json boolean active: Active (default is true)
   :<json string profile.first_name: First name
   :<json string profile.last_name: Last name
   :<json string profile.initials: Initials/short identifier (3 char max)
   :<json string profile.job_title: Job title
   :<json string profile.work_phone: Work telephone number
   :<json string profile.mobile_phone: Mobile telephone number

   **Example Response**

   .. sourcecode:: http

      HTTP/1.1 204 OK

Delete a User
_____________

You cannot currently delete users in Hilenium. Instead set their 'active' status to 'false'.


