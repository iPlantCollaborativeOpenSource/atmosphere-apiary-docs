# Group Group
Every User is assigned to a Group of their own name initially. This 'usergroup' is then in charge of all the identities, providers, instances, and applications which can be shared among other, larger groups, but can still be tracked back to the original user who made the API request.

## Group [/group/{groupname}]
A single Group object.

Each Group has the following properties:

- **identities**: collection of identities
- **name**: name of the group
- **permissions**: collection of permissions TODO
- **leaders**: collection of numbers regarding the leaders TODO
- **instances**: list of instances that are being used by the group
- **applicaiton**: list of application that are being used by the group
- **provider_machines**: list of provider machines TODO

+ Parameters
    + groupname (required, number, `nameOfGroup`) ... String `nameOfGroup` Retrieve details about a specific group.

+ Model (application/json)

    JSON representation of Group Resource.

    + Body

             {
                 "identities": [
                     {
                         "provider_id": 1,
                         "id": 1
                     }, 
                     {
                         "provider_id": 2,
                         "id": 2
                     }
                 ], 
                 "name": "nameOfGroup", 
                 "permissions": [], 
                 "leaders": [
                    4
                 ], 
                 "instances": [], 
                 "applications": [], 
                 "provider_machines": []
             }

### Retrieve a Single Group [GET]
+ Response 200 (application/json)

    [Group][]

## Groups Collection [/group]
Collection of all Groups

+ Model (application/json)

    JSON representation of Group Collection Resource

    + Body

            [
                {
                    "identities": [
                        {
                           "provider_id": 1,
                           "id": 1
                        }, 
                        {
                           "provider_id": 2,
                           "id": 2
                        }
                    ], 
                    "name": "nameOfGroup", 
                    "permissions": [], 
                    "leaders": [
                        4
                    ], 
                    "instances": [], 
                    "applications": [], 
                    "provider_machines": []
                }
            ]

### List all Groups [GET]
+ Response 200 (application/json)
    [Groups Collection][]
