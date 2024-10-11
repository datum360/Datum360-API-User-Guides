# POST /dashboard/query/history

## Description
Submits a query for a historical trend dashboard widget.

## Required Capabilities
* CanUseAPI
* CanSeeAllPages
* CanSeeDashboard

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **body** (required) (body) JSON object containing the details required for creating the historical trend widget.


## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/dashboard/query/history' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
    "conditions": {
        "logical": "AND",
        "items": [
            {
                "handle": "MAbnLPF8RD2qcKBwXn-ZXA",
                "operator": "$eq",
                "value": 1
            }
        ]
    }
}'
```

## Response Body
JSON object containing the data used to create the historical trend widget.

## Example Response
```JSON 
{
    "data": {
        "TagCnt": [
            [
                1728623031708,
                39881
            ]
        ],
        "Completeness": [
            [
                1728623031708,
                50.2
            ]
        ],
        "length": 1
    }
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200**| Matching item has been found and successfully returned.|
|**401**| Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**500**| Internal Server Error. Check that conditions have been provided in the request body.|


