# GET /customviews/{handle}

## Description
Get a custom view by handle

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
**handle** (required) (path) The handle of the view requested.


## Example Request
curl --location 'https://{{systemName}}.pim360.io/api/customviews/62utKNoWTlSkrFg14wYo6w' \
--header 'Authorization: ••••••' \

## Response Body
JSON object detailing the requested view.

## Example Response
```JSON
{
    "Hdl": "62utKNoWTlSkrFg14wYo6w",
    "Public": true,
    "Name": "Freemantle crossings",
    "Model": "TAGGED_ITEM",
    "Data": {
        "eicHdl": "UBzA9lXTQzmWtC2mketjdA",
        "fields": [
            "y6b-Bxk1S1KbPG-WEjwsBQ",
            "TssXvM-8Rb27GuDrXCBKjg",
            "XO19QrZgSjqurYdGbfMvdA",
            "vQPCnBpNRwSAjFbTbu_vxw",
            "QlTaiX6jQZez38iQi8tcag",
            "VGR1IxLlSEeXbbHYQP-MUg",
            "HvJUq1IRSrKDwwzEotOQQg"
        ],
        "conditions": {
            "logical": "AND",
            "items": [
                {
                    "handle": "TssXvM-8Rb27GuDrXCBKjg",
                    "operator": "$regex-l",
                    "value": "Fremantle (C)",
                    "caseSensitive": false,
                    "excludeUoM": false,
                    "regex": false,
                    "uom": null
                }
            ]
        }
    },
    "Type": "LIVE_VIEW",
    "Created": {
        "Name": "User Name",
        "Hdl": "HwiX1yRxSVqzzGpHRg_q5w",
        "Job": "Autodesk",
        "Ts": "2024-07-26T04:32:17.978Z"
    },
    "Modified": {
        "Name": "User Name",
        "Hdl": "HwiX1yRxSVqzzGpHRg_q5w",
        "Job": "Autodesk",
        "Ts": "2024-07-29T04:34:34.725Z"
    }
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Matching item has been found and successfully returned.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**404** |Requested item can't be found. Check that the handle has been provided and is correct.|
|**500** |Internal Server Error.|


