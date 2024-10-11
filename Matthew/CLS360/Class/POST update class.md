# POST /domains/{domHdl}/classes/{clsHdl}

## Description
Update the details of an existing class

## Required Capabilities
* CanUseAPI

* CanUpdateClass

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **domHdl** (required) (path) The handle of the Class Library/Domain to use

* **classHdl** (required) (path) The handle of the class to update

* **class** (required) (body) JSON object containing the new details of the class. To make sure that all required data is provided, it is recommended to run the `GET /domains{domHdl}/classes/{clsHdl}` API first. Then update the response with the new details.


## Example Request
```
curl --location 'https://dap-demo.cls360.io/api/domains/MAKZvz1eTQSvaQdvlHsYNw/classes/_CU46pvVSd-i3KkyPfVkVg' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
    "data": [],
    "checksum": "2b81a3df6cbdb07adf78aac48f6105e075cc66cdc0531aa77a9243691e72d223",
    "version": {
        "Ts": "2024-08-30T03:37:43.931Z",
        "Seed": {
            "Hdl": "rxX_MCitQsiiZH2HWgLAjQ",
            "Number": 874
        },
        "Origin": {
            "Hdl": "rxX_MCitQsiiZH2HWgLAjQ",
            "Number": 44
        }
    },
    "detail": {
        "hdl": "_CU46pvVSd-i3KkyPfVkVg",
        "label": "cabinet",
        "icon": "TAG",
        "key": "_CU46pvVSd-i3KkyPfVkVg",
        "date": "2024-08-30T03:37:43Z",
        "version": 63
    },
    .
    .
    .
}'
```
## Response Body
Error message or "OK" if successful

## Example Response
```
"OK"
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Item has been successfully updated.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**409** |Conflict with existing class.|
|**500** |Internal Server Error. Check body for error message.|


