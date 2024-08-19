# POST /dashboard/query

## Description
Submit a query to generate a dashboard widget. Returns the data required to build the specified widget. It can be easier to generate the required widget through the UI, then use Developer Tools in the browser to see the data that is being sent. Note that the browser sends data as form data, but the API requires data to be sent as a JSON object in the request body.

## Required Capabilities
* CanUseAPI
* CanSeeDashboard
* CanSeeAllPages

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **body** (required) (body) JSON object containing the query details.
`widgetType` must be one of:
    * bar
    * line
    * pie
    * spider
    * table
    * cell
    * treemap

`eicHdl` must be the handle of the EIC to use or `actual` for published data

`widgetTheme` is using for colouring the top of the widget and must be one of:
    * default
    * danger 
    * warning
    * success
    * info



## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/dashboard/query' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
    "objectType": "TAGGED_ITEM",
    "widgetType": "bar",
    "widgetTheme": "default",
    "eicHdl": "actual",
    "sections": [
        {
            "fields": [
                {
                    "handle": "TssXvM-8Rb27GuDrXCBKjg"
                }
            ]
        },
        {

            "fields": [
                {
                    "aggregator": "cnt",
                    "handle": "QlTaiX6jQZez38iQi8tcag",
                    "operator": "$eq",
                    "value": "TKF"
                }
                
            ]
        }
    ],
    "conditions": {
        "logical": "AND"
    }
}'
```

## Response Body
JSON object containing the data used to populate the specified widget

## Example Response
```JSON
{
    "columns": {
        "area code": 0,
        "plant code": 1
    },
    "data": [
        [
            "Kellerberrin",
            11
        ],
        [
            "Harvey",
            20
        ],
        [
            "Dundas",
            5
        ],
        [
            "Mundaring",
            1
        ],
        [
            "Katanning",
            23
        ],
        .
        .
        .
    ],
    "rows": 96
}
```

## Response Status Codes
**200** Query has been successfully submitted and returned.
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**500** Internal Server Error


