# POST /queries

## Description
Create a query used for retrieving data from Liveview. This does not execute the query but simply saves it to be executed repeadetly at another time.

## Required Capabilities
* CanUseAPI
* CanSeeLiveView
* CanSeeAllPages

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
**query** (required) (body) JSON object defining the structure of the query. Parameters are:

* **type**: The type of item being queried, must be one of:
    * TAGGED_ITEM
    * DOCUMENT
    * EQUIPMENT_ITEM
    * EQUIPMENT_MODEL

* **eic**: The handle of the EIC to retrieve data from, if missing or blank then active data will be used.

* **filter**: JSON object defining the filter to use when querying data. Filter Structure:
    * **logical**: What logical operator to apply when specifying multiple filter items. Must be one of:
        * AND
        * OR
    
    * **items**: Array of objects, where each object is a filter to apply to the query. Object structure is:
        * **handle**: Handle of the attribute to filter on
        * **operator**: Operator to apply as part of the filter, must be one of:
            * **$regex-l**: attribute **contains** value
            
            * **$eq**: value **is**

            * **$ne**: value **is not**

            * **$empty**:  value **is empty**

            * **$notempty**: value **is not empty**

            * **$required**: value **is required**

            * **$notrequired**: value **is not required**

            * **$in**: value is **in**

            * **$regex-b**: value **begins with**

            * **$regex-e**: value **ends with**

            * **$regex-nl**: value does **not contain**

            * **$regex-nb**: value does **not begin with**

            * **$regex-ne**: value does **not end with**

            * **$regex**: value **matches regex**
        * **caseSensitive**: boolean value defining whether the search should be case sensitive or not

        * **uom**: If a measure attribute is being queried, the value uom can be specified here. Can also be $any or $isempty


* **fields**: Array of strings containg the handles of the attributes to return


## Example Request
```JSON
curl --location 'https://{{systemName}}.pim360.io/api/queries' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{"type":"TAGGED_ITEM","eic":"UBzA9lXTQzmWtC2mketjdA","conditions":{"logical":"OR","items":[{"handle":"TssXvM-8Rb27GuDrXCBKjg","operator":"$eq","value":"Fremantle (C)","caseSensitive":false,"excludeUoM":false,"regex":false,"uom":null}]},"fields":["y6b-Bxk1S1KbPG-WEjwsBQ","TssXvM-8Rb27GuDrXCBKjg","XO19QrZgSjqurYdGbfMvdA","vQPCnBpNRwSAjFbTbu_vxw","QlTaiX6jQZez38iQi8tcag","VGR1IxLlSEeXbbHYQP-MUg","HvJUq1IRSrKDwwzEotOQQg"]}'
```

## Response Body
JSON object with the details of the created query

## Example Response
```JSON
{
    "url": "/api/queries/26ZkoLLpQi-KkGXcalxHMg",
    "resulturl": "/queryresults/26ZkoLLpQi-KkGXcalxHMg",
    "hdl": "26ZkoLLpQi-KkGXcalxHMg"
}
```

## Response Status Codes
**201** Query has been created
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**500** Internal Server Error


