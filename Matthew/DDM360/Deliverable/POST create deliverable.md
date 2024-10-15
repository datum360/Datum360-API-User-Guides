# POST /deliverables

## Description
Create a new deliverable in DDM360.

## Required Capabilities
* CanUseAPI
* CanCreateDeliverables
## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **deliverable** (required) (body) JSON object describing the deliverable to create. Required parameters are:
    * **eicNumber**: The number of the EIC, in PIM360, that the deliverable exists in.
    * **pimDocId**: The name of the deliverable (the name of the corresponding document in PIM360).
    * **facId**: The name of the facility that the deliverable/document exists in.
    * **revisionName**: Name of the revision for this deliverable.
    * **personResponsible**: Person responsible for this deliverable.
    * **dueDate**: When is this deliverable due. In the format YYYY-MM-DD.


## Example Request
```
curl --location 'https://{{systemName}}.ddm360.io/api/deliverables' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
    "eicNumber": 1,
    "pimDocId": "DOC-001",
    "facId": "TKF",
    "revisionName": "2",
    "personResponsible": "MF",
    "dueDate": "2024-09-05"
}'
```

## Response Body
JSON object containing the handle of the newly created deliverable.

## Example Response
```JSON
{
    "hdl": "XaVlSbewT7qLr53fgCtVgw"
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
**200** |Deliverable has been successfully created.
**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.
**404** |Requested item can't be found. Check that the handle has been provided and is correct.
**500** |Internal Server Error.


