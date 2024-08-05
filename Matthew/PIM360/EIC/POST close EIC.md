# POST /eic/close

## Description
Submits a Close EIC activity for the provided EIC.

## Required Capabilities
* CanUseAPI
* CanSeeEICExplorer
* CanCloseEIC

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
**query** (required) (body) JSON object containing a property `eicHdl` specifying which EIC to close


## Example Request
`
curl --location 'https://{{systemName}}.pim360.io/api/eic/close' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
    "eicHdl": "mbcYa6ZYSqO2X9toKkl_kw"
}'
`

## Response Body
A JSON object containing details of the close EIC activity that has been submitted. This does not guarantee that the activity has been successful, to monitor the status of an activity, use the API `GET /etl_queue/activities/{handle}`.

## Example Response
```JSON
{
    "data": {
        "jobSpec": {
            "etlActHdl": "IIzulHQsTLik4WXB0QojVA",
            "etlScript": "/etl360/etl-eic-close/build/main.js",
            "etlJob": {
                "act_name": "Close EIC",
                "act_type": "IMPORT",
                "act_id": "CLOSE_EIC",
                "user_name": "User Name",
                "user_job": "Autodesk",
                "user_handle": "HwiX1yRxSVqzzGpHRg_q5w",
                "auth_address": "https://{{systemName}}.acl360.io/",
                "project_id": "system-name-pim360",
                "eic_handle": "mbcYa6ZYSqO2X9toKkl_kw",
                "act_handle": "IIzulHQsTLik4WXB0QojVA"
            }
        },
        "type": "ETL",
        "status": "PENDING",
        "queueControl": {
            "hold": false,
            "priority": 0,
            "schedule": "2024-08-04T23:32:20.016Z",
            "repeats": {
                "enabled": "off"
            },
            "finished": false
        },
        "eic": {
            "num": 5,
            "hdl": "mbcYa6ZYSqO2X9toKkl_kw"
        },
        "hdl": "uXxJLSczSG2W-HZ4AsPvzA",
        "_id": "66b00f845d8e58078b81200f"
    }
}
```

## Response Status Codes
**200** Close EIC activity has been successfully submitted
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**500** Internal Server Error. Check that the provided EIC handle is valid


