# Group Identity
Identity related resources of the **Atmosphere API**

## Providers Collection [/provider]
### List all Providers [GET]
+ Response 200 (application/json)

        [
            {
                "type": "OpenStack",
                "location": "planet tatooine",
                "id": 1,
                "description": "this is the description of the openstack provider",
                "virtualization": 2,
                "public": false,
                "traits": [
                    1
                ]
            }
        ]

## Provider [/provider/{id}]
A single Provider object with all its details

+ Parameters
    + id (required, number, '1') ... Number `id` of the Provider.

### Retrieve a Provider [GET]
+ Response 200 (application/json)

    + Body

            {
                "type": "OpenStack",
                "location": "planet tatooine",
                "id": 1,
                "description": "This is the description of the OpenStack provider.",
                "virtualization": 2,
                "public": false,
                "traits": [
                    1
                ]
            }
