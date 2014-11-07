Assets
======

.. toctree::
  :maxdepth: 2

.. note:: The API only provides read only access to project assets. They cannot be created via the API.

Three types of assets are associated with projects:

 - Files - Any type of file that has been uploaded to a projects, such as images or documents.
 - Captured Urls - These are image 'snapshots' of urls that have added to a project.
 - Copy - HTML Text that has been added to the project for collaboration, including marked up revisions.

Object Properties
_________________

Shared Properties
+++++++++++++++++

All assets share the following properties.

====================  ========  ===============
Property              Type      Description
====================  ========  ===============
id                    int       Unique identifier
name                  string    Name
description           string    Description of the object
created_by            string    Name of the creator (falls back to email address)
created               datetime  Date created
modified              datetime  Date last modified
====================  ========  ===============

File Object
+++++++++++

Files have the following additional properties.

=====================  ========  ===============
Property               Type      Description
=====================  ========  ===============
type                   string    The 'guessed' MIME type
created_by             string    Name of the creator (falls back to email address)
_links                 href      Links to the uploaded file
_thumbnail             href      Links to file thumbnails
=====================  ========  ===============


Captured Url Object
+++++++++++++++++++

Urls have the following additional properties.

====================  ========  ===============
Property              Type      Description
====================  ========  ===============
url                   string    The url that was recorded
_links                href      Links to the uploaded file
_thumbnail            href      Links to url thumbnails
====================  ========  ===============


Copy Object
+++++++++++

Copy objects have the following additional properties.

====================  ========  ===============
Property              Type      Description
====================  ========  ===============
text                  string    Current text
====================  ========  ===============

Retrieve Files
______________

.. http:get:: /projects/[id]/files.json

   Returns files uploaded to the projects.

   :query offset: Default is 0
   :query limit: Default is 30

   **Example Response**

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Content-Type: application/json

         [
           {
             "id": 1234,
             "name": "File name",
             "created": "2014-11-04T00:29:01+00:00",
             "modified": null,
             "description": "File description",
             "type": "image/png",
             "created_by": "admin@yourorganisation.com",
              "_thumbnails": {
                 "small": {
                   "href": "https://thecdn.com/small/54581ddd80d84.png"
                 },
                 "medium": {
                   "href": "https://thecdn.com/medium/54581ddd80d84.png"
                 },
                 "large": {
                   "href": "https://thecdn.com/large/54581ddd80d84.png"
                 }
              }
            }
         ]


Retrieve Captured Urls
______________________

.. http:get:: /projects/[id]/urls.json

   Returns urls added to a project

   :query offset: Default is 0
   :query limit: Default is 30

   **Example Response**

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Content-Type: application/json

        [
          {
            "id": 1234,
            "name": "Url name",
            "created": "2014-11-04T00:29:01+00:00",
            "modified": null,
            "description": "Url description",
            "url": "http://www.theurl.com",
            "type": "image/png",
            "created_by": "admin@yourorganisation.com",
             "_thumbnails": {
                "small": {
                  "href": "https://thecdn.com/small/54581ddd80d84.png"
                },
                "medium": {
                  "href": "https://thecdn.com/medium/54581ddd80d84.png"
                },
                "large": {
                  "href": "https://thecdn.com/large/54581ddd80d84.png"
                }
             }
           }
        ]


Retrieve Copy
_____________

.. http:get:: /projects/[id]/copy.json

   Returns copy added to a project

   :query offset: Default is 0
   :query limit: Default is 30

   **Example Response**

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Content-Type: application/json

        [
          {
            "id": 1234,
            "name": "Copy name",
            "created": "2014-11-04T00:29:01+00:00",
            "modified": null,
            "description": "Url description",
            "text": "This is the latest version of the copy",
            "created_by": "admin@yourorganisation.com"
           }
        ]


Retrieve Copy Revisions
_______________________

.. http:get:: /copy/[id/revisions.json

   Returns the revision history for copy, including the marked up changes

   :query offset: Default is 0
   :query limit: Default is 30

   **Example Response**

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Content-Type: application/json

        [
          {
            "id": 1234,
            "name": "Copy name",
            "created": "2014-11-04T00:29:01+00:00",
            "modified": null,
            "modified_by": "themodifier@yourorganisation.com",
            "description": "Url description",
            "text": "This is the latest version of the copy",
            "text_diff": "Html marked up difference"
           }
        ]

