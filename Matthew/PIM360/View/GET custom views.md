# GET /customviews

## Description
Gets all custom views in a system, optionally filtered by the `type` parameter.

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
**type** (query) Optional filter for the type of view to return, if not provided then all views are returned. Must be one of:
* LIVE_VIEW
* REGISTER
* EXPLORER_STRUCTURE
* PIVOT_STRUCTURE
* DASHBOARD
* EIC_EXPLORER


## Example Request
`
curl --location 'https://dap-demo.pim360.io/api/customviews?type=LIVE_VIEW' \
--header 'Authorization: ••••••' \
`

## Response Body
A JSON array of objects, where each object is an individual view

## Example Response
```JSON
[
    {
        "Hdl": "62utKNoWTlSkrFg14wYo6w",
        "Public": true,
        "Name": "Freemantle crossings",
        "Model": "TAGGED_ITEM",
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
        },
        "ReadOnly": false
    },
    {
        "Hdl": "he0jdz5XQkW7wuPhtbMSaQ",
        "Public": true,
        "Name": "WA - All Rail Crossings",
        "Model": "TAGGED_ITEM",
        "Type": "LIVE_VIEW",
        "Created": {
            "Name": "User Name",
            "Hdl": "HwiX1yRxSVqzzGpHRg_q5w",
            "Job": "Autodesk",
            "Ts": "2024-07-29T04:37:06.928Z"
        },
        "Modified": {
            "Name": "User Name",
            "Hdl": "HwiX1yRxSVqzzGpHRg_q5w",
            "Job": "Autodesk",
            "Ts": "2024-07-29T04:37:06.928Z"
        },
        "ReadOnly": false
    }
]
```

## Response Status Codes
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**500** Internal Server Error


