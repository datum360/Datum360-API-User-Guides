# POST /etl_queue/activities/export

## Description
Submits a new export activity.

## Required Capabilities
* CanUseAPI
* CanExportObject
## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **parameters** (required) (body) JSON object containing the parameters of the activity to run.

## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/etl_queue/activities/export' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
  "liveviewHdl": "62utKNoWTlSkrFg14wYo6w",
  "etlTargetHdl": "4p8gbt4NQd-JHvITyMG0sA",
  "outputFormat": "xlsx",
  "concatUoms": false,
  "ignoreFilter": true,
  "typedData": true,
  "allAttributes": false,
  "type": "TAGGED_ITEM"
}'
```

## Response Body
A JSON object containing the details of the submitted export activity.

## Example Response
```JSON
{
    "response": {
        "act_name": "LiveView Export - Freemantle crossings",
        "act_type": "EXPORT",
        "act_id": "EXPORT_OBJECT",
        "export_mode": "xlsx",
        "export_typed": true,
        "delimiter": "\t",
        "eic_handle": "UBzA9lXTQzmWtC2mketjdA",
        "target_handle": "4p8gbt4NQd-JHvITyMG0sA",
        "missing_value": "Missing",
        "concat_uom": "false",
        "query": "eyJvYmplY3RUeXBlIjoiVEFHR0VEX0lURU0iLCJmaWVsZHMiOlt7ImhhbmRsZSI6Ink2Yi1CeGsxUzFLYlBHLVdFandzQlEifSx7ImhhbmRsZSI6IlRzc1h2TS04UmIyN0d1RHJYQ0JLamcifSx7ImhhbmRsZSI6IlhPMTlRclpnU2pxdXJZZEdiZk12ZEEifSx7ImhhbmRsZSI6InZRUENuQnBOUndTQWpGYlRidV92eHcifSx7ImhhbmRsZSI6IlFsVGFpWDZqUVplejM4aVFpOHRjYWcifSx7ImhhbmRsZSI6IlZHUjFJeExsU0VlWGJiSFlRUC1NVWcifSx7ImhhbmRsZSI6Ikh2SlVxMUlSU3JLRHd3ekVvdE9RUWcifSx7ImhhbmRsZSI6Il9oZGwifSx7ImhhbmRsZSI6Il90eXBlIn0seyJoYW5kbGUiOiJfc3RhdHVzIn1dLCJjb25kaXRpb25zIjp7fSwiY29sdW1uIjoiIiwic3VtbWFyaWVzIjpbXSwibGltaXQiOm51bGwsInVzZUFsaWFzIjpmYWxzZSwic29ydENvbCI6Ink2Yi1CeGsxUzFLYlBHLVdFandzQlEiLCJzb3J0RGlyIjpudWxsLCJjYWxsZWUiOm51bGwsImZpZWxkTWFwIjp7Ink2Yi1CeGsxUzFLYlBHLVdFandzQlEiOiJ5NmItQnhrMVMxS2JQRy1XRWp3c0JRIiwiVHNzWHZNLThSYjI3R3VEclhDQktqZyI6IlRzc1h2TS04UmIyN0d1RHJYQ0JLamciLCJYTzE5UXJaZ1NqcXVyWWRHYmZNdmRBIjoiWE8xOVFyWmdTanF1cllkR2JmTXZkQSIsInZRUENuQnBOUndTQWpGYlRidV92eHciOiJ2UVBDbkJwTlJ3U0FqRmJUYnVfdnh3IiwiUWxUYWlYNmpRWmV6MzhpUWk4dGNhZyI6IlFsVGFpWDZqUVplejM4aVFpOHRjYWciLCJWR1IxSXhMbFNFZVhiYkhZUVAtTVVnIjoiVkdSMUl4TGxTRWVYYmJIWVFQLU1VZyIsIkh2SlVxMUlSU3JLRHd3ekVvdE9RUWciOiJIdkpVcTFJUlNyS0R3d3pFb3RPUVFnIiwiX2hkbCI6Il9oZGwiLCJfdHlwZSI6Il90eXBlIiwiX3N0YXR1cyI6Il9zdGF0dXMifSwiYmFzZUZpZWxkcyI6WyJ5NmItQnhrMVMxS2JQRy1XRWp3c0JRIiwiVHNzWHZNLThSYjI3R3VEclhDQktqZyIsIlhPMTlRclpnU2pxdXJZZEdiZk12ZEEiLCJ2UVBDbkJwTlJ3U0FqRmJUYnVfdnh3IiwiUWxUYWlYNmpRWmV6MzhpUWk4dGNhZyIsIlZHUjFJeExsU0VlWGJiSFlRUC1NVWciLCJIdkpVcTFJUlNyS0R3d3pFb3RPUVFnIl19",
        "output_name": "Freemantle crossings",
        "user_name": "User Name",
        "user_job": "Autodesk",
        "user_handle": "HwiX1yRxSVqzzGpHRg_q5w",
        "act_handle": "uqTumCSpRcCZDFlU-ZwdsA"
    }
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Activity has been successfully submitted.|
|**401**| Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**404**| Requested item can't be found. Check that the handle has been provided and is correct.|
|**500** |Internal Server Error.|


