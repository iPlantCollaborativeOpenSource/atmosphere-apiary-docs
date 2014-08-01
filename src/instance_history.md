# Group Instance History
Instances are virtual machines that users have created from an application (image).  When a user creates an instance
 it immediately starts deducting AU's from their account.

## Instance History [/instance_history/{id}]
A single Instance History object.

Each Instance History has the following properties:

- **alias**: id
- **name**: name of the instance
- **machine_alias**: which image the instance was based off.  Machines are image versions.
- **machine_name**: the name of the image the instance was based off.
- **size_alias**: the size of the instance when launched
- **created_by**: username for the person who created the instance
- **ip_address**: IP address you can use to connect to the machine.  Address that start with 196, 178, or 10 are private,
 all others are public.  Instances with an IP address of 0.0.0.0 have not been assigned an IP address yet.
- **provider**: which cloud the instance was launched on
- **tags**: instance specific tags (array of strings)
- **start_date**: the date the instance was launched
- **end_date**: the date the instance was deleted
- **alias_hash**: **todo: REMOVE**
- **password**: **todo: REMOVE**
- **machine_alias_hash**: **todo: REMOVE**
- **token**: **todo: REMOVE**
    
+ Parameters
    + id (required, string, '36f0795e-f80b-11e3-8ef5-b2227cce2b55') ... String `alias` of the Instance.
    
+ Model (application/json)

    JSON representation of Instance Resource.

    + Body

            {
                "alias": "36f0795e-f80b-11e3-8ef5-b2227cce2b55",
                "name": "Ubuntu 13.04 w/Docker 0.9",
                "machine_alias": "75fdfca4-d49d-4b2d-b919-a3297bc6d7ae",
                "machine_name": "Ubuntu 13.04 w/Docker 0.9",
                "size_alias": "1",
                "created_by": "username",
                "ip_address": "127.0.0.1",
                "provider": "iPlant Cloud - Tucson",
                "tags": ["SpliceGrapher"],
                "start_date": "2014-08-01T20:10:52Z",
                "end_date": null,
                "alias_hash": "c30430ab304a637e0fac9a0322edf7a4",
                "machine_alias_hash": "3fb9e7221c139e3813a2a3aa3ea1b57b",
                "password": "498f96cb-dbd5-42db-a97d-d9f5e786a931",
                "token": "d66503d5-c324-4694-acf9-8b1c5b4d12e2"
            }

### Retrieve an Instance History [GET]
Get a specific instance history object.

+ Response 200 (application/json)

    [Instance History][]

## Instance History Collection [/instance_history]
The history of all of the user's instances since the beginning of time.
    
+ Model (application/json)

    JSON representation of Instances Collection Resource.

    + Body

            {
                "count": 1,
                "next": null,
                "previous": null,
                "results": [
                    {
                        "alias": "36f0795e-f80b-11e3-8ef5-b2227cce2b55",
                        "name": "Ubuntu 13.04 w/Docker 0.9",
                        "machine_alias": "75fdfca4-d49d-4b2d-b919-a3297bc6d7ae",
                        "machine_name": "Ubuntu 13.04 w/Docker 0.9",
                        "size_alias": "1",
                        "created_by": "username",
                        "ip_address": "127.0.0.1",
                        "provider": "iPlant Cloud - Tucson",
                        "tags": ["SpliceGrapher"],
                        "start_date": "2014-08-01T20:10:52Z",
                        "end_date": null,
                        "alias_hash": "c30430ab304a637e0fac9a0322edf7a4",
                        "machine_alias_hash": "3fb9e7221c139e3813a2a3aa3ea1b57b",
                        "password": "498f96cb-dbd5-42db-a97d-d9f5e786a931",
                        "token": "d66503d5-c324-4694-acf9-8b1c5b4d12e2"
                    }
                ]
            }
    
### List all Instances [GET]
Get a list of your instances created under the specific provider/identity.

+ Response 200 (application/json)

    [Instance History Collection][]
