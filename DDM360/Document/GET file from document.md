# GET /documents/{docHdl}/revisions/{revHdl}/versions/{verHdl}/files/{fileHdl}/content

## Description
Gets the content of a file specified by the file handle. This is the same functionality as `GET /deliverables/{delHdl}/files/{fileHdl}/content`, but this API should be used if you currently don't know or have access to the deliverable handle.

## Required Capabilities
* CanUseAPI
* CanViewDocument

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **docHdl** (required) (path) The handle of the document.

* **revHdl** (required) (path) The handle of the revision.

* **verHdl** (required) (path) The handle of the version.

* **fileHdl** (required) (path) The handle of the file.

* **action** (query) Optionally get the HTML to render the forgeviewer for this file by specifying "forgeview" as the action.

## Example Request
```
curl --location 'https://{{systemName}}.ddm360.io/api/documents/Pr__5rkHTp2Us5fyT7uy6w/revisions/AV2HCw2nQ36hrAGo5o6Iog/versions/yPiM-dcwSUych7-EfefOAQ/files/OAT1FNzzQPG2jL-hgBml7g/content' \
--header 'Authorization: ••••••'
```

## Response Body
The binary data of the file requested.

## Example Response
File stream/HTML.

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
**200** |Matching item has been found and successfully returned.
**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.
**404** |Requested item can't be found. Check that the handle has been provided and is correct.
**500** |Internal Server Error.


