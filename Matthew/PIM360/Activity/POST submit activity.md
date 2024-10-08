# POST /etl_queue/activities/{handle}

## Description
Submits a previously submitted activity but with modified parameters.

Because this API allows any activity to be submitted it is required that the authenticated user can run all activity types. It is recommended instead to use the specific activity API endpoints that have more fine grained restrictions.

## Required Capabilities
* CanUseAPI
* CanExportObject
* CanExportPivot
* CanGenerateDCF
* CanImportAssociation
* CanImportNarrow
* CanImportRegister
* CanImportSnapshot
* CanImportWide
* CanPublishEIC
* CanRemoveItemsFromEIC
* CanRunAttrGapReport
* CanRunEICImpactReport
* CanRunObjectAssociationReport
* CanRunParentTagInconsistencyReport
* CanRunSourceConflictReport

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **handle** (required) (path) The handle of the activity to base this activity on.
* **parameters** (body) JSON object containing the parameters of the activity to run.

## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/etl_queue/activities/tEN1yvVGSLWm3a1Ksm2CZw' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
    "hdl": "rgl56OgORK6mgOxh7WfBZw",
    "params": {
        "eic_handle": "UBzA9lXTQzmWtC2mketjdA",
        "inputfile": "2rrFj3OMQHm-u-fLLpekzA",
        "object_type": "TAGGED_ITEM",
        "deliverable": "--ignore--",
        "source_handle": "ECDTZbe6RyaFSKwzBgtFHQ",
        "classification": "cls",
        "terminate_attributes": "empty"
    }
}'
```

## Response Body
A JSON object containing the status and parameters of the specified activity. `status` can be one of:
* PENDING
* COMPLETE
* ERROR

Activity parameters can be found in the `params` property.

## Example Response
``` JSON 
{
    "hdl": "GWOUsjhaReSq0NUvX_Zsfg",
    "status": "PENDING",
    "params": {
        "eic_handle": "UBzA9lXTQzmWtC2mketjdA",
        "inputfile": "2rrFj3OMQHm-u-fLLpekzA",
        "object_type": "TAGGED_ITEM",
        "deliverable": "--ignore--",
        "source_handle": "ECDTZbe6RyaFSKwzBgtFHQ",
        "classification": "cls",
        "terminate_attributes": "empty"
    }
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Activity has been successfully submitted.|
|**401**| Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**404**| Requested item can't be found. Check that the handle has been provided and is correct.|
|**500** |Internal Server Error.|


