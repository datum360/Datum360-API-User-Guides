# GET /objects/{types}/{handle}/changes

## Description
Gets the change history for an object matching the provided type and handle. This is the equivelant of viewing the "Change Log" section of the UI for an item.

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters

**type** (required) (path) Item type to query on. Can be one of:  
* TAGGED_ITEM
* DOCUMENT
* EQUIPMENT_ITEM
* EQUIPMENT_MODEL
* EIC 

**handle** (required) (path) The handle of the item to get

**eic** (optional) (query) Handle of the EIC to search in, otherwise active data


## Example Request
`
curl --location 'https://{{systemName}}.pim360.io/api/objects/TAGGED_ITEM/-W4UaC1IS5K5FCmfh5PbSQ/changes?eic=XYSp3hn0TDuJV-NX6MrTBQ' \
--header 'Authorization: ••••••'
`

## Response Body
An array containing objects with details of each individual change.This includes details of the activity that made the change, who made the change and what the attribute value was before the change.

## Example Response
```JSON
[
    {
        "actHdl": "C9ahzDhQSF6-_K_SrRmZzw",
        "name": "Object Import - Wide Format",
        "user": "User",
        "eic": 1,
        "eicIDs": [
            1
        ],
        "ts": "2024-06-18T09:44:51.956Z",
        "changeLog": [
            {
                "name": "Asset Status",
                "icon": "ATTR-INFO",
                "clsHdl": "3OqLZQ7tQISsVK0X-0NVYw",
                "prev": "",
                "next": "Installed",
                "src": "standard attributes",
                "eicID": 1
            }
        ]
    },
    {
        "actHdl": "--jLTDq_QR-GIJaBzCKF_g",
        "name": "Object Import - Wide Format",
        "user": "User",
        "eic": 1,
        "eicIDs": [
            1
        ],
        "ts": "2024-06-18T09:35:04.487Z",
        "changeLog": [
            {
                "name": "plant code",
                "icon": "facility",
                "clsHdl": "QlTaiX6jQZez38iQi8tcag",
                "prev": "",
                "next": "TKF",
                "src": "standard attributes",
                "eicID": 1
            },
            {
                "name": "class name",
                "icon": "ATTR-INFO",
                "clsHdl": "XO19QrZgSjqurYdGbfMvdA",
                "prev": "",
                "next": "blower",
                "src": "standard attributes",
                "eicID": 1
            },
            {
                "name": "tag name",
                "icon": "facility",
                "clsHdl": "y6b-Bxk1S1KbPG-WEjwsBQ",
                "prev": "",
                "next": "BLW-001",
                "src": "standard attributes",
                "eicID": 1
            },
            {
                "icon": "missing",
                "clsHdl": "Object",
                "prev": "",
                "next": "Pending",
                "src": "standard attributes",
                "eicID": 1
            }
        ]
    }
]
```

## Response Status Codes
**200** Change log for item has been successfully retrieved
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Item can not be found. Check that the item handle is correct and the item type is correct.


