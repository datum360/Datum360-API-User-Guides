# POST /file

## Description
Upload a file, returning handle of file, eg. for submitting import activities.

## Required Capabilities
* CanUseAPI
* CanUploadFiles
## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **upfile** (required) (form data) Stream of the file to upload.


## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/file' \
--header 'Authorization: ••••••' \
--form 'upfile=@"postman-cloud:///1ef53a5e-ffba-4390-99c0-9541a8171f33"'
```

## Response Body
Details of the uploaded file including the handle of the file in PIM360.

## Example Response
```JSON
{
    "Path": "system-name-pim360/c4989ebe-874e-415c-afac-f384e31376c3.xlsx",
    "Hdl": "xJievodOQVyvrPOE4xN2ww",
    "ModifiedName": "c4989ebe-874e-415c-afac-f384e31376c3.xlsx",
    "OrigName": "tag load.xlsx",
    "Location": "(deprecated)",
    "Type": "xlsx",
    "Size": 8875,
    "Created": {
        "Hdl": "HwiX1yRxSVqzzGpHRg_q5w",
        "Name": "User Name",
        "Job": "Autodesk",
        "Ts": "2024-08-13T05:44:16.480Z"
    },
    "_id": "66baf2b084bb1afbb3cf57a1"
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |File has been successfully uploaded.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**500** |Internal Server Error.|


