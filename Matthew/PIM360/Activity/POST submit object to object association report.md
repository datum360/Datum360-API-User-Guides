# POST /etl_queue/activities/object_association_report

## Description
Submit an Object to Object Association report

## Required Capabilities
* CanUseAPI
* CanRunObjectAssociationReport
## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters

* **left_type** (required) (form data) the left object type in the report e.g tag in tag-to-doc. Must be one of:
    * TAGGED_ITEM
    * EQUIPMENT_ITEM
    * EQUIPMENT_MODEL
    * DOCUMENT

* **right_type** (required) (form data) the right object type in the report e.g doc in tag-to-doc
    * TAGGED_ITEM
    * EQUIPMENT_ITEM
    * EQUIPMENT_MODEL
    * DOCUMENT
* **eic_handle** (required) (form data) the handle of the EIC to get data from

* **export_mode** (required) (form data) The format of the file that will be genereated. Must be one of:
    * xlsx
    * delimited

* **delimiter** (form data) If the "delimited" format is selected, this is the character to use as the delimiter. Defaults to comma

* **left_join** (form data) Whether to show all "left" object types or not regardless of if they have associations. Must be one of:
    * on
    * off

* **datasetReference** (form data) optional datasetReference to allow the activity to be resubmitted at a later time

## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/etl_queue/activities/object_association_report' \
--header 'Authorization: ••••••' \
--form 'left_type="TAGGED_ITEM"' \
--form 'right_type="DOCUMENT"' \
--form 'eic_handle="XYSp3hn0TDuJV-NX6MrTBQ"' \
--form 'export_mode="xlsx"'
```

## Response Body
A JSON object containing the details of the submitted object to object report activity

## Example Response
```JSON
{
    "response": {
        "act_name": "Object to Object association report",
        "act_type": "REPORT",
        "act_id": "REPORT_OBJ_TO_OBJ",
        "user_name": "User Name",
        "user_job": "Autodesk",
        "user_handle": "HwiX1yRxSVqzzGpHRg_q5w",
        "auth_address": "https://{{systemName}}.acl360.io/",
        "project_id": "system-name-pim360",
        "export_mode": "xlsx",
        "eic_handle": "XYSp3hn0TDuJV-NX6MrTBQ",
        "left_type": "TAGGED_ITEM",
        "right_type": "DOCUMENT",
        "act_handle": "O8bSOWUQR4Ss7WVlhQ1otQ"
    }
}
```

## Response Status Codes
**200** Activity has been successfully submitted
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


