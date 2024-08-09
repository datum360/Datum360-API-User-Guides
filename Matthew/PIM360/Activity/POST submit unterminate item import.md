# POST /etl_queue/activities/unterminate_items

## Description
Submits an unterminate item activity

## Required Capabilities
* CanUseAPI
* CanUnterminateItems
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
curl --location 'https://{{systemName}}.pim360.io/api/etl_queue/activities/unterminate_items' \
--header 'Authorization: ••••••' \
--form 'upFile=@"postman-cloud:///1ef55e5b-8645-46b0-8606-9793314501c7"' \
--form 'eicHdl="XYSp3hn0TDuJV-NX6MrTBQ"' \
--form 'objectType="TAGGED_ITEM"' \
--form 'worksheets="Sheet1"'
```

## Response Body
A JSON object containing the details of the submitted unterminate items activity

## Example Response
```JSON
{
    "data": {
        "etlActHdl": "Ksh5ow7ZQcypPPmc14VYEw",
        "etlScript": "/etl360/etl-unterm-items/build/etl-unterm-items.js",
        "etlJob": {
            "act_name": "Unterminate items",
            "act_type": "IMPORT",
            "act_id": "UNTERMINATE_ITEMS",
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
            "inputfile": "p6TMBuPpSo26rqwAnGrUZg",
            "act_handle": "Ksh5ow7ZQcypPPmc14VYEw"
        }
    }
}
```

## Response Status Codes
**200** Activity has been successfully submitted
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


