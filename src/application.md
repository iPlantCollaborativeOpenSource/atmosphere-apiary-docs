# Group Application
Applications are analogous to **Images** or **Snapshots** of a Virtual Machine.

## Application [/application/{id}]
A single Application object.

Each Application has the following properties:

- **alias**: id
- **icon**: custom icon image to use for the application (ex: "/resources/machine_images/ibp.png")
- **created_by**: username of the person who created the application (typically by requesting an instance to be imaged)
- **uuid_hash**: **N/A**
- **tags**: tags applied to the application (an array of strings). Essentially, an application represents the most recent
 version of an image, where the machines are the previous versions, but one of the machines is also the current version.
 I'm not clear on whether these tags are applied to the application directly, or to the most recent machine, and I'm
 also not clear on whether the tags exist on a machine level at all (i.e. whether you can see which tags are applied
 to previous versions)
- **description**: description of the application
- **start_date**: when the application was created (added to Atmosphere)
- **end_date**: Atmosphere implements soft deletes for everything (or nearly everything).  Any applications with an
 end_date before the moment the request was made will (should) be filtered out of the results.  End_dates can also be
 used to schedule resources deletion by setting them at a future date.  This can also be used to give someone access to
 a resource for a limited time (such as for a workshop session).
- **private**: if private is true, it means the access to the resource is limited to a group of people (one of which is
 you.
- **featured**: this boolean field can only be set by administration. It's reserved for images that are deemed worthy of
 special attention.
- **machines**: previous version of the application (image) that also include the current version.  This list also appears
 to contain versions across multiple providers (such as the image for AWS, and the image for OpenStack).
- **is_bookmarked**: this field is specific to the user making the request, and shows whether they identified this
 application as being personally significant. (**todo:** move this into /profile or a /favorited_application endpoint)
- **projects**: User specific property.  Which user projects this application has been added to.  (**todo:** remove this from
 the application object)

+ Parameters
    + id (required, string, `bdc31c14-f807-11e3-8ef5-b2227cce2b54`) ... String `uuid` of the Application.
    
+ Model (application/json)

    JSON representation of Application Resource.

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

### Retrieve a Single Application [GET]
+ Response 200 (application/json)

    [Application][]
    
### Edit an Application [GET]
+ Response 200 (application/json)

    [Application][]

## Applications Collection [/application]
Collection of all Applications.

This is both a public and private endpoint.  If accessed without being authenticated you will get a list of all public
 applications.  If authenticated, you will also get any private images you have permission to use.

+ Model (application/json)

    JSON representation of Applications Collection Resource.

    + Body

            [
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

### List all Applications [GET]

+ Response 200 (application/json)

    [Applications Collection][]

## Creating an Application [/provider/{providerId}/identity/{identityId}/request_image/]
Applications are created by requesting an image be made of a running instance.

+ Parameters
    + id (required, string, 'b94d4964-8de3-4965-a87a-f4cf44d33165') ... String `alias` of the Instance.
    + providerId (required, number, '4') ... Number `id` of the Provider.

### Requesting an Image [POST]
Creating an application is analogous to requesting an image. To do so, specify the following properties:

- **machine_alias**: the specific version of the application you'd like to launch an instance of.
- **size_alias**: the size of the virtual machine you need
- **name**: the name of your instance
- **instance**: alias property of the instance you want imaged
- **ip_address**: (**todo:** figure out why this is here)
- **provider**: the id of the provider you want the image to be created for (**todo:** figure out if this is redundant. Is
 it the same as the provider in the url?  Is it the same as the provider the instance is running on?)
- **description**: A description of either a) what is on the instance, or b) why you're creating the instance (**todo:**
 figure out how this field is used)
- **software**: What software is installed on the instance (**todo:** figure out how this information is used)
- **sys**: (**todo:** figure out what this property means)
- **exclude**: Files on the instance that should be excluded from the image, like ssh keys? (**todo:** figure out what
 this property means)
- **tags**: Additional tags that should be associated with the image? (**todo:** can't this just be carried over from
 the instance?  Are these in addition to the instance tags?  Is this here in case people don't normally tag their
 instances?)
- **vis**: Can be public, private, or a user-list. If public, everyone can see the image.  If private, only you can.  If
 user specific, only those users can see the list (in the future this should be changed by allowing people to manage
 access to their resources themselves).

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
