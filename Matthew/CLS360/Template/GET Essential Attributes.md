# GET /domains/{domHdl}/templates/type/{type}/EssentialAttributes

## Description
Returns the essential attributes that are required for creating an object of the specified type.

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters

* **domHdl** (required) (path) The handle of the Class Library/Domain to use.

* **type** (required) (path) The type of item, must be one of:
    * TAGGED_ITEM
    * EQUIPMENT_ITEM
    * EQUIPMENT_MODEL
    * DOCUMENT

* **version** (query) The version of the Class Library/Domain to use. Must be a number, defaults to the latest available version if not provided.

## Example Request
```
curl --location 'https://{{systemName}}.cls360.io/api/domains/MAKZvz1eTQSvaQdvlHsYNw/templates/type/TAGGED_ITEM/EssentialAttributes?version=14' \
--header 'Authorization: ••••••'
```

## Response Body
JSON object with an array `value`. Each object in the array represents an attribute, containing the attribute type from CL4CL and the handle of the attribute value in the class library being used for that entry.

## Example Response
```JSON
{
    "value": [
        {
            "Key": "ID",
            "Hdl": "y6b-Bxk1S1KbPG-WEjwsBQ"
        },
        {
            "Key": "CLASS",
            "Hdl": "XO19QrZgSjqurYdGbfMvdA"
        },
        {
            "Key": "FACILITY",
            "Hdl": "QlTaiX6jQZez38iQi8tcag"
        }
    ]
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Matching item has been found and successfully returned.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**404** |Requested item can't be found. Check that the item type is correct.|
|**500** |Internal Server Error.|


