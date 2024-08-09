# POST /eic/list

## Description
Allows EICs to be created or updated if a handle is provided.

## Required Capabilities
* CanUseAPI
* CanSeeEicExplorer
* CanSeeAllPages

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
To create: A JSON object with an `attrs` array, with objects for each EIC attribute. These attributes should be the same attributes that are present when creating an EIC through the UI. Note that for the EIC class attribute, the value should be the handle of the class rather than the name.

To update: A JSON object with a `hdl` property, containing the handle of the eic to update. As well as the `attrs` array, with an object for each attribute on the EIC to update.

## Example Request
To Create:
`
curl --location 'https://{{systemName}}.pim360.io/api/eic/list' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
  "attrs": [
    {
      "name": "XO19QrZgSjqurYdGbfMvdA",
      "value": "PSpaWdpVT_uYOz4HsRekkw"
    },
    {
      "name": "crBhwt7JTAGGZNHDeUucVg",
      "value": "OPEN"
    },
    {
      "name": "vQPCnBpNRwSAjFbTbu_vxw",
      "value": "API EIC"
    }
  ]
}'
`

To update:
`
{
  "hdl": "gZbXNTq7Tiqf0Oze2VId1w",
  "attrs": [
    {
      "name": "vQPCnBpNRwSAjFbTbu_vxw",
      "value": "Updated description"
    },
    {
      "name": "XO19QrZgSjqurYdGbfMvdA",
      "value": "PSpaWdpVT_uYOz4HsRekkw"
    }
  ]
}
`

## Response Body
Returns the handle of the EIC that has been created or updated

## Example Response
```JSON
{
    "Hdl": "gZbXNTq7Tiqf0Oze2VId1w"
}
```

## Response Status Codes
**200** Create/Update has been successfully executed

**400** Bad request.
    "You must provide a CLASS attribute and value" When updating an EIC, you must provide the class of the EIC to update as well as any other attributes that are being changed

**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired

**404** Requested item can't be found. Check that the handle has been provided and is correct.

**500** Internal Server Error


