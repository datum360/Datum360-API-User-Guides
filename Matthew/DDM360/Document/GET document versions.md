# GET /documents/{docHdl}/revisions/{revHdl}/versions

## Description
Gets all versions for a specific revision of a specific document.

## Required Capabilities
* CanUseAPI
* CanViewDocument
## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **docHdl** (required) (path) The handle of the document.

* **revHdl** (required) (path) The handle of the revision.

## Example Request
```
curl --location 'https://{{systemName}}.ddm360.io/api/documents/Pr__5rkHTp2Us5fyT7uy6w/revisions/AV2HCw2nQ36hrAGo5o6Iog/versions' \
--header 'Authorization: ••••••'
```

## Response Body
JSON array containing all of the versions for the requested document revision.

## Example Response
```JSON
[
    {
        "docHdl": "Pr__5rkHTp2Us5fyT7uy6w",
        "revHdl": "AV2HCw2nQ36hrAGo5o6Iog",
        "verHdl": "yPiM-dcwSUych7-EfefOAQ",
        "verNo": 1,
        "isCurrent": true,
        "created": {
            "user": "Test Runner",
            "dateTime": "2024-09-04T01:29:11.032Z"
        },
        "file": {
            "name": "TKF-NEE-10001-E-M2D-017.dwg",
            "hdl": "OAT1FNzzQPG2jL-hgBml7g",
            "forgeId": "dXJuOmFkc2sud2lwZW1lYTpmcy5maWxlOnZmLnZkUl9RRmJSUmQ2cTl2TlRQanFJV2c_dmVyc2lvbj0x"
        },
        "files": [
            {
                "name": "TKF-NEE-10001-E-M2D-017.dwg",
                "hdl": "OAT1FNzzQPG2jL-hgBml7g",
                "forgeId": "dXJuOmFkc2sud2lwZW1lYTpmcy5maWxlOnZmLnZkUl9RRmJSUmQ2cTl2TlRQanFJV2c_dmVyc2lvbj0x"
            }
        ]
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


