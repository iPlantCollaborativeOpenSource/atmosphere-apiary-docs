# Group Profile
The Profile contains information about the authenticated user. Profile can be thought of as the 'entry-point' to the Atmosphere APIs. Once authentiated, a user can find their default provider and identity. The IDs for provider and Identity can be used to navigate the rest of the API.

## Profile [/profile]
A single Profile object.

Each Profile has the following properties:

- **user**: the id for the user this profile is for
- **username**: the username of the user this profile belongs to (**todo:** we don't need user and username)
- **email**: some kind of hash of the users email? This is a bug. (**todo:** fix this :( )
- **is_staff**: true if the user is iPlant staff
- **is_superuser**: true if the user is a super user (comes with special permissions)
- **groups**: (**todo:** remove this field from the API.  There is no client side reason this field would be used)
- **send_emails**: true if the user wants to be notified via email when instances they've launched are ready
- **quick_launch**: (**todo:** remove this from profile)
- **vnc_resolution**: (**todo:** remove this from profile)
- **default_size**: (**todo:** remove this from profile)
- **background**: (**todo:** remove this from profile)
- **icon_set**: the type of icons the user would like to see on images when no image specific icon has been set
- **selected_identity**: (**todo:** remove this from profile)


+ Model (application/json)

    JSON representation of Profile Resource.

    + Body

            {
                "user": 1,
                "username": "username",
                "email": "username@example.com",
                "is_staff": false,
                "is_superuser": false,
                "groups": [
                    "username"
                ],
                "send_emails": true,
                "quick_launch": true,
                "vnc_resolution": "800x600",
                "default_size": "m1.small",
                "background": "default",
                "icon_set": "default",
                "selected_identity": {
                    "quota": {
                        "mem": 256,
                        "suspended_count": 2,
                        "storage": 1000,
                        "cpu": 128,
                        "storage_count": 10
                    },
                    "provider_id": 1,
                    "id": 1,
                    "provider": "planet tatooine"
                }
            }
            
### Retrieve the Profile [GET]
+ Response 200 (application/json)

    [Profile][]
