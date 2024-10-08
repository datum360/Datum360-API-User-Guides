# GET /etl_queue/activities/reference/{actRef}

## Description
Gets the activity associated with the latest run of the provided dataset reference.

## Required Capabilities
* CanUseAPI
* CanSeeQueue

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **actRef** (required) (path) The dataset reference to use to request the activity.


## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/etl_queue/activities/reference/export' \
--header 'Authorization: ••••••' 
```

## Response Body
JSON object containing the details of the matching activity.

## Example Response
```JSON
{
    "_id": "66b06f2affbb8133f2b6e851",
    "Hdl": "PQMgq8U5QJyHoPpce_I1AQ",
    "Attachments": [],
    "Completed": "2024-08-05T06:20:28.275Z",
    "Created": {
        "Hdl": "HwiX1yRxSVqzzGpHRg_q5w",
        "Name": "User Name",
        "Job": "Autodesk",
        "Ts": "2024-08-05T06:20:23.779Z"
    },
    "DatasetReference": "export",
    "Name": "LiveView Export - LiveView",
    "Src": null,
    "Started": "2024-08-05T06:20:23.779Z",
    "TaskCnt": 1,
    "TaskNo": 1,
    "Tasks": [
        {
            "Hdl": "5JY0YkhIQTi-uhb0D62H3Q",
            "ActHdl": "PQMgq8U5QJyHoPpce_I1AQ",
            "Name": "Exporting Items",
            "Status": "Complete",
            "TotalRowCnt": 1286,
            "CurrRow": 1286,
            "ErrCnt": 0,
            "Attachments": [
                {
                    "Hdl": "IczLKusgRgiNP8307B89YQ",
                    "Name": "LiveView.xlsx.zip",
                    "Type": "zip"
                }
            ],
            "Started": "2024-08-05T06:20:26.462Z",
            "Completed": "2024-08-05T06:20:28.275Z"
        }
    ],
    "Type": "REPORT",
    "Status": "Complete"
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Matching item has been found and successfully returned.|
|**401**| Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**404**| Requested item can't be found. Check that the handle has been provided and is correct.|
|**500**| Internal Server Error.|


