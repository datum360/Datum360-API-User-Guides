# GET /domains/{domHdl}/templates

## Description
Returns a list of all templates

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters

* **domHdl** (required) (path) The handle of the Domain/Class Library to use

* **version** (query string) The version of the Class Library to use. Must be a number, defaults to the latest available version if not provided

## Example Request
```
curl --location 'https://{{systemName}}.cls360.io/api/domains/MAKZvz1eTQSvaQdvlHsYNw/templates' \
--header 'Authorization: ••••••'
```

## Response Body
JSON object with an array `rows`. Where each object in the array is a template from CL4CL

## Example Response
```JSON
{
    "rows": [
        {
            "Hdl": "llholBN7RnWLGz6ioAtWTg",
            "Icon": "ATTR-GRP",
            "Name": "Attribute Group",
            "_cl": "MAKZvz1eTQSvaQdvlHsYNw",
            "_vn": 1,
            "_on": 0
        },
        {
            "Hdl": "BUPAMAaDQ7G2B9NtkeeXYA",
            "Icon": "MAP",
            "Name": "Attribute Mapping",
            "_cl": "MAKZvz1eTQSvaQdvlHsYNw",
            "_vn": 1,
            "_on": 0
        },
        {
            "Hdl": "Chk-537RS4eB6txHdT9ltQ",
            "Icon": "general",
            "Name": "Data Source",
            "_cl": "MAKZvz1eTQSvaQdvlHsYNw",
            "_vn": 1,
            "_on": 0
        },
        .
        .
        .
    ],
    "header": []
}
```

## Response Status Codes
**200** Templates have been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**500** Internal Server Error


