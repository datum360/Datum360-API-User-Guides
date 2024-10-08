# POST /eic/attributes/unique

## Description
Returns a set of unique values of EIC attributes (defined by `uniqueAttributeHdl`), optionally filtered by the `attributeFilter` array.

## Required Capabilities
* CanUseAPI
* CanGenerateDCF
* CanSeeEicExplorer
* CanSeeAllPages

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
**query** (required) (body) JSON object containing properties `attributeFilter` and `uniqueAttributeHandle`. `attributeFilter` is an array of objects containing attribute handles and values to filter on. `uniqueAttributeHandle` is a single attribute handle to get unique values for.


## Example Request
The below request will get all unique values for the attribute with handle `vQPCnBpNRwSAjFbTbu_vxw` and then filter on those EICs where the attribute with handle `crBhwt7JTAGGZNHDeUucVg` and value of "Submitted".

`
curl --location 'https://{{systemName}}.pim360.io/api/eic/attributes/unique' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
    "attributeFilter": [
        {
            "hdl": "crBhwt7JTAGGZNHDeUucVg",
            "value": "Submitted"
        }
    ],
    "uniqueAttributeHdl": "vQPCnBpNRwSAjFbTbu_vxw"
}'
`

## Response Body
A JSON object with an attribute `rows`. `rows` is an array of objects where each object is a key value pair of attribute handle and attribute values that match the provided query.

## Example Response
```JSON
{
    "rows": [
        {
            "vQPCnBpNRwSAjFbTbu_vxw": "Commissioning Demo"
        },
        {
            "vQPCnBpNRwSAjFbTbu_vxw": "GIS"
        }
    ]
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Matching item has been found and successfully returned.|
|**400** |Bad request, check that `uniqueAttributeHandle` has been provided and is a valid handle.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**404** |Requested item can't be found. Check that the handle has been provided and is correct.|
|**500** |Internal Server Error.|


