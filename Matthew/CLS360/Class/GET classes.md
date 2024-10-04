# GET /domains/{domHdl}/classes

## Description
Gets all Classes from the specified Class Library/Domain. An optional filter can be provided to specify which Classes to return

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
 * **domHdl** (required) (path) Handle of the Class Library/Domain to search in

 * **filter** (query) Optional filter to search classes. Supports operators "eq" (equal) and "cnt" (contains), combine conditions with "and". Fields and values that contain spaces need wrapping with [square braces]
    Example:
    `Name cnt CABLE and [Object Type] eq Functional`

The filter should also be URL encoded when added to the query. The above example would look like:
    `Name%20cnt%20CABLE%20and%20%5BObject%20Type%5D%20eq%20Functional`
Replacing spaces with %20 and square brackets with %5B [ and %5D ]

* **pageSize** (query) Number of entries to return. Maximum and Default of 200

* **page** (query) Skip entries in multiples of `pageSize`. e.g if `pageSize` is 200 and `page` is 2, then 400 records will be skipped and records 400 - 600 will be returned. If `pageSize` has not been provided then a default value of 200 will be assumed

* **version** (query) Which version of the Class Library/Domain to use when returning data. If no value is provided, then the current version will be used.

## Example Request
```
curl --location 'https://{{systemName}}.cls360.io/api/domains/MAKZvz1eTQSvaQdvlHsYNw/classes?filter=Name%20eq%20cabinet%20and%20%5BObject%20Type%5D%20eq%20Functional' \
--header 'Authorization: ••••••' \
```

## Response Body
A JSON object containing an array `value` where each entry in the array is a class that matches the provided filter

## Example Response
```JSON
{
    "value": [
        {
            "Hdl": "_CU46pvVSd-i3KkyPfVkVg",
            "_cl": "MAKZvz1eTQSvaQdvlHsYNw",
            "_vn": 50,
            "_on": 0,
            "Name": "cabinet",
            "Asset Code": "CABI",
            "CFIHOS Object Type": "Functional",
            "abstract class flag": "no",
            "ID": "CFIHOS-30000007",
            "Description": "Is an enclosure intended to hold and protect electrical components.",
            "tag number format": "",
            "equipment installed": "yes",
            "reason for having class": "",
            "synonym": "",
            "change request number": "CR0005;CR0030;CR0029;FR60",
            "POSC CAESAR": "RDS485369",
            "ISO 15926 part4": "",
            "STEPLIB": "70037",
            "Section": "",
            "CFIHOS Note / Comment": "",
            "CFIHOS Data Source": "",
            "Icon": "TAG",
            "Status": "STANDARD",
            "Applicable to Commissioning": "",
            "Object Type": "Functional",
            "Discipline": "electrical engineering",
            "Class Library": "CFIHOS v1.5.1"
        }
    ]
}
```

## Response Status Codes
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the class library handle is correct.
**500** Internal Server Error


