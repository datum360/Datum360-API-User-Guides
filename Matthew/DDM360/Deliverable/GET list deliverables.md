# GET /deliverables

## Description
List all deliverables in DDM360

## Required Capabilities
* CanUseAPI
* CanViewDeliverables

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
The below parameters can be used to filter the deliverables returned

* **eicNumber** (query string) The EIC to get deliverables from

* **docId** (query string) The PIM360 Document ID to match to

* **facId** (query string) Get deliverables from this facility

* **pageSize** (query string) The maximum number of deliverables to return. Default and maximum of 200

* **page** (query string) Skip entries in multiples of page size to return the next set of deliverables


## Example Request
```
curl --location 'https://{{systemName}}.ddm360.io/api/deliverables' \
--header 'Authorization: ••••••'
```

## Response Body
JSON object containing an array `list` where each object in the array is a deliverable. `hasMore` indicates whether there are more deliverables to fetch on the next page. `@nextLink` provides a URL to use to get the next batch

## Example Response
```JSON
{
    "list": [
        {
            "_id": "66d903a41e5bbd7ce895b6c1",
            "hdl": "ek14n714RiOKPcyeyvwm6A",
            "eicHdl": "XYSp3hn0TDuJV-NX6MrTBQ",
            "personResponsible": "MF",
            "pimDocHdl": "O3omyFcTQfWykgsnUqDcSg",
            "pimDocId": "DOC-001",
            "pimFacId": "TKF",
            "revisionName": "1",
            "dueDate": "2024-09-05T00:00:00.000Z",
            "closed": false,
            "created": {
                "userHdl": "HwiX1yRxSVqzzGpHRg_q5w",
                "name": "Test Runner",
                "job": "Automated Tester",
                "dateTime": "2024-09-05T01:04:36.207Z",
                "_id": "66d903a41e5bbd7ce895b6c2"
            },
            "__v": 0,
            "eicNumber": 1
        },
    ],
    "hasMore": false,
    "@nextLink": "/api/deliverables?pageSize=200&page=1"
}
```

## Response Status Codes
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**500** Internal Server Error


