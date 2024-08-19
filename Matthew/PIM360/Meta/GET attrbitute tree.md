# GET /attributes/tree

## Description
Get a list of available attributes

## Required Capabilities
* CanUseAPI
* CanSeeLiveView
* CanSeeAllPages

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters



## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/attributes/tree' \
--header 'Authorization: ••••••'
```

## Response Body
Array of JSON objects, where each object is an attribute group with a property `attributes`, containg all objects within that group

## Example Response
```JSON
[
    {
        "label": "Full text",
        "haslookup": false,
        "type": "string",
        "icon": "find",
        "ismeasure": false,
        "hdl": "FTS"
    },
    {
        "label": "Metadata",
        "hdl": "METADATA",
        "attributes": [
            {
                "label": "Type",
                "meta": true,
                "icon": "general",
                "type": "string",
                "ismeasure": false,
                "hdl": "Type"
            },
            {
                "label": "Lifecycle Status",
                "meta": true,
                "icon": "general",
                "type": "string",
                "ismeasure": false,
                "hdl": "Status"
            },
            {
                "label": "Created",
                "meta": true,
                "icon": "general",
                "type": "date",
                "ismeasure": false,
                "hdl": "Created.Ts"
            },
            {
                "label": "Last Modified",
                "meta": true,
                "icon": "general",
                "type": "date",
                "ismeasure": false,
                "hdl": "Modified.Ts"
            },
            .
            .
            .
        ]
    }
]
```

## Response Status Codes
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**500** Internal Server Error


