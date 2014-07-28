# Group Project
Projects are a way for users to group related resources.  Right now users can add Instances and Volumes to a group, but
 we also plan to support adding documents, hyperlinks, Applications (Images), and letting users control access to their
 Projects (i.e. adding users, removing users, and specifying permissions such as read-only access or modifying content)

## Project [/project/{id}]
A single Project object.

Each Project has the following properties:

- **id**: the id of the project
- **owner**: username of the person who created the project
- **applications**: applications (images) in the project
- **instances**: instances in the project
- **volumes**: volumes in the project
- **name**: project name
- **description**: project description

+ Parameters
    + id (required, number, '1') ... Number `id` of the Project.
    
+ Model (application/json)

    JSON representation of Project Resource.

    + Body

            {
                "id": 1,
                "owner": "HanSolo",
                "name": "Project 1",
                "description": "This is my project description",
                "applications": [],
                "instances": [
                    {
                        "alias": "26f0795e-f80b-11e3-8ef5-b2227cce2b54",
                        "alias_hash": "b30430ab304a637e0fac9a0322edf7a3",
                        "created_by": "username",
                        "status": "active",
                        "size_alias": "1",
                        "machine_alias": "4a254940-f80b-11e3-8ef5-b2227cce2b54",
                        "machine_name": "Ubuntu 13.04 w/Docker 0.9",
                        "machine_alias_hash": "3f8add823804dc73b221a6c8308a8ab2",
                        "ip_address": "127.0.0.1",
                        "start_date": "2014-05-14T18:17:18Z",
                        "token": null,
                        "has_shell": false,
                        "has_vnc": false,
                        "identity": {
                            "id": 1,
                            "created_by": "username",
                            "provider": 1
                        },
                        "name": "Ubuntu 13.04 w/Docker 0.9",
                        "tags": ["SpliceGrapher"],
                        "projects": [
                            1
                        ]
                    }
                ],
                "volumes": [
                    {
                        "alias": "132333c94-7864-4157-9cq-5441ff321F11",
                        "created_by": 1,
                        "name": "My_First_Volume",
                        "description": "",
                        "status": "available",
                        "size": 1,
                        "attach_data": {},
                        "provider": 1,
                        "identity": {
                            "id": 1,
                            "created_by": "HanSolo",
                            "provider": 1
                        },
                        "projects": [
                            1
                        ],
                        "start_date": "2014-05-13T00:24:58Z"
                    }
                ],
                "start_date": "2014-04-11T17:51:11.511Z",
                "end_date": null
            }

### Retrieve a Project [GET]
+ Response 200 (application/json)

    [Project][]
        
### Update a Project [PUT]
+ Request (application/json)

        {
          "description": "A new description for my project."
        }

+ Response 200 (application/json)

    [Project][]

## Projects Collection [/project]
Collection of all Projects.

+ Model (application/json)

    JSON representation of Projects Collection Resource.

    + Body

            [
                {
                    "id": 1,
                    "owner": "HanSolo",
                    "name": "Project 1",
                    "description": "This is my project description",
                    "applications": [],
                    "instances": [
                        {
                            "alias": "26f0795e-f80b-11e3-8ef5-b2227cce2b54",
                            "alias_hash": "b30430ab304a637e0fac9a0322edf7a3",
                            "created_by": "username",
                            "status": "active",
                            "size_alias": "1",
                            "machine_alias": "4a254940-f80b-11e3-8ef5-b2227cce2b54",
                            "machine_name": "Ubuntu 13.04 w/Docker 0.9",
                            "machine_alias_hash": "3f8add823804dc73b221a6c8308a8ab2",
                            "ip_address": "127.0.0.1",
                            "start_date": "2014-05-14T18:17:18Z",
                            "token": null,
                            "has_shell": false,
                            "has_vnc": false,
                            "identity": {
                                "id": 1,
                                "created_by": "username",
                                "provider": 1
                            },
                            "name": "Ubuntu 13.04 w/Docker 0.9",
                            "tags": ["SpliceGrapher"],
                            "projects": [
                                1
                            ]
                        }
                    ],
                    "volumes": [
                        {
                            "alias": "132333c94-7864-4157-9cq-5441ff321F11",
                            "created_by": 1,
                            "name": "My_First_Volume",
                            "description": "",
                            "status": "available",
                            "size": 1,
                            "attach_data": {},
                            "provider": 1,
                            "identity": {
                                "id": 1,
                                "created_by": "HanSolo",
                                "provider": 1
                            },
                            "projects": [
                                1
                            ],
                            "start_date": "2014-05-13T00:24:58Z"
                        }
                    ],
                    "start_date": "2014-04-11T17:51:11.511Z",
                    "end_date": null
                },
                {
                    "id": 2,
                    "owner": "HanSolo",
                    "name": "Project 2",
                    "description": "My second project.",
                    "applications": [],
                    "instances": [],
                    "volumes": [],
                    "start_date": "2014-05-01T19:27:40.910Z",
                    "end_date": "2014-05-02T19:47:30.055Z"
                }
            ]

### List all Projects [GET]
+ Response 200 (application/json)

    [Projects Collection][]

### Create a Project [POST]
Create a Project.  You must specify the following properties:

- **name**: a name for the project
- **description**: a description of the project

+ Request (application/json)

        {
            "name": "My Awesome Project",
            "description": "A description of my awesome project."
        }

+ Response 201 (application/json)

    [Project][]

## Project Instances [/project/{id}/instance]
The Instances attached to the Project.

+ Parameters
    + id (required, number, '1') ... Number `id` of the Project.
    
### Retrieve a Project's Instances [GET]
+ Response 200 (application/json)

    [Instances Collection][]
    
## Project Instance [/project/{project_id}/instance/{instance_id}]
The endpoint to add or remove an Instance from a Project.

+ Parameters
    + project_id (required, number, '1') ... Number `id` of the Project.
    + instance_id (required, string, '26f0795e-f80b-11e3-8ef5-b2227cce2b54') ... Number `alias` of the Instance.
    
### Add Instance to Project [PUT]
+ Response 200 (application/json)

    [Instance][]
    
### Remove Instance from Project [DELETE]
+ Response 204 (application/json)
            
## Project Volumes [/project/{id}/volume]
The Volumes attached to the Project.

+ Parameters
    + id (required, number, '1') ... Number `id` of the Project.
    
### Retrieve a Project's Volumes [GET]
+ Response 200 (application/json)

    [Volumes Collection][]
    
## Project Volume [/project/{project_id}/volume/{volume_id}]
The endpoint to add or remove a Volume from a Project.

+ Parameters
    + project_id (required, number, '1') ... Number `id` of the Project.
    + volume_id (required, string, '13138b97-786a-4e57-9acc-5d41cfd21f75') ... Number `alias` of the Volume.
    
### Add Volume to Project [PUT]
+ Response 200 (application/json)

    [Volume][]
    
### Remove Volume from Project [DELETE]
+ Response 204 (application/json)
