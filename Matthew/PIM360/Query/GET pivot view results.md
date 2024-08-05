# GET /queryresults/pivot/{handle}

## Description
Return a list of view results for the pivot view specified.

## Required Capabilities
* CanUseAPI
* CanSeeLiveView
* CanSeeAllPages
## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **handle** (required) (path) The handle of the pivot view to get

* **eic** (query) The handle of the EIC to retrieve data from. Defaults to whatever was specified in the original pivot definition

* **type** (query) The type of item to retrieve data for, must be one of:
    * TAGGED_ITEM
    * EQUIPMENT_ITEM
    * EQUIPMENT_MODEL
    * DOCUMENT

Defaults to whatever was specified in the original pivot definition

* **count** (query string) boolean value, if set to `true` then it will only return the count of records available

* **skip** (query string) Number of records to skip over, default value of 0. Used for paging results

* **limit** (query string) Number of records to return. Default and maximum of 200

## Example Request
```
curl --location 'https://dap-demo.pim360.io/api/queryresults/pivot/61N4_YNmRhelnVxHCFTtmQ?type=TAGGED_ITEM' \
--header 'Authorization: ••••••'
```

## Response Body
A JSON object containing the properties: `rows`, `columns`, `total`, `pos`, `hdl`. `rows` is an array of objects where each object is a row in the pivot view. `columns` is a JSON array where each object is a column in the pivot view. `total` shows how many records are in the pivot view. `pos` shows how many records have been skipped

## Example Response
```JSON
{
    "rows": [
        {
            "TssXvM-8Rb27GuDrXCBKjg": "Albany (C)",
            "_req": "322",
            "_cnt": "14"
        },
        {
            "TssXvM-8Rb27GuDrXCBKjg": "Armadale (C)",
            "_req": "138",
            "_cnt": "6"
        },
        .
        .
        .
    ],
    "columns": {
        "TssXvM-8Rb27GuDrXCBKjg": 0,
        "_req": 3,
        "_cnt": 4
    },
    "total": 95,
    "pos": 0,
    "hdl": "61N4_YNmRhelnVxHCFTtmQ"
}
```

## Response Status Codes
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**410** Gone. Check that the pivot view handle has been provided.
**500** Internal Server Error


