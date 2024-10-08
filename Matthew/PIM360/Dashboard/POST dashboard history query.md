# POST /dashboard/query/history

## Description
Submit a query for a historical trend dashboard widget.

## Required Capabilities
* CanUseAPI
* CanSeeAllPages
* CanSeeDashboard

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **body** (required) (body)


## Example Request


## Response Body


## Example Response


## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200**| Matching item has been found and successfully returned.|
|**401**| Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**404**| Requested item can't be found. Check that the handle has been provided and is correct.|
|**500**| Internal Server Error.|


