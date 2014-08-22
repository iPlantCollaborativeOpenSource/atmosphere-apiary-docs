# Group Non-Project Resources
Because the API does enforce the concept that resources are in projects, we've provided a way to find out if the user
 has any projects that are not associated with a project.

## Null Project [/project/null]
This endpoint returns a list of all resources that are not associated with a project.

Each Project has the following properties:

- **applications**: images that are not in a project
- **instances**: instances that are not in a project
- **volumes**: volumes that are not in a project
    
+ Model (application/json)

    JSON representation of Null Project Resource.

    + Body

            {
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
                ]
            }

### Retrieve a Project [GET]
+ Response 200 (application/json)

    [Null Project][]
