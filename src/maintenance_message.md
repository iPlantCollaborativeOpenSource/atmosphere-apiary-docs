# Group Maintenance
Maintenance Messages are a way to inform the user of current or planned maintenance desks and possible downtown for the
 Atmosphere cloud.

## Maintenance Message [/maintenance/{id}]
A single Maintenance Message object.

Each Maintenance Message has the following properties:

- **id**: the id of the message
- **title**: a short title for the type of outage (planned, unplanned, network outage, maintenance, etc.)
- **message**: the message
- **provider_id**: the id of the provider this message is for
- **disable_login**: whether login is disabled for the provider while this maintenance is occurring

+ Parameters
    + id (required, Number, 1) ... Number `id` of the Maintenance Message.
    
+ Model (application/json)

    JSON representation of Maintenance Message Resource.

    + Body

            {
                "id": 1,
                "title": "Planned Maintenance",
                "message": "Atmosphere Provider Cloud is under maintenance.",
                "provider_id": 1,
                "disable_login": true,
                "start_date": "2014-07-21T06:05:40Z",
                "end_date": null
            }

### Retrieve a Maintenance Message [GET]
+ Response 200 (application/json)

    [Maintenance Message][]          

## Maintenance Message Collection [/maintenance?active=true]
Collection of all Maintenance Messages. You must pass in active=true if you only want the current messages.

+ Model (application/json)

    JSON representation of Maintenance Message Collection Resource.

    + Body

            [
                {
                    "id": 1,
                    "title": "Planned Maintenance",
                    "message": "Atmosphere Provider Cloud is under maintenance.",
                    "provider_id": 1,
                    "disable_login": true,
                    "start_date": "2014-07-21T06:05:40Z",
                    "end_date": null
                }
            ]

### List all Maintenance Messages [GET]
+ Response 200 (application/json)

    [Maintenance Message Collection][]
