Projects
========

.. toctree::
   :maxdepth: 2

====================  ========  ===============
Property              Type      Description
====================  ========  ===============
id                    int       Unique Identifier
created               datetime  Date created
modified              datetime  Date last modified
name                  string    Name
description           string    Project Description
created_by            string    Name of the user who created the project (fallback is email address)
job_code              string    Your internal code for the project
ownership             string    Internal (created by your company) or External (invited by another company)
_thumbnails           href      Links to project thumbnails in various sizes (the last image added or a default placeholder)
====================  ========  ===============

List Projects
_____________

.. http:get:: /projects.json

   Returns a summary of projects the user has been added to, including those they have been invited to from other organisations.

   :query offset: Default is 0
   :query limit: Default is 30

   **Example Response**

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Content-Type: application/json

        [
          {
             "id": 1234,
             "created": "2014-11-04T00:29:01+00:00",
             "modified": null,
             "title": "Example Project",
             "description": "This is an example marketing project",
             "created_by": "admin@yourorganisation.com",
             "job_code": "Your Unique Project Code",
             "ownership": "internal",
             "_thumbnails": {
               "small": {
                 "href": "http://thecdn.com/small/thumbnail.png"
               },
               "medium": {
                 "href": "http://thecdn.com/medium/thumbnail.png"
               },
               "large": {
                 "href": "http://thecdn.com/large/thumbnail.png"
               }
             }
           }
        ]

Create a Project
________________

.. http:post:: /projects.json

   Creates a new project for the user.

   :<json string name: Project name (50 char)
   :<json string description: The project description (1,000 char)
   :<json string job_code: Internal project identifier (20 char)

   **Example Response**

   .. sourcecode:: http

      HTTP/1.1 201 OK
      Content-Type: application/json

         {
            "id": 1234,
            "created": "2014-11-04T00:29:01+00:00",
            "modified": null,
            "title": "Example Project",
            "description": "This is an example marketing project",
            "created_by": "admin@yourorganisation.com",
            "job_code": "Your Unique Project Code",
            "ownership": "internal",
            "_thumbnails": {
              "small": {
                "href": "http://thecdn.com/small/thumbnail.png"
              },
              "medium": {
                "href": "http://thecdn.com/medium/thumbnail.png"
              },
              "large": {
                "href": "http://thecdn.com/large/thumbnail.png"
              }
            }
          }

.. note:: When a project is created the user is automatically added as a project member.


Retrieve a Project
__________________

.. http:get:: /projects/[id].json

   Returns a project summary by id.

   **Example Response**

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Content-Type: application/json

          {
            "id": 1234,
            "created": "2014-11-04T00:29:01+00:00",
            "modified": null,
            "title": "Example Project",
            "description": "This is an example marketing project",
            "created_by": "admin@yourorganisation.com",
            "job_code": "Your Unique Project Code",
            "ownership": "internal",
            "_thumbnails": {
              "small": {
                "href": "http://thecdn.com/small/thumbnail.png"
              },
              "medium": {
                "href": "http://thecdn.com/medium/thumbnail.png"
              },
              "large": {
                "href": "http://thecdn.com/large/thumbnail.png"
              }
            }
          }

Update a Project
________________

.. http:patch:: /projects/[id].json

   Updates a project. Only include the properties you wish to update in the JSON object.

   **Example Response**

   .. sourcecode:: http

      HTTP/1.1 204 OK

Delete a Project
________________

.. http:delete:: /projects/[id].json

   **Example Response**

   .. sourcecode:: http

      HTTP/1.1 204 OK

   .. note:: You must be either a company administrator or project creator to delete a project.

   .. warning:: Deleting a project is permanent. All project files, comments and assets are deleted. This cannot be reversed.