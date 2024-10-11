# GET /domains

## Description
Lists all domains/class libraries in CLS360

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **pageSize** (query) Maximum number of entries to return. Default value is 200.
* **page** (query) Skip entries in multiples of `pageSize`. e.g if `pageSize` is 200 and `page` is 2, then 400 records will be skipped and records 400 - 600 will be returned. If `pageSize` has not been provided then a default value of 200 will be assumed.

## Example Request
```
curl --location 'https://{{systemName}}.cls360.io/api/domains' \
--header 'Authorization: ••••••' \
```

## Response Body
JSON array of objects, where each object represents a class library/domain. The object contains information such as the class library name, handle and current version

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
| Status Code | Description |
| -------- | ------- |
|**200** |Items have been found and successfully returned.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**500** |Internal Server Error.|


