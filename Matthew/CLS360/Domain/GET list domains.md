# GET /domains

## Description
Lists all domains/class libraries in CLS360

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters



## Example Request
```
curl --location 'https://{{systemName}}.cls360.io/api/domains' \
--header 'Authorization: ••••••' \
```

## Response Body
JSON array of objects, where each object represents a domain/class library. The object contains information such as the class library name, handle and current version

## Example Response
```JSON
{
    "value": [
        {
            "Hdl": "MAKZvz1eTQSvaQdvlHsYNw",
            "Name": "CFIHOS v1.5.1",
            "Label": "CFIHOS v1.5.1",
            "Company": "Deprecated",
            "Logo": "img/logo.png",
            "Lock": false,
            "Version": 61
        }
    ]
}
```

## Response Status Codes
**200** items have been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**500** Internal Server Error


