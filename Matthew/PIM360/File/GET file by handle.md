# GET /file/{handle}

## Description
Get the contents of a file specified by the handle provided

## Required Capabilities
* CanUseAPI
* CanDownloadFiles
## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **handle** (required) (path) The handle of the file to download

## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/file/_il0KZTPS0WwUEOxfl59Pw' \
--header 'Authorization: ••••••'
```

## Response Body
A stream representing the file that has been requested. Note that the file may be within a zip file

## Example Response


## Response Status Codes
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


