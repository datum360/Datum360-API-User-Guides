# GET /etl_queue/activities/{handle}

## Description
Gets the status and parameters of the specified activity

## Required Capabilities
* CanUseAPI
* CanSeeQueue

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **handle** (required) (path) Handle of the activity to get


## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/etl_queue/activities/_husD3RvT12QMTE7bYe10g' \
--header 'Authorization: ••••••'
```
## Response Body
A JSON object containing the status and parameters of the specified activity. `status` can be one of:
* PENDING
* COMPLETE
* ERROR

Activity parameters can be found in the `params` property

## Example Response
``` JSON
{
    "hdl": "6DMD3g2FRbGgatxNWJZYvw",
    "status": "COMPLETE",
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
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


