# POST /etl_queue/activities/association_import

## Description
Submits an association import activity.

## Required Capabilities
* CanUseAPI
* CanImportAssociation
## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **upfile** (required) (form data) The file to upload. This should be a file stream.
* **eicHdl** (required) (form data) The handle of the EIC to import into.
* **fromType** (required) (form data) The source item type. Must be one of:
    * TAGGED_ITEM
    * DOCUMENT
    * EQUIPMENT_ITEM
    * EQUIPMENT_MODEL
* **toType** (required) (form data) The target item type. Must be one of:
    * TAGGED_ITEM
    * DOCUMENT
    * EQUIPMENT_ITEM
    * EQUIPMENT_MODEL
* **worksheets** (form data) Array of sheet names. If an Excel file is used for loading data then this specifies which workbook sheets to load from.

## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/etl_queue/activities/association_import' \
--header 'Authorization: ••••••' \
--form 'upFile=@"postman-cloud:///1ef546c1-abf2-43b0-80b9-f4fab02b61e3"' \
--form 'eicHdl="XYSp3hn0TDuJV-NX6MrTBQ"' \
--form 'fromType="TAGGED_ITEM"' \
--form 'toType="DOCUMENT"'
```

## Response Body
A JSON object containing the details of the submitted narrow import activity.

## Example Response
```JSON
{
    "data": {
        "etlActHdl": "qb6bAEyvQbKRic7qbehdwg",
        "etlScript": "/etl360/etl-ass-import/build/etl-ass-import.js",
        "etlJob": {
            "act_name": "Associations Import",
            "act_type": "IMPORT",
            "act_id": "IMPORT_ASSOCIATION",
            "user_name": "User Name",
            "user_job": "Autodesk",
            "user_handle": "HwiX1yRxSVqzzGpHRg_q5w",
            "auth_address": "https://{{systemName}}.acl360.io/",
            "project_id": "system-name-pim360",
            "eic_handle": "XYSp3hn0TDuJV-NX6MrTBQ",
            "from_type": "TAGGED_ITEM",
            "to_type": "DOCUMENT",
            "terminate_missing": "false",
            "worksheets": 1,
            "pre_script": "preprocess.sh",
            "inputfile": "iiQdfAPQTxa80FGCn3rIVQ",
            "act_handle": "qb6bAEyvQbKRic7qbehdwg"
        }
    }
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Activity has been successfully submitted.|
|**401**| Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**404**| Requested item can't be found. Check that the handle has been provided and is correct.|
|**500**| Internal Server Error.|


