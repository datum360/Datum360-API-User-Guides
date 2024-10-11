# POST /rundeltareport

## Description
Submits a new delta report activity.

## Required Capabilities
* CanUseAPI
* CanManageCls360Snapshot

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **parameters** (required) (body) JSON object containing the parameters of the activity to run. Parameters are:
    * `startnum` - The version number to start the report from.
    * `endnum` - The version number to end the report from.
    * `fileFormat` - The type of file to export. Must be one of `.txt` or `.xlsx`.
    * `domain` - The name of the class library/domain to run the report on.

## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/rundeltareport' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
  "startnum": 1,
  "endnum": 61,
  "fileFormat": ".txt",
  "domain": "CFIHOS v1.5.1"
}'
```

## Response Body
A JSON object containing the details of the submitted delta report activity.

## Example Response
```JSON
{
    "Hdl": "rf_yTQA_SWih7nZehkB46Q",
    "Name": "Delta Report for - CFIHOS v1.5.1 between versions 1 and 61",
    "Type": "REPORT",
    "Created": {
        "Hdl": "HwiX1yRxSVqzzGpHRg_q5w",
        "Name": "User Name",
        "Job": "Autodesk",
        "Ts": "2024-08-13T04:19:12.185Z"
    },
    "TaskNo": 0,
    "TaskCnt": 0,
    "Attachments": [
        {
            "Hdl": "gbzBNmhvT0qxvSPIhUPJEQ",
            "Name": "deltareport_CFIHOS v1.5.1_between_1_and_61.txt",
            "Type": "txt"
        }
    ],
    "Tasks": [],
    "Started": "2024-08-13T04:19:12.185Z",
    "Completed": "2024-08-13T04:19:16.093Z",
    "CommentCnt": 0,
    "Status": "Complete"
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Activity has been successfully submitted.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**404** |Requested item can't be found. Check that the handle has been provided and is correct.|
|**500** |Internal Server Error.|


