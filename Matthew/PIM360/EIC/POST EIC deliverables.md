# POST /eic/{eicHdl}/deliverables

## Description
Creates a new deliverable on the provided EIC. Multiple deliverables can be created in the same request.

## Required Capabilities
* CanUseAPI
* CanGenerateDCF
* CanSeeEicExplorer
* CanSeeAllPages

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* eicHdl (required) (path) Handle of the EIC to create the deliverable on.
* query (body) An array containing the deliverable(s) to create. Each object requires the deliverable ID/name and a due date, the due date must be in the format `YYYY-MM-DD`. Responsible is an optional property on each object.


## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/eic/XYSp3hn0TDuJV-NX6MrTBQ/deliverables' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '[
    {
        "ID": "New Deliverable",
        "Responsible": "User Name",
        "DueDate": "2024-08-04"
    }
]'
```

## Response Body
A JSON object containing `Status` and `Deliverables` properties. `Status` shows if the deliverables were created successfully. `Deliverables` is an array of objects, each object holding details of the newly created deliverables.

## Example Response
Successful Response:

```JSON
{
    "Status": "Created",
    "Deliverables": [
        {
            "EICHdl": "XYSp3hn0TDuJV-NX6MrTBQ",
            "Hdl": "sD2fIENfQnuYikfOdgNoLg",
            "ID": "New Deliverable",
            "Responsible": "User Name",
            "DueDate": "2024-08-04T00:00:00.000Z"
        }
    ]
}
```

Invalid Date Format:

```JSON
{
    "Status": "NOTOK",
    "Err": "Sorry, the entered 'Due Date' could not be parsed. It should be in 'YYYY-MM-DD' format."
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Deliverable has been successfully created. **Note:** if an invalid date format for `DueDate` has been provided, the API will still return a `200` status code, but there will be an error message in the response body and the deliverable will not have been created.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**404** |Requested item can't be found. Check that the handle has been provided and is correct.|
|**409** |Conflict. A deliverable with the provided ID already exists.|
|**500** |Internal Server Error.|


