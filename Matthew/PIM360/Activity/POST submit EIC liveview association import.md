# POST /etl_queue/activities/eic_related_obj_assoc/liveivew

## Description
Submits an EIC relatated object association activity. Specifying an EIC to import into and a liveview query to determine which tags to import

## Required Capabilities
* CanUseAPI
* CanAssociateItemsToEIC

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **EicRelatedObjAssocImport** (required) (body) JSON object describing where to import the data and what data to import. The object has two properties `targetEIC` and `query`. `targetEIC` holds the handle of the EIC to import into. `query` is used to specify which items to load into the EIC.


## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/etl_queue/activities/eic_related_obj_assoc/liveview' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
    "targetEIC": "XYSp3hn0TDuJV-NX6MrTBQ",
    "query": {
        "type": "TAGGED_ITEM",
        "filter": {
            "logical": "OR",
            "items": [
                {
                    "handle": "TssXvM-8Rb27GuDrXCBKjg",
                    "operator": "$eq",
                    "value": "Fremantle (C)",
                    "caseSensitive": false,
                    "excludeUoM": false,
                    "regex": false,
                    "uom": null
                }
            ]
        }
    }
}'
```

## Response Body
A JSON object containing the details of the submitted EIC object association import activity

## Example Response
```JSON
{
    "etlActHdl": "Nu48rkbATAaKyWJUbREvvQ",
    "etlScript": "/etl360/etl-eic-ass-import/build/etl-eic-ass-import-v2.js",
    "etlJob": {
        "auth_address": "https://{{systemName}}.acl360.io/",
        "project_id": "system-name-pim360",
        "project_host": "https://{{systemName}}.pim360.io/",
        "act_name": "EIC Related Object Association Import",
        "act_type": "IMPORT",
        "object_type": "TAGGED_ITEM",
        "eic_handle": "XYSp3hn0TDuJV-NX6MrTBQ",
        "query": "eyJvYmplY3RUeXBlIjoiVEFHR0VEX0lURU0iLCJlaWNOdW1iZXIiOm51bGwsImZpZWxkcyI6W3siaGFuZGxlIjoieTZiLUJ4azFTMUtiUEctV0Vqd3NCUSJ9LHsiaGFuZGxlIjoiUWxUYWlYNmpRWmV6MzhpUWk4dGNhZyJ9XSwiY29uZGl0aW9ucyI6eyJsb2dpY2FsIjoiT1IiLCJpdGVtcyI6W3siaGFuZGxlIjoiVHNzWHZNLThSYjI3R3VEclhDQktqZyIsIm9wZXJhdG9yIjoiJGVxIiwidmFsdWUiOiJGcmVtYW50bGUgKEMpIiwiY2FzZVNlbnNpdGl2ZSI6ZmFsc2UsImV4Y2x1ZGVVb00iOmZhbHNlLCJyZWdleCI6ZmFsc2UsInVvbSI6bnVsbH1dfSwiY29sdW1uIjoiIiwic3VtbWFyaWVzIjpbXSwibGltaXQiOm51bGwsInVzZUFsaWFzIjpmYWxzZSwic29ydENvbCI6Ink2Yi1CeGsxUzFLYlBHLVdFandzQlEiLCJjYWxsZWUiOm51bGwsImZpZWxkTWFwIjp7Ink2Yi1CeGsxUzFLYlBHLVdFandzQlEiOiJ5NmItQnhrMVMxS2JQRy1XRWp3c0JRIiwiUWxUYWlYNmpRWmV6MzhpUWk4dGNhZyI6IlFsVGFpWDZqUVplejM4aVFpOHRjYWcifSwiYmFzZUZpZWxkcyI6WyJ5NmItQnhrMVMxS2JQRy1XRWp3c0JRIiwiUWxUYWlYNmpRWmV6MzhpUWk4dGNhZyJdfQ==",
        "user_name": "User Name",
        "user_job": "Autodesk",
        "user_handle": "HwiX1yRxSVqzzGpHRg_q5w",
        "act_handle": "Nu48rkbATAaKyWJUbREvvQ"
    }
}
```

## Response Status Codes
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


