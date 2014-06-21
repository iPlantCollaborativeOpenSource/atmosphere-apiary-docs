# Group Provider
Providers represent the different Cloud configurations hosted on Atmosphere. Providers can be of type AWS, Eucalyptus, OpenStack.

## Provider [/api/v1/provider/{provider_id}]
A single Provider object.

Each Provider has the following properties

- **type**: type of provider
- **location**: location of provider 
- **id**: id for that provider 
- **description**: string based description of the provider
- **virtualization**: Number
- **public**: boolean
- **traits**: list 

+ Parameters
    + provider_id (required, number, '1') ... Number `provider_id` of the Identity.

+ Model(application/json)

    JSON representation of Provider Resource

    + Body

              {
                "type": "OpenStack",
                "location": "planetTatooine",
                "id": 1,
                "description": "planetTatooine",
                "virtualization": 2,
                "public": false,
                "traits": []
              }              



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
