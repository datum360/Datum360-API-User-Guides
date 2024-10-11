# POST /explorer/query

## Description
Submits an attribute explorer query.

## Required Capabilities
* CanUseAPI
* CanSeeAttributeExplorer
* CanSeeAllPages

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **taglist** (required) (body) JSON object representing the query to run.


## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/explorer/query' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{"fields":[{"aggregator":null,"handle":"TssXvM-8Rb27GuDrXCBKjg"},{"aggregator":"sum","handle":"_req"},{"aggregator":"sum","handle":"_pop"},{"aggregator":null,"handle":"_cmp"},{"aggregator":null,"handle":"_typed_cmp"},{"aggregator":null,"handle":"_cnt"}],"objectType":"TAGGED_ITEM","eicHdl":"","conditions":{"logical":"AND","items":[]},"posStart":0,"count":200,"sortDir":true}'
```

## Response Body
JSON object containing the results of the query. The object has an array `rows` where every object in the array is a row in the query results.

## Example Response
```JSON
{
    "rows": [
        {
            "TssXvM-8Rb27GuDrXCBKjg": "Albany (C)",
            "_req": 322,
            "_pop": 98,
            "_cmp": 30.43,
            "_typed_cmp": 30.43,
            "_cnt": "14"
        },
        {
            "TssXvM-8Rb27GuDrXCBKjg": "Armadale (C)",
            "_req": 138,
            "_pop": 42,
            "_cmp": 30.43,
            "_typed_cmp": 30.43,
            "_cnt": "6"
        },
        {
            "TssXvM-8Rb27GuDrXCBKjg": "Ashburton",
            "_req": 299,
            "_pop": 91,
            "_cmp": 30.43,
            "_typed_cmp": 30.43,
            "_cnt": "13"
        }
    ],
    "total": 95,
    "pos": 0
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Query has been successfully submitted and results have been returned.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**500**| Internal Server Error. Potential error in the query provided. Check response body for more details.|


