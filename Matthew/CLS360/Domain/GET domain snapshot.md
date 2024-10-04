# GFT /domains/{{domHdl}}/snapshot

## Description
Gets the full class library snapshot, used by PIM360 at a specified version

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **domHdl** (required) (path) Handle of the class library/domain to get

* **version** (required) (query) The version of the class library to get the snapshot for. Must be greater than 0 and less than or equal to the current version. If a number greater than the current version is provided, then the current version will be returned. Not providing a version at all will return no class library data.

* **fromVersion** (query) optionally filter out snapshot data to only include information after a provided version


## Example Request
```
curl --location 'https://{{systemName}}.cls360.io/api/domains/MAKZvz1eTQSvaQdvlHsYNw/snapshot?version=61' \
--header 'Authorization: ••••••'
```

## Response Body
JSON object containing a full copy of the CLS360 snapshot. Anything that can be found in the "Object Browser" section of the UI is returned in the "classes" array. Anything that can be found in the "CL4CL" section of the UI is returned in the "CL4CL" array

## Example Response
```JSON
{
    "domain": {
        "Hdl": "MAKZvz1eTQSvaQdvlHsYNw",
        "Name": "CFIHOS v1.5.1",
        "Label": "CFIHOS v1.5.1",
        "Company": "Deprecated",
        "Logo": "img/logo.png",
        "Lock": false,
        "Version": "61"
    },
    "schema": {
        "_id": "616eddc41de47d290f146be5",
        "Version": 13,
        "API": "clsio-api"
    },
    "classes": [
        ... All class, attribute, etl etc. details
    ],
    "CL4CL": [
        ... All CL4CL data
    ]
}
```

## Response Status Codes
**200** Snapshot version has been successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


