# POST /domains/{domHdl}/classes

## Description
Allows the creation of a new class in the specified Class Library/Domain

## Required Capabilities
* CanUseAPI
* CanCreateClass

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **domHdl** (required) (path) Handle of the Class Library/Domain to create the class in.

* **class** (required) (body) JSON structure of the class to create.

## Example Request
```
curl --location 'https://{{systemName}}.cls360.io/api/domains/MAKZvz1eTQSvaQdvlHsYNw/classes' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
                "mapping": [],
                "checksum": "94923e87678b4cf3702cfb02d9072468af4b4a7f96ca3ab28606b6e90d4c7eaa",
                "version": {
                "Ts": "2024-02-13T15:33:04.351Z",
                "Seed": {
                    "Hdl": null,
                    "Number": 0
                }
                },
                "detail": {
                "hdl": null,
                "label": "New Object",
                "icon": null,
                "key": null,
                "date": "2024-02-13T15:33:04Z",
                "version": "Pending"
                },
                "alias": [
                {
                    "label": "Name",
                    "value": "{{New API Class Name}}"
                }
                ],
                "metadata": [
                {
                    "label": "Icon",
                    "value": "general",
                    "options": [
                    {
                        "label": "general",
                        "value": "general"
                    },
                    {
                        "label": null,
                        "value": null
                    }
                    ]
                }
                ],
                "permissions": {
                "edit": true,
                "editAliases": true,
                "copy": false,
                "clone": false,
                "kill": false
                },
                "data": [
                {
                    "key": "schema",
                    "label": "Schema",
                    "list": [],
                    "columns": [
                    "Columns"
                    ]
                }
                ],
                "associations": [
                {
                    "label": "Object Type",
                    "value": "Functional",
                    "options": [
                    {
                        "label": "Functional",
                        "value": "Functional"
                    }
                    ]
                },
                {
                    "label": "Class Library",
                    "value": "MAKZvz1eTQSvaQdvlHsYNw",
                    "options": [
                    {
                        "label": "Datum360 Standard",
                        "value": "MAKZvz1eTQSvaQdvlHsYNw"
                    }
                    ]
                }
                ]
            }'
```

The above example will create a new Functional class in CLS360. Note that this is the bare minimum needed to create a class. **The checksum value provided can and should be reused as this is a valid checksum**

## Response Body
String containing the handle of the newly created class

## Example Response
```
"685pQ0prSV6te2rFX9WuVg"
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**201** |Class has been successfully created.|
|**401**| Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**404**| Requested item can't be found. Check that the handle has been provided and is correct.|
|**500** |Internal Server Error. Detailed error message should be provided in the response body.|


