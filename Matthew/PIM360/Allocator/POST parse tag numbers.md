# POST /allocator/parse

## Description
Takes a list of tag numbers separated by \n, parses them according to the provided facility and ENS and returns a list of parsed items or parsing errors.

## Required Capabilities
* CanUseAPI
* CanLiveTag

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **taglist** (required) (body) JSON object containing the follow properties:
    * objType - The type of item to parse ID numbers for, must be one of: TAGGED_ITEM, DOCUMENT, EQUIPMENT_ITEM, EQUIPMENT_MODEL.
    * facility - The facility to use when checking for items that already exist.
    * ensName - The name of the ENS to use when validating item numbers.
    * taglist - List of item numbers to validate, separated by \n.


## Example Request
`
curl --location 'https://{{systemName}}.pim360.io/api/allocator/parse' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
    "objtype": "TAGGED_ITEM",
    "facility": "TKF",
    "ensName": "Standard ENS",
    "taglist": "TKF-01-TW-0001\nMCC-01-TL-0001"
}'
`

## Response Body
JSON object containing a summary of the parse results, details of each item are held as objects in the array `parsedItems`.

## Example Response
```JSON
{
    "totalValid": 1,
    "totalInvalid": 1,
    "totalExists": 0,
    "parsedItems": [
        {
            "id": "8iCmloKWQFa2Sb53czTbXQ",
            "parseIssues": [],
            "existance": {
                "Status": "Valid"
            },
            "itemID": "TKF-01-TW-0001",
            "itemName": "",
            "status": "Valid",
            "errorCnt": 0,
            "fac": "TKF",
            "sys": "",
            "clsCode": "TW",
            "sequence": "",
            "suffix": "",
            "srcCls": "Thermowell",
            "funcCls": "thermowell",
            "format": "Instrumentation",
            "discipline": "",
            "parts": [
                {
                    "field": "AAA",
                    "label": "FACILITY",
                    "lookup": "plant code",
                    "minlen": 3,
                    "maxlen": 3,
                    "variablelen": "FALSE",
                    "fieldtype": "ALPHA",
                    "Text": "TKF"
                },
                {
                    "field": "-",
                    "label": "DELIMITER",
                    "lookup": "",
                    "minlen": 1,
                    "maxlen": 1,
                    "variablelen": "FALSE",
                    "fieldtype": "DEL",
                    "Text": "-"
                },
                {
                    "field": "NN",
                    "label": "SYSTEM",
                    "lookup": "system number",
                    "minlen": 1,
                    "maxlen": 2,
                    "variablelen": "TRUE",
                    "fieldtype": "NUM",
                    "Text": "01"
                },
                {
                    "field": "-",
                    "label": "DELIMITER",
                    "lookup": "",
                    "minlen": 1,
                    "maxlen": 1,
                    "variablelen": "FALSE",
                    "fieldtype": "DEL",
                    "Text": "-"
                },
                {
                    "field": "AAAA",
                    "label": "TAG CODE",
                    "lookup": "CLASSCODE",
                    "minlen": 2,
                    "maxlen": 4,
                    "variablelen": "TRUE",
                    "fieldtype": "ALPHA",
                    "Text": "TW"
                },
                {
                    "field": "-",
                    "label": "DELIMITER",
                    "lookup": "",
                    "minlen": 1,
                    "maxlen": 1,
                    "variablelen": "FALSE",
                    "fieldtype": "DEL",
                    "Text": "-"
                },
                {
                    "field": "NNNN",
                    "label": "SEQUENTIAL NUMBER",
                    "lookup": "",
                    "minlen": 4,
                    "maxlen": 4,
                    "variablelen": "TRUE",
                    "fieldtype": "NUM",
                    "Text": "0001"
                }
            ]
        },
        {
            "id": "r6XCGSyMS7KYzdWRl1TzUQ",
            "parseIssues": [
                {
                    "Error": "Field: ASSET - couldn't be parsed.",
                    "ErrorType": 0,
                    "Hint": "Field length must have 3 alphanum characters"
                },
                {
                    "Error": "Extra character(s) 'MCC' found at index 1. <span class='alert'>MCC</span>-01-TL-0001",
                    "ErrorValue": "MCC",
                    "ErrorType": 2,
                    "ErrorField": "ASSET"
                },
                {
                    "Error": "Extra character(s) 'L' found at index 9. MCC-01-T<span class='alert'>L</span>-0001",
                    "ErrorValue": "L",
                    "ErrorType": 2,
                    "ErrorField": "CLASSCODE"
                }
            ],
            "existance": {
                "Status": "Invalid"
            },
            "itemID": "MCC-01-TL-0001",
            "itemName": "",
            "status": "Invalid",
            "errorCnt": 3,
            "fac": "TKF",
            "sys": "",
            "clsCode": "T",
            "sequence": "",
            "suffix": "",
            "srcCls": "Tank",
            "funcCls": "tank",
            "format": "Mechanical and Process Equipment",
            "discipline": "",
            "parts": [
                {
                    "field": "AAA",
                    "label": "ASSET",
                    "lookup": "plant code",
                    "minlen": 3,
                    "maxlen": 3,
                    "variablelen": "FALSE",
                    "fieldtype": "ALPHANUM"
                },
                {
                    "field": "-",
                    "label": "DELIMITER",
                    "lookup": "",
                    "minlen": 1,
                    "maxlen": 1,
                    "variablelen": "FALSE",
                    "fieldtype": "DEL",
                    "Text": "-"
                },
                {
                    "field": "NN",
                    "label": "SYSTEM",
                    "lookup": "system number",
                    "minlen": 1,
                    "maxlen": 2,
                    "variablelen": "TRUE",
                    "fieldtype": "NUM",
                    "Text": "01"
                },
                {
                    "field": "-",
                    "label": "DELIMITER",
                    "lookup": "",
                    "minlen": 1,
                    "maxlen": 1,
                    "variablelen": "FALSE",
                    "fieldtype": "DEL",
                    "Text": "-"
                },
                {
                    "field": "AAAA",
                    "label": "CLASSCODE",
                    "lookup": "CLASSCODE",
                    "minlen": 1,
                    "maxlen": 4,
                    "variablelen": "TRUE",
                    "fieldtype": "ALPHA",
                    "Text": "T"
                },
                {
                    "field": "-",
                    "label": "DELIMITER",
                    "lookup": "",
                    "minlen": 1,
                    "maxlen": 1,
                    "variablelen": "FALSE",
                    "fieldtype": "DEL",
                    "Text": "-"
                },
                {
                    "field": "NNNN",
                    "label": "SEQUENCE NUMBER",
                    "lookup": "",
                    "minlen": 4,
                    "maxlen": 4,
                    "variablelen": "TRUE",
                    "fieldtype": "NUM",
                    "Text": "0001"
                }
            ]
        }
    ]
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Items have been successfully submitted to be validated. This does not guarantee that provided items are valid.|
|**401**| Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**500**| Internal Server Error. Check that all parameters are provided. Check that provided ENS name exists and is correct.|


