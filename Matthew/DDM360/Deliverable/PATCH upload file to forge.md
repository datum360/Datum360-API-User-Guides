# PATCH /deliverables/{delHdl}/files/{fileHdl}/forgeupload

## Description
Submit a file for processing to BIM360/ACC to make it viewable in the DDM360 viewer

## Required Capabilities
* CanUseAPI
* CanSubmitForge
## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **delHdl** (required) (path) Handle of the deliverable to use

* **fileHdl** (required) (path) Handle of the file to submit


## Example Request
```
curl --location --request PATCH 'https://{{systemName}}.ddm360.io/api/deliverables/XaVlSbewT7qLr53fgCtVgw/files/v8JNBCMdR8--dFZNPoiq3g/forgeupload' \
--header 'Authorization: ••••••'
```

## Response Body
JSON object with the response from the upload.

## Example Response
```JSON
{
    "fileContents": {
        "fileObj": {
            "hdl": "v8JNBCMdR8--dFZNPoiq3g",
            "origName": "TKF-NEE-10001-E-M2D-017.dwg",
            "checksum": {
                "checksumType": "MD5",
                "checksumValue": "e484766f293d60550a050d7e57763dd7",
                "_id": "66d93e321e5bbd7ce895b7dd"
            },
            "fileExtension": "dwg",
            "size": 607824,
            "created": {
                "userHdl": "HwiX1yRxSVqzzGpHRg_q5w",
                "name": "Test Runner",
                "job": "Automated Tester",
                "dateTime": "2024-09-05T05:14:26.609Z",
                "_id": "66d93e321e5bbd7ce895b7de"
            },
            "path": "system-name-ddm360/ff6402c7-6048-4711-84aa-0e0b8e370c05",
            "objectId": "ff6402c7-6048-4711-84aa-0e0b8e370c05",
            "_id": "66d93e321e5bbd7ce895b7dc",
            "derivativeSrc": "bim360docs",
            "forgeId": "dXJuOmFkc2sud2lwZW1lYTpmcy5maWxlOnZmLnZkUl9RRmJSUmQ2cTl2TlRQanFJV2c_dmVyc2lvbj02"
        }
    },
    "upload": "dXJuOmFkc2sud2lwZW1lYTpmcy5maWxlOnZmLnZkUl9RRmJSUmQ2cTl2TlRQanFJV2c_dmVyc2lvbj03",
    "setForgeId": {
        "hdl": "v8JNBCMdR8--dFZNPoiq3g",
        "origName": "TKF-NEE-10001-E-M2D-017.dwg",
        "checksum": {
            "checksumType": "MD5",
            "checksumValue": "e484766f293d60550a050d7e57763dd7",
            "_id": "66d93e321e5bbd7ce895b7dd"
        },
        "fileExtension": "dwg",
        "size": 607824,
        "created": {
            "userHdl": "HwiX1yRxSVqzzGpHRg_q5w",
            "name": "Test Runner",
            "job": "Automated Tester",
            "dateTime": "2024-09-05T05:14:26.609Z",
            "_id": "66d93e321e5bbd7ce895b7de"
        },
        "path": "{{systemName}}-ddm360/ff6402c7-6048-4711-84aa-0e0b8e370c05",
        "objectId": "ff6402c7-6048-4711-84aa-0e0b8e370c05",
        "_id": "66d93e321e5bbd7ce895b7dc",
        "derivativeSrc": "bim360docs",
        "forgeId": "dXJuOmFkc2sud2lwZW1lYTpmcy5maWxlOnZmLnZkUl9RRmJSUmQ2cTl2TlRQanFJV2c_dmVyc2lvbj03"
    }
}
```

## Response Status Codes
**200** Matching item has been found and successfully submitted
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


