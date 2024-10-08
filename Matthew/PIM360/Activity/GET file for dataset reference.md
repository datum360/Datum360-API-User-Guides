# GET /etl_queue/activities/reference/{actRef}/data

## Description
Gets the output file associated with the latest run of the activity for the provided dataset reference.

## Required Capabilities
* CanUseAPI
* CanSeeQueue


## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **actRef** (required) (path) The dataset reference to get a file for.

## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/etl_queue/activities/reference/export/data' \
--header 'Authorization: ••••••'
```

## Response Body
The output file associated with the activity. For example if the activity was an export activity to an Excel file then the contents of the response will be the Excel file.

## Example Response


## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Matching item has been found and successfully returned.|
|**401**| Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**404** |Requested item can't be found. Check that the handle has been provided and is correct.|
|**500** |Internal Server Error.|


