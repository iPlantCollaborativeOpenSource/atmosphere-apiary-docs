# Group Volume
Volumes are network based storage that a user can attach to any instance.  They can then be detached and attached to a
 different instance.

## Volume [/provider/{providerId}/identity/{identityId}/volume/{id}]
A single Volume object.

Each Volume has the following properties:

- **alias**: id (**todo:** we need to standardize on id instead of alias.  Different resources use a different name and
 it should be consistent across all resources)
- **created_by**: user id of the person who created the volume (**todo:** is this not the same as identity?  Also other
 created_by fields are using username.  Why is this one using a numbered id?)
- **name**: name of the volume
- **description**: description of the volume
- **status**: status of the volume (attached, available, trasition states) (**todo:** add state list)
- **size**: size of the volume in Gigabytes
- **attach_data**: 
- **provider**: provider the volume is created on?  (**todo:** aren't all volumes created on iTads?)
- **identity**: account the volume is owned by (**todo:** doesn't this make provider redundant?  provider is an
 identity property)

+ Parameters
    + id (required, string, '13138b97-786a-4e57-9acc-5d41cfd21f75') ... String `alias` of the Volume.
    + providerId (required, number, '1') ... Number `id` of the Provider.
    + identityId (required, number, '1') ... Number `id` of the Identity.
    
+ Model (application/json)

    JSON representation of Volume Resource.

    + Body

            {
                "alias": "232333c94-7864-4157-9cq-5441ff321F11",
                "created_by": 1,
                "name": "My_Other_Volume",
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

### Retrieve a Volume [GET]
+ Response 200 (application/json)

    [Volume][]
    
### Destroy a Volume [DELETE]
Destroy a volume.

+ Response 200 (application/json)

    [Volume][]

## Volumes Collection [/provider/{providerId}/identity/{identityId}/volume]
Collection of all Volumes.

+ Parameters
    + providerId (required, number, '1') ... Number `id` of the Provider.
    + identityId (required, number, '1') ... Number `id` of the Identity.
    
+ Model (application/json)

    JSON representation of Volumes Collection Resource.

    + Body

            [
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
                },
                {
                    "status": "in-use",
                    "attach_data": {
                        "device": "/dev/vdc",
                        "instanceId": "bac30113-423d-44bd-8d7a-41136e9ers34",
                        "serverId": "abc30021-49d7-3ebg-837p-2712623r3732",
                        "id": "1113297-786a-4e57-9acc-5d41cfd21f75",
                        "volumeId": "123138b97-282b-2r55-8ddg-5d4ddfde1f76"
                    },
                    "identity": {
                        "id": 1,
                        "created_by": "HanSolo",
                        "provider": 1
                    },
                    "alias": "13138b97-786a-4e57-9acc-5d41cfd21f76",
                    "provider": 1,
                    "size": 10,
                    "name": "My_Second_Volume",
                    "description": "",
                    "created_by": 1,
                    "start_date": "2014-05-13T00:24:58Z"
                }
            ]
    
### List all Volumes [GET]
+ Response 200 (application/json)

    [Volumes Collection][]

### Create a Volume [POST]
Create a volume.  You must specify the following properties:

- **name**: the name of the volume
- **size**: the size of the volume in Gigabytes
- **description**: a description of the volume

+ Request (application/json)

        {
            "name": "New Volume",
            "description": "Description of new volume",
            "size": 1
        }

+ Response 201 (application/json)

    [Volume][]
