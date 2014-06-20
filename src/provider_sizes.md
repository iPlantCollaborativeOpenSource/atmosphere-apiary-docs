# Group Size
Size related resources of the **Atmosphere API**

## Provider Sizes Collection [/provider/{providerId}/identity/{identityId}/size]
+ Parameters
    + providerId (required, number, '1') ... Number `id` of the Provider.
    + identityId (required, number, '1') ... Number `id` of the Identity.
    
### List all Sizes [GET]
For a combination of provider and identity.

+ Response 200 (application/json)

        [
            {
                "occupancy": 0,
                "total": 1,
                "remaining": 1,
                "active": true,
                "alias": "1",
                "name": "m1.tiny",
                "provider": 1,
                "cpu": 1,
                "disk": 0,
                "root": 1,
                "mem": 512
            },
            {
                "occupancy": 0,
                "total": 1,
                "remaining": 1,
                "active": true,
                "alias": "2",
                "name": "m1.small",
                "provider": 1,
                "cpu": 1,
                "disk": 0,
                "root": 20,
                "mem": 2048
            },
            {
                "occupancy": 0,
                "total": 1,
                "remaining": 1,
                "active": true,
                "alias": "3",
                "name": "m1.medium",
                "provider": 1,
                "cpu": 2,
                "disk": 0,
                "root": 40,
                "mem": 4096
            }
        ]
        
## Provider Size [/provider/{providerId}/identity/{identityId}/size/{id}]
A single Size object (in the specified provider) with all its details.

+ Parameters
    + id (required, string, 'b24ce221-1ed4-4317-av7q-b4yf4q4qe3239') ... String `alias` of the Size.
    + providerId (required, number, '1') ... Number `id` of the Provider.
    + identityId (required, number, '1') ... Number `id` of the Identity.

### Retrieve a Size [GET]
+ Response 200 (application/json)

    + Body

            {
                "occupancy": 0,
                "total": 1,
                "remaining": 1,
                "active": true,
                "alias": "1",
                "name": "m1.tiny",
                "provider": 1,
                "cpu": 1,
                "disk": 0,
                "root": 1,
                "mem": 512
            }
