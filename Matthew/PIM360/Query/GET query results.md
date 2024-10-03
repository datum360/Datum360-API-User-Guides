# GET /queryresults/{handle}

## Description
Return a list of results for query by handle

## Required Capabilities
* CanUseAPI
* CanSeeLiveView
* CanSeeAllPages

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **handle** (required) (path) The handle of the query to execute.

* **eic** (query ) Handle of the EIC to use, defaults to whatever was specified in the original query definition.

* **type** (query) The type of item to retrieve can be one of:
    * TAGGED_ITEM
    * EQUIPMENT_ITEM
    * EQUIPMENT_MODEL
    * DOCUMENT
    * EIC
    
Defaults to whatever was specified in the original query.

* **count** (query) Boolean value, if set to `true` then it will only return the count of records available.

* **sortCol** (query) The handle of the attribute to sort results on.

* **sortDir** (query) Boolean value, the direction to sort results on, if `sortCol` is specified. `true` = ascending, `false` = descending.

* **skip** (query) Number of records to skip over, default value of 0. Used for paging results.

* **limit** (query) Number of records to return. Default and maximum of 200.

## Example Request
```
curl --location 'https://systemName.pim360.io/api/queryresults/XarDE_IgSGmHzqGqMkrwzg' \
--header 'Authorization: ••••••' \
--header 'Cookie: express.sid=s%3AwiC2Dkb9piaMM1hsg5GX2382k1xUAl-O.XYLZpGotNqwVlm0htPj2wHx3wqNoffb3Q%2Byiccngm3Q'
```

## Response Body
A JSON object containing the properties: `hdl`, `data`, `timetaken`, `hasmore`, `url`, `queryurl`. `data` is an array of objects, where each object is an item from the query. `hasmore` is a boolean value, if set to `true` then this indicates that there are more records to retrieve and that the `skip` parameter should be used to access them.

## Example Response
```JSON
{
    "hdl": "XarDE_IgSGmHzqGqMkrwzg",
    "data": [
        {
            "hdl": "qVQBFsVuQ-uOl0kwccsZvg",
            "objId": "183",
            "idHdl": "y6b-Bxk1S1KbPG-WEjwsBQ",
            "type": "TAGGED_ITEM",
            "icon": "TAG",
            "QlTaiX6jQZez38iQi8tcag": {
                "value": "TKF",
                "uom": null,
                "valueChange": "",
                "rawValue": "TKF",
                "name": "plant code",
                "isRequired": true
            },
            "y6b-Bxk1S1KbPG-WEjwsBQ": {
                "value": "183",
                "uom": null,
                "valueChange": "",
                "rawValue": "183",
                "name": "tag name",
                "isRequired": true
            },
            "XO19QrZgSjqurYdGbfMvdA": {
                "value": "rail crossing indicator",
                "uom": null,
                "valueChange": "",
                "rawValue": "rail crossing indicator",
                "name": "class name",
                "isRequired": true
            },
            "vQPCnBpNRwSAjFbTbu_vxw": {
                "value": "Cliff St (Fpa) : Single : Public : Boom Barriers : 118Z005",
                "uom": null,
                "valueChange": "",
                "rawValue": "Cliff St (Fpa) : Single : Public : Boom Barriers : 118Z005",
                "name": "description",
                "isRequired": true
            },
            "TssXvM-8Rb27GuDrXCBKjg": {
                "value": "Fremantle (C)",
                "uom": null,
                "valueChange": "",
                "rawValue": "Fremantle (C)",
                "name": "area code",
                "isRequired": true
            },
            "VGR1IxLlSEeXbbHYQP-MUg": {
                "value": "-32.05444666",
                "uom": null,
                "valueChange": "",
                "rawValue": "-32.05444666",
                "name": "latitude",
                "isRequired": true
            },
            "HvJUq1IRSrKDwwzEotOQQg": {
                "value": "115.7418902",
                "uom": null,
                "valueChange": "",
                "rawValue": "115.7418902",
                "name": "longitude",
                "isRequired": true
            }
        }
    ],
    "timetaken": 10,
    "hasmore": false,
    "url": "/queryresults/XarDE_IgSGmHzqGqMkrwzg",
    "queryurl": "/queries/XarDE_IgSGmHzqGqMkrwzg"
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Matching item has been found and successfully returned.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**404** |Requested item can't be found. Check that the handle has been provided and is correct.|
|**500** |Internal Server Error.|


