# GET /queryresults/views/{handle}

## Description
Return a list of view results for the custom view specified.

## Required Capabilities
* CanUseAPI
* CanSeeLiveView
* CanSeeAllPages

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **handle** (required) (path) Handle of the view to retrieve

* **eic** (query string) Handle of the EIC to retrieve data for, defaults to whatever was specified in the original view definition

* **type** (query string) Type of item to retrieve, must be one of:
    * TAGGED_ITEM
    * EQUIPMENT_ITEM
    * EQUIPMENT_MODEL
    * DOCUMENT
defaults to whatever was specified in the original query defintion

* **count** (query string) boolean value, if set to `true` then it will only return the count of records available

* **skip** (query string) Number of records to skip over, default value of 0. Used for paging results

* **limit** (query string) Number of records to return. Default and maximum of 200

## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/queryresults/views/62utKNoWTlSkrFg14wYo6w?eic=UBzA9lXTQzmWtC2mketjdA&type=TAGGED_ITEM' \
--header 'Authorization: ••••••' \
```

## Response Body
A JSON object containing the properties: `data`, `timetaken`, `hasmore`, `url`, `queryurl`. `data` is an array of objects, where each object is an item from the query. `hasmore` is a boolean value, if set to `true` then this indicates that there are more records to retrieve and that the `skip` paramter should be used to access them.

## Example Response
```JSON
{
    "data": [
        {
            "hdl": "qVQBFsVuQ-uOl0kwccsZvg",
            "objId": "183",
            "idHdl": "y6b-Bxk1S1KbPG-WEjwsBQ",
            "type": "TAGGED_ITEM",
            "objectChange": "update",
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
                "value": "new desc",
                "uom": null,
                "valueChange": "update",
                "rawValue": "new desc",
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
        },
        .
        .
        .
    ],
    "timetaken": 10,
    "hasmore": false,
    "url": "/queryresults/undefined",
    "queryurl": "/queries/undefined"
}
```

## Response Status Codes
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


