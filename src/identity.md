# Group Identity
Identities are like user account information. A user has at least one identity per provider, and each identity
 contains information about how many resources can be consumed on that provider.  If a user has multiple identities
 under a single provider, it means they can allocate more resources by using a different identity.

## Identity [/identity/{id}]
A single Identity object.

Each Identity has the following properties:

- **id**: id of the Identity
- **provider_id**: the id of the provider this identity is for
- **provider**: **[deprecated]** the name of the provider 
- **quota**: object describing the resources that can be allocated on the provider under this identity
- **quota.mem**: the maximum amount of memory that can be allocated across all instances under this identity
- **quota.suspended_count**: **[deprecated]** how many instances are currently suspended
- **quota.storage**: the maximum storage space that can be allocated across all volumes under this identity
- **quota.cpu**: the number of CPUs that can be allocated across all instance under this identity
- **quota.storage_count**: the maximum number of volumes that can be created under this identity

+ Parameters
    + id (required, number, 1) ... Number `id` of the Identity.
    
+ Model (application/json)

    JSON representation of Identity Resource.

    + Body

            {
                "id": 1,
                "provider_id": 1,
                "provider": "iPlant Cloud - Tucson",
                "quota": {
                    "mem": 256,
                    "suspended_count": 2,
                    "storage": 1000,
                    "cpu": 128,
                    "storage_count": 10
                }
            }

## Identity Collection [/identity]
Collection of all Identities.

+ Model (application/json)

    JSON representation of Identity Collection Resource.

    + Body

            [
                {
                    "id": 1,
                    "provider_id": 1,
                    "provider": "iPlant Cloud - Tucson",
                    "quota": {
                        "mem": 256,
                        "suspended_count": 2,
                        "storage": 1000,
                        "cpu": 128,
                        "storage_count": 10
                    }
                }
                
            ]
            
### List all Identities [GET]
+ Response 200 (application/json)

    [Identity Collection][]
