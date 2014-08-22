# Group Image/Application
Images are snapshots of an instance at some point in time, including all programs and files.  They can be used to create
 a clone of an instance for others to use, or simply to save the state of an instance as a backup or recovery.

## Image [/application/{id}]
A single Image object.

Each Image has the following properties:

- **alias**: unique id of the image
- **icon**: (optional) if a custom display icon has been uploaded for this image, this field will contain the relative
 path to that image (e.g. "/images/icon.png")
- **created_by**: username of the person who created the image
- **uuid_hash**: **[deprecated]**
- **tags**: tags applied to the image (an array of strings).
- **description**: description of the image
- **start_date**: the date the image was created
- **end_date**: Atmosphere implements soft deletes for everything (or nearly everything).  Any images with an
 end_date before the moment the request was made will be filtered out of the result set.  however, end_dates can also be
 used to schedule resources deletion by setting them at a future date.  This can also be used to give someone access to
 a resource for a limited time (such as for a workshop session).
- **private**: if this field is true, it means the access to the image is limited to a group of people that includes you
- **featured**: this boolean field can only be set by Atmosphere staff and is reserved for images that have gone through
 a special review process
- **machines**: admittedly, this field is poorly named, but it represents all the previous versions of this image, which
  includes the current version.  It also shows which cloud providers that image version is available for.
- **is_bookmarked**: **[user specific property]** this field is specific to the user making the request, and shows whether they identified this
 images as being personally significant. In the future this will be taken out and moved to a different endpoint.
- **projects**: **[user specific property]** Shows which projects the user has added this image to.

+ Parameters
    + id (required, string, `bdc31c14-f807-11e3-8ef5-b2227cce2b54`) ... String `uuid` of the Image.
    
+ Model (application/json)

    JSON representation of Image Resource.

    + Body

            {
                "uuid": "bdc31c14-f807-11e3-8ef5-b2227cce2b54",
                "icon": null,
                "created_by": "username",
                "uuid_hash": "318bf81a238d6c263fc7241c1ff41361",
                "name": "Ubuntu 12.04 Updated NoGUI v1",
                "tags": [
                    "Ubuntu",
                    "Featured"
                ],
                "description": "Descriptiong for Ubuntu 12.04 Updated NoGUI v1",
                "start_date": "2014-02-05T01:03:27.903Z",
                "end_date": null,
                "private": false,
                "featured": true,
                "machines": [
                    {
                        "alias": "813557f2-f808-11e3-8ef5-b2227cce2b54",
                        "version": "1",
                        "start_date": "2014-02-04T23:56:40.077Z",
                        "end_date": null,
                        "provider": 1
                    }
                ],
                "is_bookmarked": false,
                "projects": []
            }

### Retrieve a Single Image [GET]
+ Response 200 (application/json)

    [Image][]
    
### Edit an Image [GET]
+ Response 200 (application/json)

    [Image][]

## Images Collection [/application]
Collection of all Images.

This is both a public and private endpoint.  If accessed without being authenticated you will get a list of all public
 images.  If authenticated, you will also get any private images you have permission to use.

+ Model (application/json)

    JSON representation of the Images Collection.

    + Body

            {
                "count": 5,
                "next": null, 
                "previous": null, 
                "results": [
                    {
                        "uuid": "457b8b7c-f809-11e3-8ef5-b2227cce2b54", 
                        "icon": null, 
                        "created_by": "username", 
                        "uuid_hash": "4f8bc92e81dbcb7bd856be34173966e7", 
                        "name": "Ubuntu 13.04 NoGUI Base", 
                        "tags": [], 
                        "description": "Description of Ubuntu 13.04 NoGUI Base", 
                        "start_date": "2014-01-14T23:17:23.813Z", 
                        "end_date": null, 
                        "private": false, 
                        "featured": true, 
                        "machines": [
                            {
                                "alias": "855e8c3d-cefa-4654-8728-32902d4d74c2", 
                                "version": "1", 
                                "start_date": "2014-01-28T05:14:56.114Z", 
                                "end_date": null, 
                                "provider": 1
                            }, 
                            {
                                "alias": "2657cad0-f809-11e3-8ef5-b2227cce2b54", 
                                "version": "2", 
                                "start_date": "2014-01-14T19:25:22.220Z", 
                                "end_date": null, 
                                "provider": 1
                            }
                        ], 
                        "is_bookmarked": false, 
                        "projects": null
                    }, 
                    {
                        "uuid": "589174a6-f809-11e3-8ef5-b2227cce2b54", 
                        "icon": null, 
                        "created_by": "username", 
                        "uuid_hash": "b51ae503a6e4cfef6ec00084f3046db0", 
                        "name": "TCW v1.2", 
                        "tags": [], 
                        "description": "Description for TCW v1.2", 
                        "start_date": "2014-01-16T03:04:29.764Z", 
                        "end_date": null, 
                        "private": false, 
                        "featured": false, 
                        "machines": [
                            {
                                "alias": "8803eb10-f809-11e3-8ef5-b2227cce2b54", 
                                "version": "1", 
                                "start_date": "2014-01-28T05:14:56.114Z", 
                                "end_date": null, 
                                "provider": 1
                            }, 
                            {
                                "alias": "8c632108-f809-11e3-8ef5-b2227cce2b54", 
                                "version": "2", 
                                "start_date": "2014-01-15T13:35:42.820Z", 
                                "end_date": null, 
                                "provider": 1
                            }
                        ], 
                        "is_bookmarked": false, 
                        "projects": null
                    }, 
                    {
                        "uuid": "aa672302-f809-11e3-8ef5-b2227cce2b54", 
                        "icon": null, 
                        "created_by": "username", 
                        "uuid_hash": "ba12c5bec58263cadfeee62131a0242d", 
                        "name": "Ubuntu 13.04 XFCE GUI Base", 
                        "tags": [], 
                        "description": "Description for Ubuntu 13.04 XFCE GUI Base", 
                        "start_date": "2014-01-16T08:10:31.622Z", 
                        "end_date": null, 
                        "private": false, 
                        "featured": true, 
                        "machines": [
                            {
                                "alias": "af851984-f809-11e3-8ef5-b2227cce2b54", 
                                "version": "1", 
                                "start_date": "2014-01-28T05:14:56.114Z", 
                                "end_date": null, 
                                "provider": 1
                            }
                        ], 
                        "is_bookmarked": true, 
                        "projects": null
                    }, 
                    {
                        "uuid": "bdc31c14-f807-11e3-8ef5-b2227cce2b54",
                        "icon": null,
                        "created_by": "username",
                        "uuid_hash": "318bf81a238d6c263fc7241c1ff41361",
                        "name": "Ubuntu 12.04 Updated NoGUI v1",
                        "tags": [
                            "Ubuntu",
                            "Featured"
                        ],
                        "description": "Descriptiong for Ubuntu 12.04 Updated NoGUI v1",
                        "start_date": "2014-02-05T01:03:27.903Z",
                        "end_date": null,
                        "private": false,
                        "featured": true,
                        "machines": [
                            {
                                "alias": "813557f2-f808-11e3-8ef5-b2227cce2b54",
                                "version": "1",
                                "start_date": "2014-02-04T23:56:40.077Z",
                                "end_date": null,
                                "provider": 1
                            }
                        ],
                        "is_bookmarked": false,
                        "projects": []
                    },
                    {
                        "uuid": "8f66dae2-f80a-11e3-8ef5-b2227cce2b54", 
                        "icon": null, 
                        "created_by": "username", 
                        "uuid_hash": "83ae31784ba0e1768f1439ca4b18bb38", 
                        "name": "phytoImage", 
                        "tags": [], 
                        "description": "Description of phytoImage", 
                        "start_date": "2014-01-18T06:12:46.923Z", 
                        "end_date": null, 
                        "private": false, 
                        "featured": false, 
                        "machines": [
                            {
                                "alias": "89b42744-f80a-11e3-8ef5-b2227cce2b54", 
                                "version": "1", 
                                "start_date": "2014-01-28T05:14:56.114Z", 
                                "end_date": null, 
                                "provider": 5
                            }
                        ], 
                        "is_bookmarked": true, 
                        "projects": null
                    }
                ]
            }

### List all Images [GET]

+ Response 200 (application/json)

    [Images Collection][]

## Request an Image [/provider/{providerId}/identity/{identityId}/request_image/]
Images are created by sending a request to Atmosphere support.  This is the endpoint used to make that request.

+ Parameters
    + id (required, string, 'b94d4964-8de3-4965-a87a-f4cf44d33165') ... String `alias` of the Instance.
    + providerId (required, number, '4') ... Number `id` of the Provider.

### Request an Image [POST]
To request an image, you need to specify the following properties:

- **name**: the name of the image
- **instance**: alias property of the instance you want imaged
- **provider**: the id of the provider you want the image to be created for
- **description**: A description of the image for display purposes
- **software**: What software is installed on the instance
- **sys**: (**todo:** add details for what this field controls)
- **exclude**: Files on the instance that should be excluded from the image, like ssh keys
- **tags**: tags that should be applied to the image
- **vis**: This field can be one of public, private, or a user-list. If public, everyone can view and create an instance
  from the image.  If this field is private, the user who created the image will be able to see or launch it.  If user
  specific, only those users that are listed will be able to see or launch the image.

+ Request (application/json)

        {
            instance: "74089c18-f80a-11e3-8ef5-b2227cce2b54",
            ip_address: "127.0.0.1",
            provider: 1,
            description: "I would like to request an image of this instance for [reasons].",
            software: "Description of software installed on the machine.",
            sys: "I'm not sure what this field means.",
            exclude: "I do not need any files excluded from the image.",
            tags: [
                "ESD",
                "BGF",
                "apache2",
                "SpliceGrapher"
            ],
            vis: "public"
        }
