# POST /domains/seed

## Description
Create a new class library/domain based on the contents of another class library/domain

## Required Capabilities
* CanUseAPI
* CanCreateDomain
## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **object** (required) (body) JSON object containing the details for the new Class Library and which one to copy from. The required properties are:
    * hdl - The handle of the Class Library to copy from
    * name - The name for the new Class Library
    * label - The value of the label for the new Class Library
    * copyContextAndCore - boolean value, if true then context and core attributes are copied over from the base Class Library

## Example Request
```
curl --location 'https://{{systemName}}.cls360.io/api/domains/seed' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
    "hdl": "MAKZvz1eTQSvaQdvlHsYNw",
    "name": "API Class Library",
    "label": "API Class Library",
    "copyContextAndCore": true
}'
```

## Response Body
JSON object containing the handle of the newly created Class Library

## Example Response
```JSON
{
    "hdl": "LF4zzSU8TNKvTiFmA3wDfw"
}
```

## Response Status Codes
**200** Class Library has been successfully created
**400** Bad request. Make sure that all required parameters are provided. Error message will detail missing parameters.
Check that the source class library handle provided is correct.
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


