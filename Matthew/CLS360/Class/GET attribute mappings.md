# GET /domains/{domHdl}/classes/{classHdl}/AttributeMappings

## Description
For a given ETL Data Source class, specified by classHdl, get all of the output mappings for that Data Source. This is useful for creating knowing which headers to use in a load file when loading data into PIM360 using the specified ETL Source.

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **domHdl** (required) (path) The handle of the Domain/Class Library to get the class from

* **classHdl** (required) (path) The handle of the class to get. This must be a class of type "Data Source", if any other handle is used then a 404 error will be returned.

* **version** (query string) Which version of the Class Library to get the Class from. The latest version will be used by default.


## Example Request
```
curl --location 'https://{{systemName}}.cls360.io/api/domains/MAKZvz1eTQSvaQdvlHsYNw/classes/yqvnK8LoRwuYGuc87WuaBg/AttributeMappings' \
--header 'Authorization: ••••••'
```

## Response Body
JSON object with an array property "rows" where each entry in the array is an ETL Source Mapping. The key properties within each mapping are `Mapped To Attribute` which describes which attribute in CLS360 this is being mapped to, and `Name` which describes the value that the attribute name will be mapped from.

## Example Response
```JSON
{
    "rows": [
        {
            "Hdl": "lPJYTYqqSzm40P-TFCLRmA",
            "Icon": "MAP",
            "Name": "Asset ID",
            "_cl": "MAKZvz1eTQSvaQdvlHsYNw",
            "_vn": 14,
            "_on": 13,
            "Mapped To Attribute": "Asset ID",
            "Ignore": "",
            "Status": "PROPOSED"
        },
        {
            "Hdl": "sPVJwJCgRIK_nhwzbk5y7A",
            "Icon": "MAP",
            "Name": "Class Name",
            "_cl": "MAKZvz1eTQSvaQdvlHsYNw",
            "_vn": 14,
            "_on": 13,
            "Mapped To Attribute": "class name",
            "Ignore": "",
            "Status": "PROPOSED"
        },
        {
            "Hdl": "7yEuy7RSRJGiwE_P6TDb-Q",
            "Icon": "MAP",
            "Name": "Form ID",
            "_cl": "MAKZvz1eTQSvaQdvlHsYNw",
            "_vn": 14,
            "_on": 13,
            "Mapped To Attribute": "Form ID",
            "Ignore": "",
            "Status": "PROPOSED"
        },
        {
            "Hdl": "KpgE2Hr1RiuiensE1Zh-yg",
            "Icon": "MAP",
            "Name": "Form Location",
            "_cl": "MAKZvz1eTQSvaQdvlHsYNw",
            "_vn": 14,
            "_on": 13,
            "Mapped To Attribute": "Form Location",
            "Ignore": "",
            "Status": "PROPOSED"
        },
        {
            "Hdl": "dpzUzU-ITGCJ8KFbX04QGA",
            "Icon": "MAP",
            "Name": "Form Status",
            "_cl": "MAKZvz1eTQSvaQdvlHsYNw",
            "_vn": 14,
            "_on": 13,
            "Mapped To Attribute": "Form Status",
            "Ignore": "",
            "Status": "PROPOSED"
        },
        {
            "Hdl": "6WtUb6c3S3Gq-Zp0i08ljA",
            "Icon": "MAP",
            "Name": "Form Steps Completed",
            "_cl": "MAKZvz1eTQSvaQdvlHsYNw",
            "_vn": 14,
            "_on": 13,
            "Mapped To Attribute": "Form Steps Completed",
            "Ignore": "",
            "Status": "PROPOSED"
        },
        {
            "Hdl": "g1uEwFPIQRaffa9LdD8yRA",
            "Icon": "MAP",
            "Name": "Form Steps Completeness",
            "_cl": "MAKZvz1eTQSvaQdvlHsYNw",
            "_vn": 14,
            "_on": 13,
            "Mapped To Attribute": "Form Steps Completeness",
            "Ignore": "",
            "Status": "PROPOSED"
        },
        {
            "Hdl": "ZJRqZRubQcy5r3Pdgsf8SA",
            "Icon": "MAP",
            "Name": "Form Steps Required",
            "_cl": "MAKZvz1eTQSvaQdvlHsYNw",
            "_vn": 14,
            "_on": 13,
            "Mapped To Attribute": "Form Steps Required",
            "Ignore": "",
            "Status": "PROPOSED"
        },
        {
            "Hdl": "2ZfRAOL_SwGxQSCg7ejfcA",
            "Icon": "MAP",
            "Name": "clientAssetId",
            "_cl": "MAKZvz1eTQSvaQdvlHsYNw",
            "_vn": 14,
            "_on": 13,
            "Mapped To Attribute": "tag name",
            "Ignore": "",
            "Status": "PROPOSED"
        },
        {
            "Hdl": "3Bj9rmAIR9GG1-jqXALrVA",
            "Icon": "MAP",
            "Name": "document URL",
            "_cl": "MAKZvz1eTQSvaQdvlHsYNw",
            "_vn": 14,
            "_on": 13,
            "Mapped To Attribute": "document URL",
            "Ignore": "",
            "Status": "PROPOSED"
        },
        {
            "Hdl": "W_qYKSMYTwCCUWy04VI68w",
            "Icon": "MAP",
            "Name": "document number",
            "_cl": "MAKZvz1eTQSvaQdvlHsYNw",
            "_vn": 14,
            "_on": 13,
            "Mapped To Attribute": "document number",
            "Ignore": "",
            "Status": "PROPOSED"
        },
        {
            "Hdl": "Asrpp5IWQeaDvXCvOKE9rA",
            "Icon": "MAP",
            "Name": "plant code",
            "_cl": "MAKZvz1eTQSvaQdvlHsYNw",
            "_vn": 30,
            "_on": 13,
            "Mapped To Attribute": "plant code",
            "Ignore": "FALSE",
            "Status": "PROPOSED"
        }
    ],
    "header": [
        "Mapped To Attribute",
        "Ignore",
        "Status"
    ]
}
```

## Response Status Codes
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct and that the handle being used is of an ETL Source
**500** Internal Server Error


