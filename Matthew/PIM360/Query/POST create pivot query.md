# POST /pivot/query

## Description
Creates a new pivot query and submits it to return the results

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
**query** (required) (body) The object to create the pivot query. Object structure is:

* **fields** array of objects, where each object is an attribute to include. Object structure is:
    * **handle** handle of the attribute to include
* **objectType** Type of object to query on, must be one of:
    * TAGGED_ITEM
    * EQUIPMENT_ITEM
    * EQUIPMENT_MODEL
    * DOCUMENT
* **eicHdl** Handle of the EIC to query, defaults to active data

* **conditions** JSON object defining the filter to use when querying data. Filter Structure:
    * **logical**: What logical operator to apply when specifying multiple filter items. Must be one of:
        * AND
        * OR
    
    * **items** Array of objects, where each object is a filter to apply to the query. Object structure is:
        * **handle** Handle of the attribute to filter on
        * **operator** Operator to apply as part of the filter, must be one of:
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

* **column** The atribute to use for column value

* **summaries** JSON array of objects where each object is a summary attribute. Object structure is:
    * **aggregator** type of the summary attribute. Can be one of: 
        * sum
        * cnt
    * **handle** handle of the summary attribute 

* **sortCol** The handle of the attribute to sort results on

* **sortDir** boolean value, the direction to sort results on, if `sortCol` is specified. `true` = ascending, `false` = descending

* **posStart**  where to start in the query. Defaults to 0

* **count** How many records to fetch

* **isCount** Boolean value, whether to return the count of records or not

## Example Request
```
curl --location 'https://dap-demo.pim360.io/api/pivot/query' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{"eicHdl":"UBzA9lXTQzmWtC2mketjdA","conditions":{"logical":"AND","items":[{"handle":"TssXvM-8Rb27GuDrXCBKjg","operator":"$regex-l","value":"Fremantle","caseSensitive":false,"excludeUoM":false,"regex":false,"uom":null}]},"fields":[{"handle":"TssXvM-8Rb27GuDrXCBKjg"}],"column":"HvJUq1IRSrKDwwzEotOQQg","summaries":[{"aggregator":"sum","handle":"_req"},{"aggregator":"cnt","handle":"_cnt"},{"aggregator":"sum","handle":"_group_qy86Z4MwSs6mZDjDtefNKw_typed_cmp"}],"objectType":"TAGGED_ITEM","sortCol":"TssXvM-8Rb27GuDrXCBKjg","sortDir":true,"isCount":true}'
```

## Response Body
JSON object containing the results of the pivot query

## Example Response
```JSON
{
    "columns": {
        "count": 0
    },
    "rows": [
        {
            "count": 1
        }
    ],
    "total": 1,
    "pos": 0
}
```

## Response Status Codes
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


