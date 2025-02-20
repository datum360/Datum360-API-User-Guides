

## Description


## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters



## Example Request


## Response Body


## Example Response


## Response Status Codes
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


