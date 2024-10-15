# POST /tags/query

## Description
Gets details of a tag using the associated tag alias in DDM360.

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **data** (required) (body) JSON object describing the query to get associated tags. Properties are:
    * **fileHdl** (required) The handle of the DDM360 file to query.
    * **locationType** (required) How to find the required tag, options are:
        * NONE
        * OBJECTID
        * XYCOORDS
    * **query** (required) Object describing what data to use to find the tag. Object properties depends on the selected locationType.
        * **objectId** If "OBJECTID" has been specified as the locationType, then this should be an array of IDs of items in the file to search for related tags.
        * **xCoord** If "XYCOORDS" has been specified as the locationType, then this should be the x Coordinate of the item in the file to search for related tags.
        * **yCoord** If "XYCOORDS" has been specified as the locationType, then this should be the y Coordinate of the item in the file to search for related tags.
        * **text** If "NONE" has been specified as the locationType, then this should be the text to search for in the file that has an associated tag.


## Example Request
```
curl --location 'https://{{systemName}}.ddm360.io/api/tags/query' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
    "fileHdl": "W8SlBQUlQqyS_Rwg4aurew",
    "locationType": "OBJECTID",
    "query": {
        "objectId": [
            3220
        ]
    }
}'
```

## Response Body
JSON array of objects where each object is a tag that matches the submitted query.

## Example Response
```JSON
[
    {
        "hdl": "hOMGshnmSL6puuKoAtn0EA",
        "tagId": "TK-1004",
        "facId": "TKF"
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


