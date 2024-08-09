# POST /etl_queue/activities/register_import

## Description
Submit a register import activity

## Required Capabilities
* CanUseAPI
* CanImportRegister

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **upfile** (required) (form data) The file to upload. This should be a file stream
* **eicHdl** (required) (form data) The handle of the EIC to upload into.
* **etlSourceHdl** (required) (form data) The handle of the ETL source to use to load. This value can be retrieved from CLS360
* **objectType** (required) (form data) The type of object to upload. Must be one of:
    * TAGGED_ITEM
    * DOCUMENT
    * EQUIPMENT_ITEM
    * EQUIPMENT_MODEL
* **deliverableHdl** (form data) The handle of the deliverable to upload against. This value can be retrieved by using the API `GET /eic/{eicHdl}/deliverables`
* **worksheets** (form data) Array of sheet names. If an Excel file is used for loading data then this specifies which workbook sheets to load from.

## Example Request
curl --location 'https://dap-demo.pim360.io/api/etl_queue/activities/register_import' \
--header 'Authorization: ••••••' \
--form 'upfile=@"postman-cloud:///1ef53a5e-ffba-4390-99c0-9541a8171f33"' \
--form 'eicHdl="XYSp3hn0TDuJV-NX6MrTBQ"' \
--form 'etlSourceHdl="ECDTZbe6RyaFSKwzBgtFHQ"' \
--form 'objectType="TAGGED_ITEM"' \
--form 'worksheets="Sheet1"'

## Response Body
A JSON object containing the details of the submitted regster import activity

## Example Response
```JSON
{
    "data": {
        "etlActHdl": "MNsVaXy3RCS3NKXs3Oh5Mg",
        "etlScript": "/etl360/etl-tag-import-incremental-rebuild/build/etl-tag-import-incremental-rebuild.js",
        "etlJob": {
            "act_name": "Register Import",
            "act_type": "IMPORT",
            "act_id": "IMPORT_REGISTER",
            "user_name": "User Name",
            "user_job": "Autodesk",
            "user_handle": "HwiX1yRxSVqzzGpHRg_q5w",
            "auth_address": "https://{{systemName}}.acl360.io/",
            "project_id": "system-name-pim360",
            "object_type": "TAGGED_ITEM",
            "source_handle": "ECDTZbe6RyaFSKwzBgtFHQ",
            "eic_handle": "XYSp3hn0TDuJV-NX6MrTBQ",
            "deliverable": "--ignore--",
            "worksheets": [
                1
            ],
            "default_class": "null",
            "allow_new": "true",
            "pre_script": "preprocess-wide.sh",
            "classification": "cls",
            "terminate_missing": "false",
            "terminate_missing_attributes": "false",
            "uom_label": "UOM",
            "inputfile": "CL3zSCWORoWupwrhf3ijAw",
            "act_handle": "MNsVaXy3RCS3NKXs3Oh5Mg"
        }
    }
}
```

## Response Status Codes
**200** Activity has been successfully submitted
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


