# POST /facility-explorer/tree

## Description
Submit a Facility Explorer query and return the definition.

## Required Capabilities
* CanUseAPI
* CanSeeFacilityExplorer
* CanSeeAllPages

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **options** (required) (body) JSON object for the query structure with three parameters: `fieldType`, `fieldName`, `conditions`.


## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/facility-explorer/tree' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
    "fieldName": "plant code",
    "fieldType": "plant code",
    "conditions": {}
}'
```

## Response Body
JSON object with a `rows` array, where each object in the array is a row in the facility explorer result.

## Example Response
```JSON
{
    "rows": [
        {
            "QlTaiX6jQZez38iQi8tcag": "TKF",
            "_typed_cmp": 30.41,
            "_cmp": 30.41,
            "_hdl": 1286,
            "descr": "TKF",
            "Value": "TKF",
            "Key": "plant code",
            "Type": "plant code"
        }
    ]
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Query has been successfully submitted and returned.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**500** |Internal Server Error.|


