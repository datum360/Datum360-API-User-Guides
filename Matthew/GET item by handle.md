# GET /objects/{type}/{{handle}}

## Description
Get an item of the specified type with the specified handle

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

**handle** (required) (path) The handle of the item to get

**eic** (optional) (query string) Handle of the EIC to search in, otherwise Active Data

## Example Request
`
curl --location 'https://{{systemName}}.pim360.io/api/objects/TAGGED_ITEM/-W4UaC1IS5K5FCmfh5PbSQ?eic=XYSp3hn0TDuJV-NX6MrTBQ' \
--header 'Authorization: ******'
`

## Response Body


## Example Response


## Response Status Codes
**200** 
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired


