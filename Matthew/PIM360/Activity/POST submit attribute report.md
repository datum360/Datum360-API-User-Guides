# POST /etl_queue/activities/attribute_report

## Description
Submits a Attribute report activity    

## Required Capabilities
* CanUseAPI
* CanRunObjectAttributeReport
## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **object_type** (required) (form data) The type of object to generate the report on. Must be one of:
    * TAGGED_ITEM
    * DOCUMENT
    * EQUIPMENT_ITEM
    * EQUIPMENT_MODEL
* **eic_handle** (form data) The handle of the EIC to run the report on. If not provided then active data will be used
* **delimiter** (form data) If the "delimited" format is selected, this is the character to use as the delimiter. Defaults to comma
* **dataset_reference** (form data) optional datasetReference to allow the activity to be resubmitted at a later time
* **output_name** (form data) The name of the file to generate. Will automatically append the correct file extension. Defaults to {item type}-export

## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/etl_queue/activities/attribute_report' \
--header 'Authorization: ••••••' \
--form 'object_type="TAGGED_ITEM"'
```

## Response Body
A JSON object containing the details of the submitted Attribute report activity

## Example Response
```JSON
{
    "response": {
        "act_name": "Attribute Report",
        "act_type": "REPORT",
        "act_id": "ATTRIBUTE_REPORT",
        "user_name": "User Name",
        "user_job": "Autodesk",
        "user_handle": "HwiX1yRxSVqzzGpHRg_q5w",
        "auth_address": "https://{{systemName}}.acl360.io/",
        "project_id": "system-name-pim360",
        "export_mode": "long",
        "eic_handle": null,
        "object_type": "TAGGED_ITEM",
        "act_handle": "z8_c7-QfTl22mgi7_xyFVA"
    }
}
```

## Response Status Codes
**200** Activity has been successfully submitted
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


