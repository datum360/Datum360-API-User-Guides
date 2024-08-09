# POST /etl_queue/activities/terminate_items

## Description
Submits a terminate activity

## Required Capabilities
* CanUseAPI
* CanTerminateItems
## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **upfile** (required) (form data) The file to upload. This should be a file stream
* **eicHdl** (required) (form data) The handle of the file to load into
* **objectType** (required) (form data) The type of object to upload. Must be one of:
    * TAGGED_ITEM
    * DOCUMENT
    * EQUIPMENT_ITEM
    * EQUIPMENT_MODEL
* **worksheets** (form data) Array of sheet names. If an Excel file is used for loading data then this specifies which workbook sheets to load from.

## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/etl_queue/activities/terminate_items' \
--header 'Authorization: ••••••' \
--form 'upFile=@"postman-cloud:///1ef53a5e-ffba-4390-99c0-9541a8171f33"' \
--form 'eicHdl="XYSp3hn0TDuJV-NX6MrTBQ"' \
--form 'objectType="TAGGED_ITEM"' \
--form 'worksheets="Sheet1"'
```

## Response Body
A JSON object containing the details of the submitted terminate item activity

## Example Response
```JSON
{
    "data": {
        "etlActHdl": "U-cAphhbTPy4rwG_8LX43Q",
        "etlScript": "/etl360/etl-term-items/build/etl-term-items.js",
        "etlJob": {
            "act_name": "Terminate items",
            "act_type": "IMPORT",
            "act_id": "TERMINATE_ITEMS",
            "user_name": "User Name",
            "user_job": "Autodesk",
            "user_handle": "HwiX1yRxSVqzzGpHRg_q5w",
            "auth_address": "https://{{systemName}}.acl360.io/",
            "project_id": "system-name-pim360",
            "object_type": "TAGGED_ITEM",
            "eic_handle": "XYSp3hn0TDuJV-NX6MrTBQ",
            "worksheets": [
                1
            ],
            "inputfile": "sTMLYhGOQPOq9HxPzujf8w",
            "act_handle": "U-cAphhbTPy4rwG_8LX43Q"
        }
    }
}
```

## Response Status Codes
**200** Activity has been successfully submitted
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


