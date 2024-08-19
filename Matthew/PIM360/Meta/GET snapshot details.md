# GET /snapshotversion

## Description
Retrieves the name of the synced Class Library, the handle of the synced Class Library, the current version of the synced Class Library

## Required Capabilities
* CanUseAPI
* CanManageCls360Snapshot
* CanSeeAdmin

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters

## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/snapshotversion' \
--header 'Authorization: ••••••'
```

## Response Body
JSON object containing details of the currently synced snapshot

## Example Response
```JSON
{
    "name": "CFIHOS v1.5.1",
    "hdl": "MAKZvz1eTQSvaQdvlHsYNw",
    "version": 61
}
```

## Response Status Codes
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


