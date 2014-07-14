# Group Provider
Providers represent the different Cloud configurations hosted on Atmosphere. Providers can be of type AWS, Eucalyptus, OpenStack.

## Provider [/provider/{provider_id}]
A single Provider object.

Each Provider has the following properties:

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


### Retrieve a Provider [GET]
+ Response 200 (application/json)

    [Provider][]

## Providers Collection [/provider]
Collection of all Providers.

+ Model (application/json)

    JSON representation of Providers Collection Resource.

    + Body

            [
                {
                    "type": "OpenStack",
                    "location": "planetTatooine",
                    "id": 1,
                    "description": "planetTatooine",
                    "virtualization": 2,
                    "public": false,
                    "traits": []
                }
            ]
            
### List all Providers [GET]
+ Response 200 (application/json)

    [Providers Collection][]
