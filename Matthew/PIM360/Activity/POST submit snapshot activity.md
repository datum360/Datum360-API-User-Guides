# POST /etl_queue/activities/snapshot

## Description
Submits a snapshot activity to a specified version.

## Required Capabilities
* CanUseAPI
* CanManageCls360Snapshot

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **parameters** (required) (body) JSON object describing the snapshot activity to submit. The object has 3 properties: `version`, `comment`, `cl_name`. `version` specifies which version of the class library to snapshot to. `comment` specifies the comment to put against the snapshot. `cl_name` specifies the name of the class library. If any or all data is missing then a snapshot will be run against the current version of the snapshot, i.e it will not be increased to the latest available version.

## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/etl_queue/activities/snapshot' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
    "version": 58,
    "comment": "API Snapshot",
    "cl_name": "CFIHOS v1.5.1"
}'
```

## Response Body
A JSON object containing the details of the submitted snapshot activity.

## Example Response
```JSON
{
    "data": {
        "etlActHdl": "fBM1QyPzTeWIis28k091vg",
        "etlScript": "/etl360/etl-snapshot-import-mongodb/build/etl-snapshot-import-mongodb.js",
        "etlJob": {
            "act_name": "Class Library snapshot update from version 58 to 59",
            "act_type": "IMPORT",
            "act_id": "IMPORT_SNAPSHOT",
            "user_name": "User Name",
            "user_job": "Autodesk",
            "user_handle": "HwiX1yRxSVqzzGpHRg_q5w",
            "auth_address": "https://{{systemName}}.acl360.io/",
            "project_id": "system-name-pim360",
            "version": "59",
            "comment_text": "API Snapshot",
            "domain": "CFIHOS v1.5.1",
            "caches_only_snapshot": "false",
            "act_handle": "fBM1QyPzTeWIis28k091vg"
        }
    }
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Activity has been successfully submitted.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**500** |Internal Server Error.|


