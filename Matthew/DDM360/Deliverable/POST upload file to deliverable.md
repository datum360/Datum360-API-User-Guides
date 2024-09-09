# POST /deliverables/{delHdl}/files

## Description
Upload one or more files to a deliverable in DDM360. This will automatically create a new version of the deliverable.

## Required Capabilities
* CanUseAPI
* CanUploadFile

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **delHdl** (required) (path) Handle of the deliverable to upload to.

* **file** (required) (formData) The file to upload


## Example Request
```
curl --location 'https://{{systemName}}.ddm360.io/api/deliverables/XaVlSbewT7qLr53fgCtVgw/files' \
--header 'Authorization: ••••••' \
--form 'file=@"postman-cloud:///1ef6b45b-63b2-46a0-b3e0-17edb0056ed1"'
```

## Response Body
JSON object describing the new version of the deliverable that has been created

## Example Response
```JSON
{
    "documentHdl": "ANZ1GrhpTUixLsuBRmwxHg",
    "pimDocHdl": "O3omyFcTQfWykgsnUqDcSg",
    "revisionHdl": "DqD5jsLkQqC_0r7-wUuNhw",
    "versionHdl": "e9qE6UdtRIGbF4rzdTZ-tQ",
    "fileHdls": [
        "v8JNBCMdR8--dFZNPoiq3g"
    ],
    "fileExtensions": [
        "dwg"
    ],
    "fileNames": [
        "TKF-NEE-10001-E-M2D-017.dwg"
    ]
}
```

## Response Status Codes
**200** File has been sucessfully uploaded to the deliverable
**400** Bad request. Check that file has been added to the request
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


