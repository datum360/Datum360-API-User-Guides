# GET /files/{fileHdl}

## Description
Download a file by handle

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **fileHdl** (required) (path) The handle of the file.

## Example Request
```
curl --location 'https://{{systemName}}.cls360.io/api/files/XcCdxuQBTeme6RESpy20Ag' \
--header 'Authorization: ••••••'
```

## Response Body
The binary data of the file requested

## Example Response
File Object

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Matching item has been found and successfully returned.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**404** |Requested item can't be found. Check that the handle has been provided and is correct.|
|**500** |Internal Server Error.|

