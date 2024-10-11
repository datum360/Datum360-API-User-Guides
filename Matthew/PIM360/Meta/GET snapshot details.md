# GET /snapshotversion

## Description
Retrieves the name and handle of the current class library and the current version of the class library.

## Required Capabilities
* CanUseAPI
* CanManageCls360Snapshot
* CanSeeAdmin

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
No parameters

## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/snapshotversion' \
--header 'Authorization: ••••••'
```

## Response Body
JSON object containing details of current class library.

## Example Response
```JSON
{
    "name": "CFIHOS v1.5.1",
    "hdl": "MAKZvz1eTQSvaQdvlHsYNw",
    "version": 61
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Matching item has been found and successfully returned.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**404** |Requested item can't be found. Check that the handle has been provided and is correct.|
|**500** |Internal Server Error.|


