# POST /etl_queue/activities/eic_impact_report

## Description
Submits an EIC impact report activity.

## Required Capabilities
* CanUseAPI
* CanRunEICImpactReport

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **export_mode** (required) (form data) The format of the file that will be generated. Must be one of:
    * xlsx
    * delimited
* **eic_handle** (required) (form data) The handle of the EIC to run the report on.
* **delimiter** (form data) If the "delimited" format is selected, this is the character to use as the delimiter. Defaults to comma.
* **datasetReference** (form data) Optional datasetReference to allow the activity to be resubmitted at a later time.

## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/etl_queue/activities/eic_impact_report' \
--header 'Authorization: ••••••' \
--form 'export_mode="xlsx"' \
--form 'eic_handle="XYSp3hn0TDuJV-NX6MrTBQ"'
```

## Response Body
A JSON object containing the details of the submitted EIC impact report activity.

## Example Response
```JSON
{
    "response": {
        "act_name": "EIC impact report",
        "act_type": "REPORT",
        "act_id": "REPORT_EIC_IMPACT",
        "user_name": "User Name",
        "user_job": "Autodesk",
        "user_handle": "HwiX1yRxSVqzzGpHRg_q5w",
        "auth_address": "https://{{systemName}}.acl360.io/",
        "project_id": "system-name-pim360",
        "export_mode": "xlsx",
        "eic_handle": "XYSp3hn0TDuJV-NX6MrTBQ",
        "act_handle": "xhZ2G0vlQHCY3LRYl94lKQ"
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


