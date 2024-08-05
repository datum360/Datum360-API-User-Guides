# POST /eic/query

## Description
Submit an EIC query and return all EICs that match the query

## Required Capabilities
* CanUseAPI
* CanGenerateDCF
* CanSeeEicExplorer
* CanSeeAllPages

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
**query** (required) (body) JSON object containing a property `attributeFilter` which is an array of objects. Where each object is an attribute handle to query and the value to search for.


## Example Request
`
curl --location 'https://{{systemName}}.pim360.io/api/eic/query' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
    "attributeFilter": [
        {
        "hdl": "wHq8duseQeiKHFTEq6zoog",
        "value": "Commissioning Demo"
        }
    ]
}'
`

## Response Body
A JSON object with an attribute `rows` containing an array of objects, one object for each EIC that matches the query. If no matching items are found then an empty array will be returned.

## Example Response
```JSON
{
    "rows": [
        {
            "id": "XYSp3hn0TDuJV-NX6MrTBQ",
            "ID": 1,
            "Status": "Active",
            "cmp": 8.97,
            "typed_cmp": 8.97,
            "wHq8duseQeiKHFTEq6zoog": "Commissioning Demo",
            "WzGMbejhR5i8FFPJ8354iQ": "Seed ACC (This EIC)",
            "L48ZcUL6RWeDwDZeAkLvwQ": 1,
            "vQPCnBpNRwSAjFbTbu_vxw": "Commissioning Demo",
            "crBhwt7JTAGGZNHDeUucVg": "Submitted",
            "XO19QrZgSjqurYdGbfMvdA": "Commissioning Integration"
        }
    ]
}
```

## Response Status Codes
**200** Matching item has been found and successfully returned
**400** Bad request, check that the EIC attribute handle provided is valud.
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**500** Internal Server Error


