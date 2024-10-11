# GET /tags/{facId}/{tagId}/files

## Description
Given a tag ID and facility, find all files that contain the provided tag.

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **facId** (required) (path) The name of the facility that the tag belongs to

* **tagId** (required) (path) The name of the tag to get files for

* **results** (query) Optionally get a summary of results by providing "summary" or full details by providing "full"


## Example Request
```
curl --location 'https://{{systemName}}.ddm360.io/api/tags/TKF/TK-1003/files' \
--header 'Authorization: ••••••'
```

## Response Body
Array of objects, where each object contains the handle of file containing the specified tag

## Example Response
```JSON
[
    {
        "fileHdl": "EwmPrdfJQuu3SgEA_Qju-Q"
    }
]
```

## Response Status Codes
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


