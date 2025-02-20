# POST /etl_queue/activities/datatyping_errors_report

## Description
Submits a datatyping errors report activity. 

## Required Capabilities
* CanUseAPI
* CanRunDatatypingErrorsReport

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
* **eic_handle_active** (required) (form data) The handle of the EIC to run the report on or "active" for active data.
* **delimiter** (form data) If the "delimited" format is selected, this is the character to use as the delimiter. Defaults to comma.
* **datasetReference** (form data) Optional datasetReference to allow the activity to be resubmitted at a later time.

## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/etl_queue/activities/datatyping_errors_report' \
--header 'Authorization: ••••••' \
--form 'object_type="TAGGED_ITEM"' \
--form 'export_mode="xlsx"' \
--form 'eic_handle_active="active"'
```

## Response Body
A JSON object containing the details of the submitted datatyping errors report activity.

## Example Response
```JSON
{
    "response": {
        "act_name": "Datatyping errors",
        "act_type": "REPORT",
        "act_id": "REPORT_DATATYPING_ERRORS",
        "user_name": "User Name",
        "user_job": "Autodesk",
        "user_handle": "HwiX1yRxSVqzzGpHRg_q5w",
        "auth_address": "https://{{systemName}}.acl360.io/",
        "project_id": "system-name-pim360",
        "export_mode": "xlsx",
        "eic_handle_active": "active",
        "object_type": "TAGGED_ITEM",
        "act_handle": "m5Z280McRUefJptjct4K5w"
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


