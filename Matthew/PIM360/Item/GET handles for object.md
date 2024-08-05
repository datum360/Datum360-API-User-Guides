# GET /objects/{type}/handles

## Description
Finds all objects of the specified type that have the attribute value that is provided and returns their handles. For example find all tagged items that have the facility of "CASTOR". Note that the attribute values do need to have been published to search on them.

## Required Capabilities

* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters

**type** (required) (path) Item type to query on. Can be one of:  
* TAGGED_ITEM
* DOCUMENT
* EQUIPMENT_ITEM
* EQUIPMENT_MODEL

**name** (required) (query string) The name of the attribute to query on. Should be URL encoded.

**value** (required) (query string) The value of the attribute to query on. Should be URL encoded.

**eic** (query string) The handle of the EIC to search in, otherwise Active Data will be used

**skip** (query string) Used for paging, the number of entries to skip

**limit** (query string) Used for paging, the number of entries to return (maximum/default of 200)

## Example Request

`
curl --location 'https://{{SystemName}}.pim360.io/api/objects/TAGGED_ITEM/handles?name=facility&value=CASTOR&eic=XYSp3hn0TDuJV-NX6MrTBQ' \
--header 'Authorization: ******'
`

## Response Body
Returns an array of handles for items that match the provided query. If no matching items are found then an empty array will be returned with a successful statuss code

## Example Response
```JSON
["-W4UaC1IS5K5FCmfh5PbSQ"]
```

## Response Status Codes
**200** Matching items have been successfully found and returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired


