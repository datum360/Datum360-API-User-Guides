# GET /file/{handle}

## Description
Gets the contents of a file by handle provided.

## Required Capabilities
* CanUseAPI
* CanDownloadFiles
## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **handle** (required) (path) The handle of the file.

## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/file/_il0KZTPS0WwUEOxfl59Pw' \
--header 'Authorization: ••••••'
```

## Response Body
A stream of the file requested. Note that the file may be within a zip file.

## Example Response
File stream.

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Matching file has been found and successfully returned.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**404** |Requested file can't be found. Check that the handle has been provided and is correct.|
|**500**|Internal Server Error.|


