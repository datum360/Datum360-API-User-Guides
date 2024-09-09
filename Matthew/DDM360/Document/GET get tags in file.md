# GET /documents/{docHdl}/revisions/{revHdl}/versions/{verHdl}/files/{fileHdl}/tags

## Description
Get all tags that have been associated with the provided file

## Required Capabilities
* CanUseAPI
* CanViewDocument
## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **docHdl** (required) (path) The handle of the document to use

* **revHdl** (required) (path) The handle of the revision to use

* **verHdl** (required) (path) The handle of the version to use. Defaults to the current version

* **fileHdl** (required) (path) The handle of the file to use


## Example Request
```
curl --location 'https://{{systemName}}.ddm360.io/api/documents/ANZ1GrhpTUixLsuBRmwxHg/revisions/ixW69Ok-QQ-IKmD_Dn-VKg/versions/xgBW4ta4SA2cvVdecy2XjA/files/EwmPrdfJQuu3SgEA_Qju-Q/tags' \
--header 'Authorization: ••••••'
```

## Response Body
JSON array of objects, where each object in the array is a tag on the file. A tag can be linked to multiple components in the file, in this case the `components` array contains an object for each component that the tag is linked to.

## Example Response
```JSON
[
    {
        "hdl": "JUm-gPdmQnyecS-HpWzl9w",
        "tagId": "TK-1004",
        "facId": "TKF-1004",
        "pimDetails": {},
        "components": [
            {
                "text": "TK-1004",
                "objectId": [
                    340
                ],
                "_id": "66d90ad71e5bbd7ce895b70b"
            }
        ]
    }
]
```

## Response Status Codes
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handles have been provided and are correct.
**500** Internal Server Error


