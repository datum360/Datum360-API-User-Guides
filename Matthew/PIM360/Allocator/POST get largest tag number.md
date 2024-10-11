# POST /allocator/lastnumerics

## Description
Takes a regular expression that matches a tag number format, a facility and an object type, and returns the largest matching tag number.

## Required Capabilities
* CanUseAPI
* CanLiveTag

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **query** (required) (body) JSON object containing the query to return the correct item number. Object contains properties: 
    * `tag` - Regex pattern to find the matching tag.
    * `facid` - The facility of the item.
    * `type` - The type of item to generate. Can be one of TAGGED_ITEM, DOCUMENT, EQUIPMENT_ITEM, EQUIPMENT_MODEL.


## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/allocator/lastnumerics' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
    "tag": "[A-Z]{2,3}-[0-9]{3}",
    "facid": "TKF",
    "type": "TAGGED_ITEM"
}'
```

## Response Body
JSON object containing the property `tag` which contains the matching item number. If no matching item is found then `null` is returned for the tag.

## Example Response
```JSON
{
    "tag": "BLW-001"
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Matching item has been found and successfully returned.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**500** |Internal Server Error.|


