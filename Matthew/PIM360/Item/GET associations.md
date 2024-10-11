# GET /associations

## Description
Returns associations for a certain item type on the provided item.

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **type** (required) (query) The item type of the source item, must be one of:
    * TAGGED_ITEM
    * DOCUMENT
    * EQUIPMENT_ITEM
    * EQUIPMENT_MODEL
    * EIC

* **hdl** (required) (query) The handle of the item to request associations for.

* **assoc** (required) (query) The type of associated item to find, must be one of:
    * TAGGED_ITEM
    * DOCUMENT
    * EQUIPMENT_ITEM
    * EQUIPMENT_MODEL
    * EIC
    * PARENT
    * CHILDREN

* **eic** (optional) (query) Handle of the EIC to use, otherwise active data.

* **skip** (optional) (query) Used for paging, the number of records to skip over.


## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/associations?type=TAGGED_ITEM&hdl=-W4UaC1IS5K5FCmfh5PbSQ&assoc=DOCUMENT&eic=XYSp3hn0TDuJV-NX6MrTBQ' \
--header 'Authorization: ••••••'
```

## Response Body
A JSON object with a property `items` which is an array of associated objects. The object also has a get `getMore` property, if this is set to `1` then there are more associations to retrieve and the skip parameter should be used in the next request. Only 200 associations will be returned per request, so subsequent calls should skip by multiples of 200. If a tagged item has documents that a required against it then these associations will also appear here even if a document has not been provided.

## Example Response
```JSON
{
    "items": [
        {
            "Hdl": "LlFBILLXS_i8pTtsoJrw7Q",
            "ID": "",
            "Type": "NULL",
            "Icon": "general",
            "ClsName": "operations management - operating manual",
            "Description": "",
            "NonNormal": false,
            "AssocAction": "",
            "Provider": {
                "Type": "TAGGED_ITEM",
                "ID": "BLW-001",
                "FacID": "TKF"
            },
            "Url": null
        },
        {
            "Hdl": "O3omyFcTQfWykgsnUqDcSg",
            "ID": "DOC-001",
            "Type": "DOCUMENT",
            "FacID": "TKF",
            "Icon": "general",
            "ClsName": "architectural engineering - approval certificate",
            "Completeness": 8.11,
            "Description": "",
            "NonNormal": true,
            "AssocAction": "Create",
            "ItemAction": "Create",
            "Provider": {
                "Type": "TAGGED_ITEM",
                "ID": "BLW-001",
                "FacID": "TKF"
            },
            "Url": null
        }
    ],
    "getMore": 0
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Matching item has been found and successfully returned. If no associations are present |then a `200` response will be returned but the items array will be empty.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**404** |Requested item can't be found. Check that handle has been provided is correct.|
|**500** |Internal Server Error.|


