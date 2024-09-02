# GET /files/dataset/{datasetReference}

## Description
If a file has been submitted to an activity using a dataset reference, the contents of that file can be retrieved using the same dataset reference

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **datasetReference** (required) (path) The dataset reference to use


## Example Request
```
curl --location 'https://{{systemName}}.cls360.io/api/files/dataset/FunctionalExport' \
--header 'Authorization: ••••••'
```

## Response Body
The binary data of the file requested

## Example Response


## Response Status Codes
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


