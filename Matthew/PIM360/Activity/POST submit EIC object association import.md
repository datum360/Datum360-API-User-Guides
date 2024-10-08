# POST /etl_queue/activities/eic_related_obj_assoc

## Description
Submits an EIC related object association import activity.

## Required Capabilities
* CanUseAPI
* CanAssociateItemsToEIC

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **upfile** (required) (form data) The file to upload. This should be a file stream.
* **eicHdl** (required) (form data) The handle of the file to load into.
* **objectType** (required) (form data) The type of object to upload. Must be one of:
    * TAGGED_ITEM
    * DOCUMENT
    * EQUIPMENT_ITEM
    * EQUIPMENT_MODEL


## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/etl_queue/activities/eic_related_obj_assoc' \
--header 'Authorization: ••••••' \
--form 'upFile=@"postman-cloud:///1ef53a5e-ffba-4390-99c0-9541a8171f33"' \
--form 'eicHdl="UBzA9lXTQzmWtC2mketjdA"' \
--form 'objectType="TAGGED_ITEM"'
```

## Response Body
A JSON object containing the details of the submitted EIC object association import activity.

## Example Response
```JSON
{
    "data": {
        "etlActHdl": "LddBnNMjTq6V-pv_i08BTQ",
        "etlScript": "/etl360/etl-eic-ass-import/build/etl-eic-ass-import-v2.js",
        "etlJob": {
            "act_name": "EIC Related Object Association Import",
            "act_type": "IMPORT",
            "act_id": "ASSOCIATE_TO_EIC",
            "user_name": "Test Runner",
            "user_job": "Automated Tester",
            "user_handle": "HwiX1yRxSVqzzGpHRg_q5w",
            "auth_address": "https://{{systemName}}.acl360.io/",
            "project_id": "{{systemName}}-pim360",
            "object_type": "TAGGED_ITEM",
            "eic_handle": "UBzA9lXTQzmWtC2mketjdA",
            "worksheets": 1,
            "pre_script": "preprocess.sh",
            "inputfile": "LO_rEaC-Tr2Bzat6bsZvlA",
            "act_handle": "LddBnNMjTq6V-pv_i08BTQ"
        }
    }
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Activity has been successfully submitted.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**404** |Requested item can't be found. Check that the handle has been provided and is correct.|
|**500** |Internal Server Error.|


