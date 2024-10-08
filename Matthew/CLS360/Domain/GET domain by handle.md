# GET /domains/{domHdl}

## Description
Gets the class library/domain with the handle specified

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **domHdl** (required) (path) The handle of the class library to get

## Example Request
```
curl --location 'https://{{systemName}}.cls360.io/api/domains/MAKZvz1eTQSvaQdvlHsYNw' \
--header 'Authorization: ••••••'
```

## Response Body
JSON object containing the details of the requested class library

## Example Response
```JSON
{
    "Hdl": "MAKZvz1eTQSvaQdvlHsYNw",
    "Name": "CFIHOS v1.5.1",
    "Label": "CFIHOS v1.5.1",
    "Company": "Deprecated",
    "Logo": "img/logo.png",
    "Lock": false,
    "Version": 61
}
```

## Response Status Codes
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


