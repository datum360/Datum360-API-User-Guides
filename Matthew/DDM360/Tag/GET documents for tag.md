# GET /tags/{facId}/{tagId}/documents

## Description
Gets all documents that the provided tag is present in.

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **facId** (required) (path) The name of the facility that the tag belongs to.

* **tagId** (required) (path) The name of the tag.


## Example Request
```
curl --location 'https://{{systemName}}.ddm360.io/api/tags/TKF/TK-1003/documents' \
--header 'Authorization: ••••••'
```

## Response Body
JSON array of objects where each object is a document that the tag appears in.

## Example Response
```JSON
[
    {
        "_id": "66da38e4dbfeb99467e27ef8",
        "hdl": "aHvYXXw_TlOKnXkXhaI4Sg",
        "pimDocHdl": "O3omyFcTQfWykgsnUqDcSg",
        "pimDocId": "DOC-001",
        "pimFacId": "TKF",
        "currentRevisionHdl": null,
        "created": {
            "userHdl": "HwiX1yRxSVqzzGpHRg_q5w",
            "name": "Test Runner",
            "job": "Automated Tester",
            "dateTime": "2024-09-05T23:04:04.187Z",
            "_id": "66da38e4dbfeb99467e27ef9"
        },
        "revisions": [
            {
                "hdl": "oQ_dtNfUSb6U15x_W1jSew",
                "deliverableHdl": "X-VP8zBAQAKBvG8cKOR1Eg",
                "revisionName": "1",
                "created": {
                    "userHdl": "HwiX1yRxSVqzzGpHRg_q5w",
                    "name": "Test Runner",
                    "job": "Automated Tester",
                    "dateTime": "2024-09-05T23:04:04.188Z",
                    "_id": "66da38e4dbfeb99467e27efb"
                },
                "versions": [
                    {
                        "hdl": "c54WEcw1TB65VQMfmAhutg",
                        "versionNumber": 1,
                        "created": {
                            "userHdl": "HwiX1yRxSVqzzGpHRg_q5w",
                            "name": "Test Runner",
                            "job": "Automated Tester",
                            "dateTime": "2024-09-05T23:04:04.190Z",
                            "_id": "66da38e4dbfeb99467e27efd"
                        },
                        "files": [
                            {
                                "hdl": "YP_4TNTGSUiAQYbs8t1uIw",
                                "origName": "TKF-NEE-10001-E-M2D-017.dwg",
                                "checksum": {
                                    "checksumType": "MD5",
                                    "checksumValue": "e484766f293d60550a050d7e57763dd7",
                                    "_id": "66da38e4dbfeb99467e27eff"
                                },
                                "fileExtension": "dwg",
                                "size": 607824,
                                "created": {
                                    "userHdl": "HwiX1yRxSVqzzGpHRg_q5w",
                                    "name": "Test Runner",
                                    "job": "Automated Tester",
                                    "dateTime": "2024-09-05T23:04:04.326Z",
                                    "_id": "66da38e4dbfeb99467e27f00"
                                },
                                "path": "{{systemName}}-ddm360/b6ad703a-90e7-4f41-b51e-ab122e6aba98",
                                "objectId": "b6ad703a-90e7-4f41-b51e-ab122e6aba98",
                                "_id": "66da38e4dbfeb99467e27efe",
                                "derivativeSrc": "bim360docs",
                                "forgeId": "dXJuOmFkc2sud2lwZW1lYTpmcy5maWxlOnZmLnZkUl9RRmJSUmQ2cTl2TlRQanFJV2c_dmVyc2lvbj05"
                            }
                        ],
                        "_id": "66da38e4dbfeb99467e27efc"
                    }
                ],
                "_id": "66da38e4dbfeb99467e27efa",
                "currentVersionHdl": "c54WEcw1TB65VQMfmAhutg"
            }
        ],
        "__v": 0
    }
]
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
**200** |Matching item has been found and successfully returned.
**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.
**404** |Requested item can't be found. Check that the handle has been provided and is correct.
**500** |Internal Server Error.


