# Group Provider
Providers represent the different cloud providers managed by Atmosphere.

## Provider [/provider/{provider_id}]
A single Provider object.

Each Provider has the following properties:

- **type**: cloud provider (AWS, Azure, OpenStack, etc.)
- **location**: the display name for the provider
- **id**: unique id for the provider 
- **description**: a description of the provider
- **virtualization**: **[deprecated]**
- **public**: **[deprecated]**
- **traits**: **[deprecated]** 

+ Parameters
    + provider_id (required, number, '1') ... Number `provider_id` of the Identity.

+ Model(application/json)

    JSON representation of Provider Resource

    + Body

            {
                "id": 1,
                "type": "OpenStack",
                "location": "planetTatooine",
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
                    "id": 1,
                    "type": "OpenStack",
                    "location": "planetTatooine",
                    "description": "planetTatooine",
                    "virtualization": 2,
                    "public": false,
                    "traits": []
                }
            ]
            
### List all Providers [GET]
+ Response 200 (application/json)

    [Providers Collection][]
