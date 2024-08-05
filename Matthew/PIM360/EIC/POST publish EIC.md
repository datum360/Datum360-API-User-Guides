# POST /eic/publish

## Description
Publishes the provided EIC

## Required Capabilities
* CanUseAPI
* CanPublishEIC

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
**query** (required) (body) An object containing the handle of the EIC to publish


## Example Request
curl --location 'https://{{systemName}}.pim360.io/api/eic/publish' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
    "hdl": "XYSp3hn0TDuJV-NX6MrTBQ"
}'

## Response Body
A JSON object containing details of the publish activity that has been submitted. This shows that the activity has been successfully submitted to process but does not guarantee that the publish itself will be successful. To monitor the status of an activity, use the API `GET /etl_queue/activities/{handle}`.

## Example Response
```JSON
{
    "data": {
        "etlActHdl": "100XZd0VRZ-HpW_i0oNMHw",
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
            "eic_handle": "XYSp3hn0TDuJV-NX6MrTBQ",
            "act_handle": "100XZd0VRZ-HpW_i0oNMHw"
        }
    }
}
```

## Response Status Codes
**200** EIC has been successfully submitted for publish. This does not guarantee that the publish itself is successful.
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


