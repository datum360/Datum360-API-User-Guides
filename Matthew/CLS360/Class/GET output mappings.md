# GET /domains/{domHdl}/classes/{classHdl}/OutputMappings

## Description
For a given ETL Data Target class, specified by classHdl, get all of the output mappings for that Data Target.

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **domHdl** (required) (path) The handle of the Domain/Class Library to get the class from

* **classHdl** (required) (path) The handle of the class to get. This must be a class of type "Data Target", if any other handle is used then a 404 error will be returned.

* **version** (query) Which version of the Class Library to get the Class from. The latest version will be used by default.


## Example Request
```
curl --location 'https://{{systemName}}.cls360.io/api/domains/MAKZvz1eTQSvaQdvlHsYNw/classes/4p8gbt4NQd-JHvITyMG0sA/OutputMappings' \
--header 'Authorization: ••••••'
```

## Response Body
JSON object with an array property "rows" where each entry in the array is an ETL Output Mapping. The key properties within each mapping are `Mapped From Attribute` which describes which attribute in CLS360 this is being mapped from, and `Name` which describes the value that the attribute name will be mapped to.

## Example Response
``` JSON
{
    "rows": [
        {
            "Hdl": "0hVnwuYNRcmU-95LjL2Dmw",
            "Icon": "MAP",
            "Name": "Asset ID",
            "_cl": "MAKZvz1eTQSvaQdvlHsYNw",
            "_vn": 18,
            "_on": 16,
            "Mapped From Attribute": "Asset ID",
            "Status": "PROPOSED"
        },
        {
            "Hdl": "awDYZYoLQcqw732lupMZVQ",
            "Icon": "MAP",
            "Name": "Class Name",
            "_cl": "MAKZvz1eTQSvaQdvlHsYNw",
            "_vn": 18,
            "_on": 16,
            "Mapped From Attribute": "class name",
            "Status": "PROPOSED"
        },
        {
            "Hdl": "g84ADPMjQzOi3twh6tlzpA",
            "Icon": "MAP",
            "Name": "Status",
            "_cl": "MAKZvz1eTQSvaQdvlHsYNw",
            "_vn": 18,
            "_on": 16,
            "Mapped From Attribute": "Asset Status",
            "Status": "PROPOSED"
        },
        {
            "Hdl": "DDqnR2g3Sh2-RK3jyJLnLA",
            "Icon": "MAP",
            "Name": "clientAssetId",
            "_cl": "MAKZvz1eTQSvaQdvlHsYNw",
            "_vn": 18,
            "_on": 16,
            "Mapped From Attribute": "tag name",
            "Status": "PROPOSED"
        },
        {
            "Hdl": "HnA0JodmRYOIBXbPI5UgsA",
            "Icon": "MAP",
            "Name": "plant code",
            "_cl": "MAKZvz1eTQSvaQdvlHsYNw",
            "_vn": 31,
            "_on": 16,
            "Mapped From Attribute": "plant code",
            "Status": "PROPOSED"
        }
    ],
    "header": [
        "Mapped From Attribute",
        "Ignore",
        "Status"
    ]
}
```

## Response Status Codes
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


