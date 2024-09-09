# PATCH /documents/{docHdl}/revisions/{revHdl}/version/{verHdl}

## Description
Allows the specified document version to be updated so that it can point to a different file that has already been uploaded to DDM360.

## Required Capabilities
* CanUseAPI
* CanUploadFile

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **docHdl** (required) (path) The handle of the document to update

* **revHdl** (required) (path) The handle of the revision to update

* **verHdl** (required) (path) The handle of the version to update

* **version** (required) (body) JSON object containing a property `modelFileHdl` and the handle of the file to use.

## Example Request
```
curl --location --request PATCH 'https://{{systemName}}.ddm360.io/api/documents/Pr__5rkHTp2Us5fyT7uy6w/revisions/AV2HCw2nQ36hrAGo5o6Iog/version/yPiM-dcwSUych7-EfefOAQ' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
    "modelFileHdl": "OAT1FNzzQPG2jL-hgBml7g"
}'
```

## Response Body
JSON object containing the newly updated version object

## Example Response
```JSON
{
    "hdl": "yPiM-dcwSUych7-EfefOAQ",
    "versionNumber": 1,
    "created": {
        "userHdl": "HwiX1yRxSVqzzGpHRg_q5w",
        "name": "Test Runner",
        "job": "Automated Tester",
        "dateTime": "2024-09-04T01:29:11.032Z",
        "_id": "66d7b7e707fbb95949d33533"
    },
    "files": [
        {
            "hdl": "OAT1FNzzQPG2jL-hgBml7g",
            "origName": "TKF-NEE-10001-E-M2D-017.dwg",
            "checksum": {
                "checksumType": "MD5",
                "checksumValue": "e484766f293d60550a050d7e57763dd7",
                "_id": "66d7b7e707fbb95949d33535"
            },
            "fileExtension": "dwg",
            "size": 607824,
            "created": {
                "userHdl": "HwiX1yRxSVqzzGpHRg_q5w",
                "name": "Test Runner",
                "job": "Automated Tester",
                "dateTime": "2024-09-04T01:29:11.199Z",
                "_id": "66d7b7e707fbb95949d33536"
            },
            "path": "dap-demo-ddm360/171be990-656e-4223-9292-0084553fe612",
            "objectId": "171be990-656e-4223-9292-0084553fe612",
            "_id": "66d7b7e707fbb95949d33534",
            "derivativeSrc": "bim360docs",
            "forgeId": "dXJuOmSkc2sud2lwZW1lZTpmcy5maWxgOnZmLnZkUl9RRmJSUmQ4cTl2TlRQanFJV2d_dmVyc2lvbj0x"
        }
    ],
    "_id": "66d7b7e707fbb95949d33532",
    "modelFileHdl": "OAT1FNzzQPG2jL-hgBml7g"
}
```

## Response Status Codes
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


