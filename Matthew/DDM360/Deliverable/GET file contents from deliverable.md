# GET /deliverables/{delHdl}/files/{fileHdl}/content

## Description
Gets the content of a file by the file handle. This is the same functionality as `GET /documents/{docHdl}/revisions/{revHdl}/versions/{verHdl}/files/{fileHdl}/content` but with less information required to get the file

## Required Capabilities
* CanUseAPI
* CanViewDocument

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **delHdl** (required) (path) The handle of the deliverable.

* **fileHdl** (required) (path) The handle of the file.

* **action** (query) Optionally get the HTML to render the forgeviewer for this file by specifying "forgeview" as the action.


## Example Request
```
curl --location 'https://{{systemName}}.ddm360.io/api/deliverables/XaVlSbewT7qLr53fgCtVgw/files/v8JNBCMdR8--dFZNPoiq3g/content' \
--header 'Authorization: ••••••'
```

## Response Body
The binary data of the file, or HTML page for forgeviewer (if "forgeview" is specified as the action).

## Example Response
File stream/HTML.

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Matching item has been found and successfully returned.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**404**| Requested item can't be found. Check that the handle has been provided and is correct.|
|**500** |Internal Server Error.|


