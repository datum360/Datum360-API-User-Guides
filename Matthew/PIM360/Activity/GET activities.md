# GET /timeline

## Description
Gets a list of all activities from the activity timeline.

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **categories** (query) The type of activities to get. Must be one of:
    * ALL
    * REPORT
    * EXPORT
    * IMPORT
    * DELTA_REPORT
    * CLS_SNAPSHOT_IMPORT

* **offset** (query) The number of records to skip over, used for paging and defaults to 0.

* **limit** (query) The number of records to return, default and maximum of 200.

* **own** (query) Whether to return only the authenticated users activities. `1` = `true`, defaults to `false`.

* **eic** (query) EIC handle to restrict activities to.

* **hdl** (query) Handle of specific activity to get.

## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/timeline' \
--header 'Authorization: ••••••'
```

## Response Body
Array of objects where each object is an activity, containing details of the individual tasks within that activity. If no matching activities are found then an empty array is returned.

## Example Response
```JSON
[
    {
        "_id": "66b04e1effbb8133f2b66ffb",
        "Hdl": "tEN1yvVGSLWm3a1Ksm2CZw",
        "Attachments": [],
        "Completed": "2024-08-05T03:59:26.890Z",
        "Created": {
            "Hdl": "HwiX1yRxSVqzzGpHRg_q5w",
            "Name": "User Name",
            "Job": "Autodesk",
            "Ts": "2024-08-05T03:59:24.043Z"
        },
        "EIC": {
            "Hdl": "UBzA9lXTQzmWtC2mketjdA",
            "ID": 3
        },
        "Name": "EIC-3 Object Import - Wide Format",
        "Src": "ECDTZbe6RyaFSKwzBgtFHQ",
        "Started": "2024-08-05T03:59:24.043Z",
        "TaskCnt": 4,
        "TaskNo": 4,
        "Tasks": [
            {
                "Hdl": "oK-c8CTOTlK04e95dIIGvQ",
                "ActHdl": "tEN1yvVGSLWm3a1Ksm2CZw",
                "Name": "Postprocessing",
                "Status": "Complete",
                "TotalRowCnt": 0,
                "CurrRow": 0,
                "ErrCnt": 0,
                "Attachments": [
                    {
                        "Hdl": "_X8ESJ-tQ2eeR0eq5351eg",
                        "Name": "system-name-pim360-imp-log-2024.08.05_03.59.24.txt.zip",
                        "Type": "zip"
                    }
                ],
                "Started": "2024-08-05T03:59:26.648Z",
                "Completed": "2024-08-05T03:59:26.890Z"
            },
            {
                "Hdl": "uhiFLPXRRTuvjRV-uavXnA",
                "ActHdl": "tEN1yvVGSLWm3a1Ksm2CZw",
                "Name": "Processing files",
                "Status": "Complete",
                "TotalRowCnt": 1,
                "CurrRow": 1,
                "ErrCnt": 0,
                "Attachments": [],
                "Started": "2024-08-05T03:59:26.545Z",
                "Completed": "2024-08-05T03:59:26.647Z"
            },
            {
                "Hdl": "sxDPu6NUQsex7UP2KJvHAw",
                "ActHdl": "tEN1yvVGSLWm3a1Ksm2CZw",
                "Name": "Checking files",
                "Status": "Complete",
                "TotalRowCnt": 0,
                "CurrRow": 0,
                "ErrCnt": 0,
                "Attachments": [],
                "Started": "2024-08-05T03:59:26.517Z",
                "Completed": "2024-08-05T03:59:26.544Z"
            },
            {
                "Hdl": "5TY4HV61Td6uBPHRrD4rBA",
                "ActHdl": "tEN1yvVGSLWm3a1Ksm2CZw",
                "Name": "Loading files",
                "Status": "Complete",
                "TotalRowCnt": 0,
                "CurrRow": 0,
                "ErrCnt": 0,
                "Attachments": [
                    {
                        "Hdl": "2rrFj3OMQHm-u-fLLpekzA",
                        "Name": "AttributesChange_for_183_in_EIC-3.txt",
                        "Type": "txt"
                    }
                ],
                "Started": "2024-08-05T03:59:26.442Z",
                "Completed": "2024-08-05T03:59:26.516Z"
            }
        ],
        "Type": "IMPORT",
        "CommentCnt": 1,
        "Status": "Complete",
        "Comments": [
            {
                "_id": "66b04e1e2c9cf54df39e73b9",
                "Text": "<table class='table table-striped table-condensed table-bordered'><thead></thead><tbody><tr><td style='word-break: normal'><b>Objects processed</b></td><td style='word-break: normal'>1</td></tr><tr><td style='word-break: normal'><b>Valid objects</b></td><td style='word-break: normal'>1</td></tr><tr><td style='word-break: normal'><b>Invalid objects</b></td><td style='word-break: normal'>0</td></tr><tr><td style='word-break: normal'><b>Objects classified by class name</b></td><td style='word-break: normal'>1</td></tr><tr><td style='word-break: normal'><b>Objects that could not be classified by class name</b></td><td style='word-break: normal'>0</td></tr><tr><td style='word-break: normal'><b>Tag format not found</b></td><td style='word-break: normal'>0</td></tr><tr><td style='word-break: normal'><b>Tag code not found</b></td><td style='word-break: normal'>0</td></tr><tr><td style='word-break: normal'><b>Tag code not mapped</b></td><td style='word-break: normal'>0</td></tr><tr><td style='word-break: normal'><b>Missing association values</b></td><td style='word-break: normal'>0</td></tr><tr><td style='word-break: normal'><b>Association Object does not exist</b></td><td style='word-break: normal'>0</td></tr><tr><td style='word-break: normal'><b>Attributes processed</b></td><td style='word-break: normal'>4</td></tr><tr><td style='word-break: normal'><b>Attributes missing</b></td><td style='word-break: normal'>0</td></tr><tr><td style='word-break: normal'><b>Attributes found</b></td><td style='word-break: normal'>4</td></tr><tr><td style='word-break: normal'><b>Attributes ignored</b></td><td style='word-break: normal'>0</td></tr><tr><td style='word-break: normal'><b>Valid attributes</b></td><td style='word-break: normal'>4</td></tr><tr><td style='word-break: normal'><b>Invalid attributes</b></td><td style='word-break: normal'>0</td></tr><tr><td style='word-break: normal'><b>Attributes not found</b></td><td style='word-break: normal'>0</td></tr><tr><td style='word-break: normal'><b>Data Typing failed</b></td><td style='word-break: normal'>0</td></tr><tr><td style='word-break: normal'><b>Objects inserted</b></td><td style='word-break: normal'>0</td></tr><tr><td style='word-break: normal'><b>Objects updated</b></td><td style='word-break: normal'>0</td></tr><tr><td style='word-break: normal'><b>Objects not modified</b></td><td style='word-break: normal'>0</td></tr><tr><td style='word-break: normal'><b>Objects terminated</b></td><td style='word-break: normal'>0</td></tr><tr><td style='word-break: normal'><b>Total issues</b></td><td style='word-break: normal'>0</td></tr><tr><td colspan='2' style='text-align: center'><b>Activity Parameters</b></td></tr><tr><td><b>Source Name</b></td><td style='word-break: normal'>standard attributes</td></tr><tr><td><b>Classification By</b></td><td style='word-break: normal'>CLS</td></tr><tr><td><b>Terminate Missing Tags</b></td><td style='word-break: normal'>undefined</td></tr><tr><td><b>Terminate Attributes</b></td><td style='word-break: normal'>empty</td></tr></tbody></table>",
                "Created": {
                    "Name": "PIM360",
                    "Job": "ETL Import"
                }
            }
        ]
    }
]
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
| **200** |Matching item has been found and successfully returned.|
| **401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**500** |Internal Server Error.|


