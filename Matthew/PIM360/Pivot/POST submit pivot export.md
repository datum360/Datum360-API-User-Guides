# POST /pivot/export

## Description
Submits a new activity to export a pivot query.

## Required Capabilities
* CanUseAPI
* CanExportPivot

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **query** (required) (body) JSON object describing the activity to run. Object structure is:
* **eicHdl** Handle of the EIC to query, defaults to active data.\
* **column** The attribute to use for column value.
* **sortCol** The handle of the attribute to sort results on.
* **sortDir** Boolean value, the direction to sort results on, if `sortCol` is specified. `true` = ascending, `false` = descending.
* **objectType** Type of object to query on, must be one of:
    * TAGGED_ITEM
    * EQUIPMENT_ITEM
    * EQUIPMENT_MODEL
    * DOCUMENT
* **conditions** JSON object defining the filter to use when querying data. 
Filter Structure:
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
        * **caseSensitive**: Boolean value defining whether the search should be case sensitive or not.

        * **uom**: If a measure attribute is being queried, the value uom can be specified here. Can also be ``$any`` or ``$isempty``.
* **fields** array of objects, where each object is an attribute to include. Object structure is:
    * **handle** handle of the attribute to include
* **summaries** JSON array of objects where each object is a summary attribute. Object structure is:
    * **aggregator** Type of the summary attribute. Can be one of: 
        * sum
        * cnt
    * **handle** Handle of the summary attribute.

## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/pivot/export' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
    "eicHdl": "",
    "conditions": {
        "logical": "AND",
        "items": []
    },
    "fields": [
        {
            "handle": "2GjKIbc8QI6EQV8M9KNkBg"
        }
    ],
    "column": "",
    "summaries": [
        {
            "aggregator": "cnt",
            "handle": "_cnt"
        }
    ],
    "objectType": "TAGGED_ITEM",
    "sortCol": "2GjKIbc8QI6EQV8M9KNkBg",
    "sortDir": true,
    "output_name": "Pivot-Export"
}'
```

## Response Body
A JSON object containing the details of the submitted export activity.

## Example Response
```JSON
{
    "response": {
        "auth_address": "https://{{systemName}}.acl360.io/",
        "project_id": "system-name-pim360",
        "act_name": "Pivot Export",
        "user_handle": "HwiX1yRxSVqzzGpHRg_q5w",
        "user_name": "User Name",
        "user_job": "Autodesk",
        "act_type": "EXPORT",
        "object_type": "TAGGED_ITEM",
        "eic_handle": "",
        "query": "eyJjb25kaXRpb25zIjp7ImxvZ2ljYWwiOiJBTkQiLCJpdGVtcyI6W119LCJmaWVsZHMiOlt7ImhhbmRsZSI6IjJHaktJYmM4UUk2RVFWOE05S05rQmcifV0sImNvbHVtbiI6IiIsInN1bW1hcmllcyI6W3siYWdncmVnYXRvciI6ImNudCIsImhhbmRsZSI6Il9jbnQifV0sIm9iamVjdFR5cGUiOiJUQUdHRURfSVRFTSIsImNhbGxlZSI6InBpdm90Iiwic29ydENvbCI6IjJHaktJYmM4UUk2RVFWOE05S05rQmciLCJzb3J0RGlyIjp0cnVlLCJyZXF1aXJlR3JvdXBpbmdzIjp0cnVlfQ==",
        "output_name": "Pivot-Export",
        "export_mode": "delimited",
        "act_handle": "AxHfd3p_SdSi19sf5COwRQ"
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


