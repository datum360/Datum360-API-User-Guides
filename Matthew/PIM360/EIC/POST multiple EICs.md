# POST /eic/publish/multiple    

## Description
Allows multiple EICs to be submitted for publish in one activity.

## Required Capabilities
* CanUseAPI
* CanPublishEIC

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
**query** (required) (body) A JSON object containing a property `hdl`, which is an array of EIC handles to publish.


## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/eic/publish/multiple' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
    "hdl": [
        "XYSp3hn0TDuJV-NX6MrTBQ",
        "tJsy-BtWQbe2SoaTeNVAcQ"
    ]
}'
```

## Response Body
A JSON object containing details of the publish activity that has been submitted. This shows that the activity has been successfully submitted to process but does not guarantee that the publish itself will be successful. To monitor the status of an activity, use the API `GET /etl_queue/activities/{handle}`.

## Example Response
```JSON
{
    "data": {
        "etlActHdl": "2PfSlg7QTSulSCicje49bQ",
        "etlScript": "/etl360/etl-eic-publish-mongodb/build/etl-eic-publish-mongodb.js",
        "etlJob": {
            "act_name": "Publish EIC",
            "act_type": "IMPORT",
            "act_id": "PUBLISH_EIC",
            "user_name": "User Name",
            "user_job": "Autodesk",
            "user_handle": "HwiX1yRxSVqzzGpHRg_q5w",
            "auth_address": "https://{{systemName}}.acl360.io/",
            "project_id": "system-name-pim360",
            "eic_handle": "XYSp3hn0TDuJV-NX6MrTBQ,tJsy-BtWQbe2SoaTeNVAcQ",
            "act_handle": "2PfSlg7QTSulSCicje49bQ"
        }
    }
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |EICs have been successfully submitted for publish. This does not guarantee that the publish has been successful.|
|**400** |Bad request, check that handles have been provided.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**404** |Requested item can't be found. Check that all provided handles are valid|
|**500** |Internal Server Error.|

