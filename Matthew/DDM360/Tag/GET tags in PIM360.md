# GET /tags/query

## Description
Gets details of a tag using the associated tag alias in DDM360.

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **data** (required) (body) JSON object describing the query to get associated tags.


## Example Request
```
curl --location 'https://{{systemName}}.ddm360.io/api/tags/query' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
    "fileHdl": "YP_4TNTGSUiAQYbs8t1uIw",
    "locationType": "OBJECTID",
    "query": {
        "objectId": [
            340
        ]
    }
}'
```

## Response Body
JSON array of objects where each object is a tag that matches the submitted query.

## Example Response
```JSON
[
    {
        "hdl": "hOMGshnmSL6puuKoAtn0EA",
        "tagId": "TK-1004",
        "facId": "TKF"
    }
]
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
**200** |Matching item has been found and successfully returned.
**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.
**404** |Requested item can't be found. Check that the handle has been provided and is correct.
**500** |Internal Server Error.


