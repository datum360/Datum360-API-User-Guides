# PATCH /document/{docHdl}

## Description
Updates a document specified by the provided handle. Currently only allows changes to set the currentRevisionHdl attribute

## Required Capabilities
* CanUseAPI
* CanUpdateDocument
## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **docHdl** (required) (path) The handle of the document to update

* **updates** (required) (body) JSON object to set the currentRevisionHdl attribute


## Example Request
```
curl --location --request PATCH 'https://{{systemName}}.ddm360.io/api/documents/Pr__5rkHTp2Us5fyT7uy6w' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
    "currentRevisionHdl": "AV2HCw2nQ36hrAGo5o6Iog"
}'
```

## Response Body
JSON object containing the updated currentRevisonHdl. If an empty object is returned then that means that the update has not been sucessful. Make sure that the attribute to update is `currentRevisionHdl`.

## Example Response
```JSON
{
    "currentRevisionHdl": "AV2HCw2nQ36hrAGo5o6Iog"
}
```

## Response Status Codes
**200** Matching item has been found and successfully updated
**400** Bad request. Check that the document handle is correct
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided.
**500** Internal Server Error


