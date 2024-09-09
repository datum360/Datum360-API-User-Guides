# GET /deliverables/{delHdl}/revision

## Description
Get details of the revison and all associated versions on the deliverable specified

## Required Capabilities
* CanUseAPI
* CanViewDeliverables

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **delHdl** (required) (path) The handle of the deliverable to get revisions for


## Example Request
```
curl --location 'https://{{systemName}}.ddm360.io/api/deliverables/XaVlSbewT7qLr53fgCtVgw/revision' \
--header 'Authorization: ••••••'
```

## Response Body
JSON object describing the revision on the specified deliverable and all versions on that revision

## Example Response
```JSON
{
    "docHdl": "ANZ1GrhpTUixLsuBRmwxHg",
    "revision": {
        "hdl": "DqD5jsLkQqC_0r7-wUuNhw",
        "deliverableHdl": "XaVlSbewT7qLr53fgCtVgw",
        "revisionName": "2",
        "created": {
            "userHdl": "HwiX1yRxSVqzzGpHRg_q5w",
            "name": "Test Runner",
            "job": "Automated Tester",
            "dateTime": "2024-09-05T05:13:25.745Z",
            "_id": "66d93df51e5bbd7ce895b771"
        },
        "versions": [
            {
                "hdl": "TOU0XZx7S8SWMstX1hTP7w",
                "versionNumber": 1,
                "created": {
                    "userHdl": "HwiX1yRxSVqzzGpHRg_q5w",
                    "name": "Test Runner",
                    "job": "Automated Tester",
                    "dateTime": "2024-09-05T05:13:25.746Z",
                    "_id": "66d93df51e5bbd7ce895b773"
                },
                "files": [
                    {
                        "hdl": "wAlZqhBDQ7qrgk4qL6bryA",
                        "origName": "TKF-NEE-10001-E-M2D-017.dwg",
                        "checksum": {
                            "checksumType": "MD5",
                            "checksumValue": "e484766f293d60550a050d7e57763dd7",
                            "_id": "66d93df51e5bbd7ce895b775"
                        },
                        "fileExtension": "dwg",
                        "size": 607824,
                        "created": {
                            "userHdl": "HwiX1yRxSVqzzGpHRg_q5w",
                            "name": "Test Runner",
                            "job": "Automated Tester",
                            "dateTime": "2024-09-05T05:13:25.875Z",
                            "_id": "66d93df51e5bbd7ce895b776"
                        },
                        "path": "dap-demo-ddm360/42b9ece9-774e-410e-83c6-15d90bd3e5ae",
                        "objectId": "42b9ece9-774e-410e-83c6-15d90bd3e5ae",
                        "_id": "66d93df51e5bbd7ce895b774",
                        "derivativeSrc": "bim360docs",
                        "forgeId": "dXJuOmFkc2sud2lwZW1lYTpmcy5maWxlOnZmLnZkUl9RRmJSUmQ2cTl2TlRQanFJV2c_dmVyc2lvbj00"
                    }
                ],
                "_id": "66d93df51e5bbd7ce895b772"
            }
        ],
        "_id": "66d93df51e5bbd7ce895b770",
        "currentVersionHdl": "e9qE6UdtRIGbF4rzdTZ-tQ"
    }
}
```

## Response Status Codes
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle is correct.
**500** Internal Server Error


