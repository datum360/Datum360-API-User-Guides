# POST /etl_queue/activities/narrow_import

## Description
Submit a narrow import activity

## Required Capabilities
* CanUseAPI
* CanImportNarrow

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **upfile** (required) (form data) The file to upload. This should be a file stream
* **eicHdl** (required) (form data) The handle of the file to load into
* **etlSourceHdl** (required) (form data) The handle of the ETL source to use to load. This value can be retrieved from CLS360
* **objectType** (required) (form data) The type of object to upload. Must be one of:
    * TAGGED_ITEM
    * DOCUMENT
    * EQUIPMENT_ITEM
    * EQUIPMENT_MODEL
* **deliverableHdl** (form data) The handle of the deliverable to upload against. This value can be retrieved by using the API `GET /eic/{eicHdl}/deliverables`
* **terminateAttributes** (form data) Whether to terminate attribute data or not, if so then which ones. Must be one of:
    * ignore - Don't terminate any attriubute data. This is the default
    * empty - Terminate attribute data where the attribute is present in the load file, but has no value provided. This is useful for removing existing attribute data
    * missing - Terminate attribute data where the attribute is not present in the load file
* **ensData** (form data) The name of the ENS (Engineering numbering specification) to use
* **terminateMissing** (form data) boolean value, whether tags missing from the load file should be terminated or not. Defaults to `false`
* **loadUnknownAttributes** (form data) boolean value, whether attributes that are present in the load file but not present in CLS360 should be imported. Defaults to `true`
* **classification** (form data) What method to use for classifying tags. Must be one of:
    * cls - Use the class name specified in the laod file. This is the default value
    * ens - Use the specified ENS to attempt to classify the tags
* **worksheets** (form data) Array of sheet names. If an Excel file is used for loading data then this specifies which workbook sheets to load from.


## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/etl_queue/activities/narrow_import' \
--header 'Authorization: ••••••' \
--form 'upfile=@"postman-cloud:///1ef53a5e-ffba-4390-99c0-9541a8171f33"' \
--form 'eicHdl="XYSp3hn0TDuJV-NX6MrTBQ"' \
--form 'etlSourceHdl="ECDTZbe6RyaFSKwzBgtFHQ"' \
--form 'objectType="TAGGED_ITEM"' \
--form 'worksheets="Sheet1"'
```

## Response Body
A JSON object containing the details of the submitted narrow import activity

## Example Response
```JSON
{
    "data": {
        "etlActHdl": "nHU_EJZ-RDCp5s6bRHvD1g",
        "etlScript": "/etl360/etl-tag-import-incremental-rebuild/build/etl-tag-import-incremental-rebuild.js",
        "etlJob": {
            "act_name": "Object Import - Narrow Format",
            "act_type": "IMPORT",
            "act_id": "IMPORT_OBJECT_NARROW",
            "user_name": "User Name",
            "user_job": "Autodesk",
            "user_handle": "HwiX1yRxSVqzzGpHRg_q5w",
            "auth_address": "https://{{systemName}}.acl360.io/",
            "project_id": "system-name-pim360",
            "object_type": "TAGGED_ITEM",
            "source_handle": "ECDTZbe6RyaFSKwzBgtFHQ",
            "eic_handle": "XYSp3hn0TDuJV-NX6MrTBQ",
            "deliverable": "--ignore--",
            "classification": "cls",
            "ens_name": "",
            "terminate_attributes": "empty",
            "load_unknown_attributes": "true",
            "worksheets": [
                1
            ],
            "default_class": "Unclassified",
            "allow_new": "true",
            "pre_script": "preprocess-narrow.sh",
            "inputfile": "Serv0VNMSVy8L8RstnhzRg",
            "act_handle": "nHU_EJZ-RDCp5s6bRHvD1g"
        }
    }
}
```

## Response Status Codes
**200** Activity has been successfully submitted
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


