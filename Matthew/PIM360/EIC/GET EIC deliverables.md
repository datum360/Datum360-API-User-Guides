# GET /eic/{eicHdl}/deliverables

## Description
Gets a list of all deliverables that are associated with the provided EIC.

## Required Capabilities
* CanUseAPI
* CanGenerateDCF
* CanSeeEicExplorer
* CanSeeAllPages

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* eicHdl (required) (path) The handle of the EIC to use.


## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/eic/XYSp3hn0TDuJV-NX6MrTBQ/deliverables' \
--header 'Authorization: ••••••'
```

## Response Body
JSON object with a property `Deliverables` containing an array of objects. Each object in the array is a deliverable. Each deliverable lists all of the files that have been loaded against it.

## Example Response
```JSON
{
    "Deliverables": [
        {
            "_id": "667154b3b3c3fadbc520298e",
            "EICHdl": "XYSp3hn0TDuJV-NX6MrTBQ",
            "ID": "DOC-001",
            "Responsible": "MF",
            "DueDate": "2024-06-18T00:00:00.000Z",
            "Hdl": "cY45litXSYqsii46DpcB1A",
            "Type": "DOCUMENT",
            "Files": [
                {
                    "Hdl": "O3omyFcTQfWykgsnUqDcSg",
                    "Name": "DOC-001",
                    "Type": "Document",
                    "Created": {
                        "Hdl": "HwiX1yRxSVqzzGpHRg_q5w",
                        "Name": "User Name",
                        "Job": "Autodesk",
                        "Ts": "2024-07-15T06:19:45.620Z",
                        "ActHdl": "jUxK4dLfTouAI_PqlwVaFw",
                        "SrcHdl": "zyz6EVl3QmiA3Ls5FHDt7w",
                        "EICHdl": "XYSp3hn0TDuJV-NX6MrTBQ"
                    }
                }
            ],
            "Created": {
                "Hdl": "I292TPZ0S2maliDSJ3hrJQ",
                "Name": "User Name",
                "Job": "Autodesk",
                "Ts": "2024-06-18T09:34:43.261Z"
            },
            "ImpCnt": 2,
            "LastImpDate": "2024-07-15T06:19:43.227Z",
            "Class": "architectural engineering - approval certificate",
            "exists": true
        }
    ]
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Matching item has been found and successfully returned.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**500** |Internal Server Error. Check that the provided EIC handle is valid.|


