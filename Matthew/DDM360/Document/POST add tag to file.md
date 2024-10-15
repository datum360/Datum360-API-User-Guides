# POST /documents/{docHdl}/revisions/{revHdl}/versions/{verHdl}/files/{fileHdl}/aliases

## Description
Add one or more tags to components on the specified file.

## Required Capabilities
* CanUseAPI
* CanCreateTagAlias

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **docHdl** (required) (path) The handle of the document.

* **revHdl** (required) (path) The handle of the revision.

* **verHdl** (required) (path) The handle of the version. Defaults to the current version

* **fileHdl** (required) (path) The handle of the file.

* **tagAliasInfo** (required) (body) JSON object describing which tags to the file and which component they are associated with. Multiple tags can be associated at once by adding multiple entries in the `tagAliases` array.
    * `locationType` set to `OBJECTID`
    * `tagAliases` is an array of tags to add to the file. For each tag, add an object with:
        * `components` an array of components to associate the tag to.
        * `tags` an array of tags to add. Must include tag ID and facility.

## Example Request
```
curl --location 'https://{{systemName}}.ddm360.io/api/documents/ANZ1GrhpTUixLsuBRmwxHg/revisions/ixW69Ok-QQ-IKmD_Dn-VKg/versions/xgBW4ta4SA2cvVdecy2XjA/files/EwmPrdfJQuu3SgEA_Qju-Q/aliases' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
    "locationType": "OBJECTID",
    "tagAliases": [
        {
            "components": [
                {
                    "text": "TK-1003",
                    "objectId": [
                        343
                    ]
                }
            ],
            "tags": [
                {
                    "tagId": "TK-1003",
                    "facId": "TKF"
                }
            ]
        }
    ]
}'
```

## Response Body
JSON object confirming the details of the newly added tag alias.

## Example Response
```JSON
{
    "docHdl": "ANZ1GrhpTUixLsuBRmwxHg",
    "revHdl": "ixW69Ok-QQ-IKmD_Dn-VKg",
    "verHdl": "xgBW4ta4SA2cvVdecy2XjA",
    "fileHdl": "EwmPrdfJQuu3SgEA_Qju-Q",
    "locationType": "OBJECTID",
    "tagAliases": [
        {
            "components": [
                {
                    "text": "TK-1003",
                    "objectId": [
                        343
                    ]
                }
            ],
            "tags": [
                {
                    "tagId": "TK-1003",
                    "facId": "TKF",
                    "tagHdl": "7aEGOcm-TjGDVUD1kQ7pUg",
                    "created": false
                }
            ],
            "aliasHdl": "aS8SteroS_SHuWkKxvhsHw",
            "created": true
        }
    ],
    "userInfo": {
        "userHdl": "HwiX1yRxSVqzzGpHRg_q5w",
        "name": "Test Runner",
        "job": "Automated Tester"
    }
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
**201** |Tag alias has been successfully created.
**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.
**404** |Requested item can't be found. Check that the handles have been provided and are correct.
**500** |Internal Server Error. Check that all required items have been provided in the request body.


