# GET /etl_queue

## Description
Gets the status of the activity queue and a list of all running and pending activities

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters



## Example Request
```
curl --location 'https://dap-demo.pim360.io/api/etl_queue' \
--header 'Authorization: ••••••'
```

## Response Body
JSON object containing Activity Queue status attributes `locked`, `pausing` and `state`. As well as `queue` which is an array of objects with one object per activity in the queue

## Example Response
```JSON
{
    "queue": [
        {
            "_id": "66b45f839da9c3f5231f3d4f",
            "jobSpec": {
                "etlActHdl": "JgRF5xHGRt2ik4c-zX4zCQ",
                "etlScript": "/etl360/etl-tag-import-incremental-rebuild/build/etl-tag-import-incremental-rebuild.js",
                "etlJob": {
                    "act_name": "Object Import - Wide Format",
                    "act_type": "IMPORT",
                    "act_id": "IMPORT_OBJECT_WIDE",
                    "user_name": "User Name",
                    "user_job": "Autodesk",
                    "user_handle": "HwiX1yRxSVqzzGpHRg_q5w",
                    "auth_address": "https://{{systemName}}.acl360.io/",
                    "project_id": "system-name-pim360",
                    "object_type": "TAGGED_ITEM",
                    "source_handle": "3tGdPZ5UQxSnQhHVcsnWOA",
                    "eic_handle": "pc4KTt--SoqnZGTEe3d3Bw",
                    "deliverable": "KYYNisAIR3WdmDWgag1zow",
                    "classification": "cls",
                    "ens_name": "",
                    "terminate_attributes": "empty",
                    "load_unknown_attributes": "true",
                    "worksheets": 1,
                    "default_class": "null",
                    "allow_new": "true",
                    "pre_script": "preprocess-wide.sh",
                    "uom_label": "UOM",
                    "inputfile": "-GtPTSRbTmum1yejX6Wi8Q",
                    "act_handle": "JgRF5xHGRt2ik4c-zX4zCQ"
                }
            },
            "type": "ETL",
            "status": "RUNNING",
            "queueControl": {
                "hold": false,
                "priority": 0,
                "schedule": "2024-08-08T06:02:43.293Z",
                "repeats": {
                    "enabled": "off"
                },
                "finished": false,
                "workerPid": null
            },
            "eic": {
                "num": 4,
                "hdl": "pc4KTt--SoqnZGTEe3d3Bw"
            },
            "hdl": "QayVKbPMS0usY2DnyR_jVA"
        }
    ],
    "state": "IDLE",
    "pausing": false,
    "locked": false,
    "counts": {
        "Pending": 0,
        "Held": 0
    }
}
```

## Response Status Codes
**200** Sucessfully returned queue data
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**500** Internal Server Error


