# POST /etl_queue/activities/parent_tag_inconsistency_report.md

## Description
Submit a Parent Tag Inconsistency Report activity

## Required Capabilities
* CanUseAPI
* CanRunParentTagInconsistencyReport
## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **export_mode** (required) (form data) The format of the file that will be genereated. Must be one of:
    * xlsx
    * delimited
* **delimiter** (form data) If the "delimited" format is selected, this is the character to use as the delimiter. Defaults to comma
* **datasetReference** (form data) optional datasetReference to allow the activity to be resubmitted at a later time

## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/etl_queue/activities/parent_tag_inconsistency_report' \
--header 'Authorization: ••••••' \
--form 'export_mode="xlsx"'
```

## Response Body
A JSON object containing the details of the submitted Parent Tag Inconsistency Report activity

## Example Response
```JSON
{
    "response": {
        "act_name": "Parent Tag inconsistency report",
        "act_type": "REPORT",
        "act_id": "REPORT_PARENT_TAG_INCONSISTENCY",
        "user_name": "User Name",
        "user_job": "Autodesk",
        "user_handle": "HwiX1yRxSVqzzGpHRg_q5w",
        "auth_address": "https://{{systemName}}.acl360.io/",
        "project_id": "system-name-pim360",
        "export_mode": "delimited",
        "act_handle": "0xGeKrwATiewE3tx1uaIqA"
    }
}
```

## Response Status Codes
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


