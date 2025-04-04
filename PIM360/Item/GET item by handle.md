# GET /objects/{type}/{handle}

## Description
Gets an item of the specified type with the specified handle.

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters

* **type** (required) (path) Item type to query on. Can be one of:  
  * TAGGED_ITEM
  * DOCUMENT
  * EQUIPMENT_ITEM
  * EQUIPMENT_MODEL
  * EIC

* **handle** (required) (path) The handle of the item to get.

* **eic** (optional) (query) Handle of the EIC to use, otherwise active data.

## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/objects/TAGGED_ITEM/-W4UaC1IS5K5FCmfh5PbSQ?eic=XYSp3hn0TDuJV-NX6MrTBQ' \
--header 'Authorization: ******'
```

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
    "3OqLZQ7tQISsVK0X-0NVYw": {
      "hdl": "3OqLZQ7tQISsVK0X-0NVYw",
      "name": "Asset Status",
      "icon": "ATTR-INFO",
      "hasLookup": true,
      "hasUOM": false,
      "isNormal": true,
      "value": "Installed",
      "typedValue": "Installed",
      "typeError": {},
      "dataType": "STRING",
      "uom": null,
      "FTS": "Installed",
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
| Status Code | Description |
| -------- | ------- |
|**200** |Matching item has been found and successfully returned.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**404** |Requested item can't be found. Check that the handle has been provided and is correct. Check that the provided item type is correct. Make sure that the attribute name has been provided.|
|**500** |Internal Server Error. |


