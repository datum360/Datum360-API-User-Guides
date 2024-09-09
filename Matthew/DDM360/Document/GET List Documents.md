# GET /documents

## Description
Lists a summary of all documents in DDM360. Documents are returned 200 at a time and the `@nextlink` property should point to the next set of documents if available.

## Required Capabilities
* CanUseAPI
* CanViewDocument

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters



## Example Request
```
curl --location 'https://{{systemName}}.ddm360.io/api/documents' \
--header 'Authorization: ••••••'
```

## Response Body
JSON object containing an array `list` where each object in the array is a document in DDM360

## Example Response
```JSON
{
    "list": [
        {
            "_id": "66d7b7e707fbb95949d3352e",
            "hdl": "Pr__5rkHTp2Us5fyT7uy6w",
            "pimDocId": "DOC-001",
            "pimFacId": "TKF"
        }
    ],
    "@nextLink": "TODO"
}
```

## Response Status Codes
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


