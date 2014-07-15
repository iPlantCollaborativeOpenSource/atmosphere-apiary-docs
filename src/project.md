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
                "name": "Default",
                "description": "This is my project description",
                "applications": [],
                "instances": [
                    {
                        "alias": "100wer-3c2-48e0-9a34-0623c7d63b62ea",
                        "alias_hash": "f7c8373138a234076098c098098web9e43",
                        "application_name": "Base Image",
                        "application_uuid": "10394-9cc6-5bx3-923e-42234c9f53c",
                        "created_by": "HanSolo",
                        "status": "Unknown",
                        "size_alias": "Unknown",
                        "machine_alias": "a23431q3-2r50-999e-110p-fa21cbc233t2",
                        "machine_name": "iPlant Base Image w VNC (04/21/2012)",
                        "machine_alias_hash": "47f7f56d601be9cad330bc74903e0c38",
                        "ip_address": "74.125.225.169",
                        "start_date": "2014-04-17T22:50:22Z",
                        "token": "103daw-1fa1-44r1-p2e2-31e2e5bbcr6a",
                        "has_shell": false,
                        "has_vnc": false,
                        "identity": {
                            "id": 1,
                            "created_by": "HanSolo",
                            "provider": 1
                        },
                        "name": "Instance Name",
                        "tags": [],
                        "projects": [1]
                    }
                ],
                "volumes": [
                    {
                        "status": "Unknown",
                        "attach_data": "Unknown",
                        "identity": {
                            "id": 1,
                            "created_by": "HanSolo",
                            "provider": 1
                        },
                        "projects": [299],
                        "alias": "2560cd87-6c67-46c7-a3bb-6e3c10e5f191",
                        "provider": 1,
                        "size": 1,
                        "name": "Volume Name",
                        "description": "",
                        "created_by": 1,
                        "start_date": "2014-03-29T21:17:58Z"
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
                    "owner": "Hansolo",
                    "name": "Project 1",
                    "description": "My first project.",
                    "applications": [],
                    "instances": [],
                    "volumes": [],
                    "start_date": "2014-05-01T19:27:40.910Z",
                    "end_date": "2014-05-02T19:47:30.055Z"
                },
                {
                    "id": 2,
                    "owner": "HanSolo",
                    "name": "Project 2",
                    "description": "My second project.",
                    "applications": [],
                    "instances": [
                        {
                            "alias": "7r2833-b853-493m-82b9-f1er58fsaff",
                            "alias_hash": "b81284baf4fa748c8y0n7sn39encf19553b",
                            "application_name": "iPlant Base Image w VNC (04/21/2012)",
                            "application_uuid": "a6b99d36-4cb6-5139-92ce-4q948dj439f53c",
                            "created_by": "HanSolo",
                            "status": "Unknown",
                            "size_alias": "Unknown",
                            "machine_alias": "n5013e33-e934-4bt34-ac0d-ea230d00k4242",
                            "machine_name": "iPlant Base Image w VNC (04/21/2012)",
                            "machine_alias_hash": "47f2342809809823dd330bc74903e0c38",
                            "ip_address": "172.22.2.4",
                            "start_date": "2014-04-17T22:51:19Z",
                            "token": null,
                            "has_shell": false,
                            "has_vnc": false,
                            "identity": {
                                "id": 1,
                                "created_by": "HanSolo",
                                "provider": 1
                            },
                            "name": "Base Image",
                            "tags": [],
                            "projects": [1]
                        }
                    ],
                    "volumes": [
                        {
                            "status": "Unknown",
                            "attach_data": "Unknown",
                            "identity": {
                                "id": 1,
                                "created_by": "HanSolo",
                                "provider": 1
                            },
                            "projects": [199],
                            "alias": "21038ser87-6c67-46c7-a3bb-6e234012f191",
                            "provider": 1,
                            "size": 1,
                            "name": "lololol1331",
                            "description": "",
                            "created_by": 3,
                            "start_date": "2014-03-29T21:17:58Z"
                        }
                    ],
                    "start_date": "2014-04-11T17:51:11.511Z",
                    "end_date": null
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
