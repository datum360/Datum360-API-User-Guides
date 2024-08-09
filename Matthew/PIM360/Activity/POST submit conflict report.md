# POST /etl_queue/activities/conflict_report

## Description
Submits a conflict report activity

## Required Capabilities
* CanUseAPI
* CanRunConflictReport
## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **objectType** (required) (form data) The type of object to generate the report on. Must be one of:
    * TAGGED_ITEM
    * DOCUMENT
    * EQUIPMENT_ITEM
    * EQUIPMENT_MODEL
* **outputFormat** (required) (form data) The format of the file that will be genereated. Must be one of:
    * xlsx
    * delimited
* **eicHdls** (required) (form data) comma delimited list of EIC handles to use
* **fromDate** (required) (form data) start date of the report timeframe. Date must be in the format YYYY-MM-DD
* **delimiter** (form data) If the "delimited" format is selected, this is the character to use as the delimiter. Defaults to comma
* **toDate** (form data) end date of the report timeframe. Defaults to the current date. Date must be in the format YYYY-MM-DD
* **datasetReference** (form data) optional datasetReference to allow the activity to be resubmitted at a later time

## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/etl_queue/activities/conflict_report' \
--header 'Authorization: ••••••' \
--form 'objectType="TAGGED_ITEM"' \
--form 'outputFormat="delimited"' \
--form 'eicHdls="XYSp3hn0TDuJV-NX6MrTBQ, tJsy-BtWQbe2SoaTeNVAcQ"' \
--form 'fromDate="2024-01-01+10:40"' \
--form 'eicHdls="tJsy-BtWQbe2SoaTeNVAcQ"' \
--form 'toDate="2024-12-31+10:40"'
```

## Response Body
A JSON object containing the details of the submitted conflict report activity

## Example Response
```JSON
{
    "response": {
        "act_name": "Change log report",
        "act_type": "REPORT",
        "act_id": "REPORT_CHANGE_LOG",
        "object_type": "TAGGED_ITEM",
        "export_mode": "delimited",
        "delimiter": null,
        "eic_handles": "tJsy-BtWQbe2SoaTeNVAcQ",
        "from_date": "2024-01-01+10:40",
        "user_name": "User Name",
        "user_job": "Autodesk",
        "user_handle": "HwiX1yRxSVqzzGpHRg_q5w",
        "to_date": "2024-12-31+10:40",
        "act_handle": "BgpG_MMxQmehjCbdwMXb3A"
    }
}
```

## Response Status Codes
**200** Activity has been successfully submitted
**400** Bad request, make sure that at least object type, output format, eic handles and from date are provided
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


