# Group Instance
Instances are virtual machines that users have created from an application (image).  When a user creates an instance
 it immediately starts deducting AU's from their account.

## Instance [/provider/{providerId}/identity/{identityId}/instance/{id}]
A single Instance object.

Each Instance has the following properties:

- **alias**: id
- **alias_hash**: N/A
- **created_by**: username for the person who created the instance
- **status**: active, suspended, shutoff, ... others?
- **size_alias**: the id of the size resource for the instance (number of CPUs, RAM, and Disk Space)
- **machine_alias**: which image the instance was based off.  Machines are image versions.
- **ip_address**: IP address you can use to connect to the machine.  Address that start with 196, 178, or 10 are private,
 all others are public.  Instances with an IP address of 0.0.0.0 have not been assigned an IP address yet.
- **start_date**: the date the instance was created
- **token**: N/A
- **has_shell**: true if a user can ssh into the instance
- **has_vnc**: true if a user can remote desktop into the instance
- **identity**: which account the instance deducts AU's from
- **name**: name of the instance
- **tags**: instance specific tags (array of strings)
    
+ Parameters
    + id (required, string, '26f0795e-f80b-11e3-8ef5-b2227cce2b54') ... String `alias` of the Instance.
    + providerId (required, number, '1') ... Number `id` of the Provider.
    + identityId (required, number, '1') ... Number `id` of the Identity.
    
+ Model (application/json)

    JSON representation of Instance Resource.

    + Body

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

### Retrieve an Instance [GET]
Get a specific instance.

+ Response 200 (application/json)

    [Instance][]
    
### Terminate an Instance [DELETE]
Terminate an instance.

+ Response 200 (application/json)

    [Instance][]
    
## Instance Actions [/provider/{providerId}/identity/{identityId}/instance/{id}/action]

+ Parameters
    + id (required, string, '26f0795e-f80b-11e3-8ef5-b2227cce2b54') ... String `alias` of the Instance.
    + providerId (required, number, '1') ... Number `id` of the Provider.
    + identityId (required, number, '1') ... Number `id` of the Identity.

### Suspend an Instance [POST]
Suspend a running instance.  This will also stop subtracting AU's.

+ Request (application/json)

        { 
            "action": "suspend"
        }

+ Response 200 (application/json)

        {
            "message": "The requested action <suspend> was run successfully",
            "object": null,
            "result": "success"
        }

### Resume an Instance [POST]
Resume a suspended instance.  This will also start subtracting AU's again.

+ Request (application/json)

        { 
            action: "resume"
        }

+ Response 200 (application/json)

        {
            message: "The requested action <resume> was run successfully",
            object: null,
            result: "success"
        }
        
### Stop an Instance [POST]
Stop a running instance.  Stopped instances continue to reduce the AU's.

+ Request (application/json)

        { 
            action: "start"
        }

+ Response 200 (application/json)

        {
            message: "The requested action <start> was run successfully",
            object: null,
            result: "success"
        }
        
### Start an Instance [POST]
Start a stopped instance.

+ Request (application/json)

        { 
            action: "stop"
        }

+ Response 200 (application/json)

        {
            message: "The requested action <stop> was run successfully",
            object: null,
            result: "success"
        }

## Instances Collection [/provider/{providerId}/identity/{identityId}/instance]
Collection of all Instances for a specific identity and provider.

+ Parameters
    + providerId (required, number, '1') ... Number `id` of the Provider.
    + identityId (required, number, '1') ... Number `id` of the Identity.
    
+ Model (application/json)

    JSON representation of Instances Collection Resource.

    + Body

            [
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
            ]
    
### List all Instances [GET]
Get a list of your instances created under the specific provider/identity.

+ Response 200 (application/json)

    [Instances Collection][]
        
### Launch an Instance [POST]
Launch an instance of an application.  You must specify the following properties:

- **machine_alias**: the specific version of the application you'd like to launch an instance of.
- **size_alias**: the size of the virtual machine you need
- **name**: the name of your instance

+ Request (application/json)

        { 
            machine_alias: "237f983e-f80d-11e3-8ef5-b2227cce2b54"
            size_alias: "1"
            name: "Instance Name"
        }

+ Response 201 (application/json)

    [Instance][]

## Instances Collection **legacy** [/instance]
Collection of all Instances, **however the data won't be current**.  This endpoint returns the status of your instances
 the last time the server actually checked, which is the last time you called the real-time endpoint.

### List all Instances [GET]
Get a list of all instances, across all identities and providers, but with values that reflect the last time the
 real-time endpoint was called.

+ Response 200 (application/json)

    [Instances Collection][]
