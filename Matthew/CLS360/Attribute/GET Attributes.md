# GET /domains/{domHdl}/attributes

## Description
Gets all attributes or a single attribute by name, for the Class Library/Domain specified. Only the attribute summary is returned i.e Hdl, Name etc. To get further information, pass the attribute handle to the API `GET /domains/{domHdl}/classes/{clsHdl}`

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **domHdl** (required) (path) The handle of the Class Library/Domain to use

* **attributeName** (query) The name of the attribute to get. Attribute names must be URL encoded.

* **version** (query) The version of the Class Library to get data from


## Example Request
```
curl --location 'https://{{systemName}}.cls360.io/api/domains/MAKZvz1eTQSvaQdvlHsYNw/attributes?attributeName=ISO%20currency%20code' \
--header 'Authorization: ••••••'
```

## Response Body
A JSON object containing an array `rows` where each object in the array is an attribute.

## Example Response
```JSON
{
    "rows": [
        {
            "Hdl": "3it2CsNrSQSIl20mLL6K5Q",
            "Icon": "facility",
            "Name": "ISO currency code",
            "_cl": "MAKZvz1eTQSvaQdvlHsYNw",
            "_vn": 7,
            "_on": 0,
            "Status": "STANDARD"
        }
    ]
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
| 200  | Matching item has been found and successfully returned.    |
| 401 | Unauthorised, authentication is missing or invalid. Check that the token has not expired.     |
| 404    | Requested item can't be found. Check that the handle has been provided and is correct.    |
| 5000    | Internal Server Error.    |
