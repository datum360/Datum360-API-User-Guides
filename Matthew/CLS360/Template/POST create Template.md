# POST /domains/{domHdl}/templates

## Description
Allows the creation of a new template in CL4CL.

## Required Capabilities
* CanUseAPI
* CanUpdateCL4CL
## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters

* **domHdl** (required) (path) The handle of the Class Library/Domain to create the template in.

* **template** (required) (body) The JSON object representing the template to create.

## Example Request
```
curl --location 'https://{{systemName}}.cls360.io/api/domains/MAKZvz1eTQSvaQdvlHsYNw/templates' \
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
                    "value": "API Template"
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
                    "value": "Data",
                    "options": [
                    {
                        "label": "Data",
                        "value": "Data"
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

## Response Body
The handle of the newly created CL4CL template.

## Example Response
```
"nNoiWWvKTbKZo2wvH_CmiQ"
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Template has been successfully created.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**500** |Internal Server Error.|


