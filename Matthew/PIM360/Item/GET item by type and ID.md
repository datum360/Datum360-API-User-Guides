# GET /objects/{{type}}/{{handle}}/id/{{ID}}

## Description
Gets an object by type and its ID. Where ID is the attribute set in the context tab for the item type in CL4CL. For example a Tagged Item might have an ID attribute of "tag name".

**Note: ** There is currently a limitation with this API where it will only return the newest item that matches the `type` and `ID` combination, this is expected to be resolved in V2 of the API.

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

**ID** (required) (path) The ID of the item to get

**eic** (optional) (query string) Handle of the EIC to search in, otherwise Active Data


## Example Request
`
curl --location 'https://{{systemName}}.pim360.io/api/objects/TAGGED_ITEM/id/BLW-001?eic=XYSp3hn0TDuJV-NX6MrTBQ' \
--header 'Authorization: ••••••'
`

## Response Body
An object containing the details of the requested item. Item attributes are held in an object called `attrs` where the keys in the object are the attribute handles, and the values are the attribute details and values. Note that if an item is added to an EIC but not published, if the EIC handle is not provided in the request then tag details will be returned but they will be missing attribute details.

## Example Response
```JSON
{
    "hdl": "-W4UaC1IS5K5FCmfh5PbSQ",
    "type": "TAGGED_ITEM",
    "eic": "XYSp3hn0TDuJV-NX6MrTBQ",
    "id": "BLW-001",
    "facility": "TKF",
    "icon": "TAG",
    "clsname": "blower",
    "link": "",
    "attrs": {
        "y6b-Bxk1S1KbPG-WEjwsBQ": {
            "hdl": "y6b-Bxk1S1KbPG-WEjwsBQ",
            "name": "tag name",
            "icon": "facility",
            "hasLookup": false,
            "hasUOM": false,
            "isNormal": true,
            "value": "BLW-001",
            "typedValue": "BLW-001",
            "typeError": {},
            "dataType": "STRING",
            "uom": null,
            "FTS": "BLW-001",
            "change": true,
            "typedChange": true,
            "conflict": [],
            "provenance": []
        },
        "XO19QrZgSjqurYdGbfMvdA": {
            "hdl": "XO19QrZgSjqurYdGbfMvdA",
            "name": "class name",
            "icon": "ATTR-INFO",
            "hasLookup": true,
            "hasUOM": false,
            "isNormal": true,
            "value": "blower",
            "typedValue": "blower",
            "typeError": {},
            "dataType": "STRING",
            "uom": null,
            "FTS": "blower",
            "change": true,
            "typedChange": true,
            "conflict": [],
            "provenance": []
        },
        "QlTaiX6jQZez38iQi8tcag": {
            "hdl": "QlTaiX6jQZez38iQi8tcag",
            "name": "plant code",
            "icon": "facility",
            "hasLookup": true,
            "hasUOM": false,
            "isNormal": true,
            "value": "TKF",
            "typedValue": "TKF",
            "typeError": {},
            "dataType": "STRING",
            "uom": null,
            "FTS": "TKF",
            "change": true,
            "typedChange": true,
            "conflict": [],
            "provenance": []
        },
        .
        .
        .
    },
    "populated": 4,
    "eiclist": [
        {
            "ID": 1,
            "Name": "Commissioning Demo",
            "Status": "Submitted",
            "ClsHdl": "KYqvG_IhQ0y6IrnRwgbCAg",
            "Class": "Commissioning Integration",
            "Hdl": "XYSp3hn0TDuJV-NX6MrTBQ"
        }
    ],
    "commentcount": 0
}
```

## Response Status Codes
**200** Matching item has been found and successfully returned

**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired

**404** Requested item can't be found. Check that the ID and object type have been provided and are correct.

**500** Internal Server Error