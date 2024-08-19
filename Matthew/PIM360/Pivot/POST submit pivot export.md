# POST /pivot/export

## Description
Submit a new activity to export a pivot query

## Required Capabilities
* CanUseAPI
* CanExportPivot

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **query** (required) (body) JSON object describing the activity to run


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
A JSON object containing the details of the submitted export activity

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
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


