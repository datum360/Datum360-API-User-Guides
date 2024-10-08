# POST /etl_queue/activities/source_conflict_report

## Description
Submits a source conflict report activity.

## Required Capabilities
* CanUseAPI
* CanRunSourceConflictReport
## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **object_type** (required) (form data) The type of object to generate the report on. Must be one of:
    * TAGGED_ITEM
    * DOCUMENT
    * EQUIPMENT_ITEM
    * EQUIPMENT_MODEL
* **export_mode** (required) (form data) The format of the file that will be generated. Must be one of:
    * xlsx
    * delimited
* **eic_handle** (required) (form data) The handle of the EIC to use.
* **delimiter** (form data) If the "delimited" format is selected, this is the character to use as the delimiter. Defaults to comma.
* **datasetReference** (form data) Optional datasetReference to allow the activity to be resubmitted at a later time.

## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/etl_queue/activities/source_conflict_report' \
--header 'Authorization: ••••••' \
--form 'object_type="TAGGED_ITEM"' \
--form 'export_mode="xlsx"' \
--form 'eic_handle="XYSp3hn0TDuJV-NX6MrTBQ"'
```

## Response Body
A JSON object containing the details of the submitted source conflict report activity.

## Example Response
```JSON
{
    "response": {
        "act_name": "Source conflict report",
        "act_type": "REPORT",
        "act_id": "REPORT_SOURCE_CONFLICTS",
        "user_name": "Test Runner",
        "user_job": "Automated Tester",
        "user_handle": "HwiX1yRxSVqzzGpHRg_q5w",
        "auth_address": "https://{{systemName}}.acl360.io/",
        "project_id": "system-name-pim360",
        "object_type": "TAGGED_ITEM",
        "export_mode": "xlsx",
        "eic_handle": "XYSp3hn0TDuJV-NX6MrTBQ",
        "act_handle": "BhG8DKFgSkyiUv3scTnUcA"
    }
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200**| Activity has been successfully submitted.|
|**400** |Bad request, make sure the object type, export mode and eic handles are provided.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**404** |Requested item can't be found. Check that the handle has been provided and is correct.|
|**500** |Internal Server Error.|


