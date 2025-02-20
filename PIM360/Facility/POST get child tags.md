# POST /facility-explorer/leaf

## Description
Gets child tags for a given facility explorer parent item.

## Required Capabilities
* CanUseAPI
* CanSeeAllPages
* CanSeeFacilityExplorer

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **options** (required) (body) JSON object containing the details of the parent tag to retrieve children for.

## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/facility-explorer/leaf' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
    "facID": "TKF",
    "skip": 0,
    "id": "fvkjqq8TRzyCU5zE4uWW_A1724117626954"

}'
```

## Response Body
JSON object with a `rows` array, where each object in the array is a row in the facility explorer result. Each API call returns 200 rows at a time, the `fetchMore` property in the response indicates if there are more records available. If more records are available, call the API again but increase the `skip` parameter by increments of 200 until there are no more records available.

## Example Response
```JSON
{
    "rows": [
        {
            "id": "tOcUlYvGQ3-YeeUdXcquOA1724115393858",
            "Hdl": "tOcUlYvGQ3-YeeUdXcquOA",
            "ID": "1",
            "FacID": "TKF",
            "ObjType": "TAGGED_ITEM",
            "HasChildren": 0,
            "Completeness": 30.43,
            "Completeness_2": 30.43,
            "y6b-Bxk1S1KbPG-WEjwsBQ": "<div class='icon-TAG' title='TAG'><span class='icon-text'>1</span></div>"
        },
        {
            "id": "x7HdNGrfTS6GWN2p5pC7KA1724115393858",
            "Hdl": "x7HdNGrfTS6GWN2p5pC7KA",
            "ID": "100",
            "FacID": "TKF",
            "ObjType": "TAGGED_ITEM",
            "HasChildren": 0,
            "Completeness": 30.43,
            "Completeness_2": 30.43,
            "y6b-Bxk1S1KbPG-WEjwsBQ": "<div class='icon-TAG' title='TAG'><span class='icon-text'>100</span></div>"
        }
    ],
    "fetchMore": true
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Query has been successfully submitted and returned.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**500** |Internal Server Error.|


