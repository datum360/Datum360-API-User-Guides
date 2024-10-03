# GET /domains/{domHdl}/templates/{tmpHdl}

## Description
Gets the CL4CL Template by handle.

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters

* **domHdl** (required) (path) The handle of the Class Library/Domain to use.
* **tmpHdl** (required) (path) The handle of the template to request.
* **version** (query) The version of the Class Library/Domain to use. Must be a number, defaults to the latest available version if not provided.

## Example Request
```
curl --location 'https://{{systemName}}.cls360.io/api/domains/MAKZvz1eTQSvaQdvlHsYNw/templates/qHw1SY80Ty-wZegNrrvymw' \
--header 'Authorization: ••••••'
```

## Response Body
JSON object containing the full details of the requested CL4CL Template.

## Example Response
```JSON
{
    "data": [],
    "checksum": "ea429bd0c79462d0e00d9b8c8e190302686262084d42e42ed720f63fc4338273",
    "version": {
        "Ts": "2024-06-17T12:36:32.277Z",
        "Seed": {
            "Hdl": "YVjtAqLwRiSUdqNyQMgeUQ",
            "Number": 491
        },
        "Origin": {
            "Hdl": "YVjtAqLwRiSUdqNyQMgeUQ",
            "Number": 1
        }
    },
    "detail": {
        "hdl": "qHw1SY80Ty-wZegNrrvymw",
        "label": "Information Attribute",
        "icon": "ATTR-INFO",
        "key": "qHw1SY80Ty-wZegNrrvymw",
        "date": "2024-06-17T12:36:32Z",
        "version": 7
    },
    "alias": [
        {
            "label": "Name",
            "value": "Information Attribute"
        }
    ],
    "permissions": {
        "edit": true,
        "editAliases": true,
        "copy": false,
        "clone": false,
        "kill": false
    },
    "metadata": [
        {
            "label": "Icon",
            "value": "ATTR-INFO",
            "options": [
                {
                    "label": "TAG",
                    "value": "TAG"
                },
                {
                    "label": "SS",
                    "value": "SS"
                }
            ]
        },
        {
            "label": "Data Type",
            "value": "STRING",
            "options": [
                {
                    "label": "STRING",
                    "value": "STRING"
                },
                {
                    "label": "DATE",
                    "value": "DATE"
                },
                {
                    "label": "INTEGER",
                    "value": "INTEGER"
                },
                {
                    "label": "FLOAT",
                    "value": "FLOAT"
                },
                {
                    "label": "BOOLEAN",
                    "value": "BOOLEAN"
                }
            ]
        }
    ],
    "mapping": [
        {
            "key": "alias",
            "label": "Alias",
            "list": [
                {
                    "Hdl": "Name",
                    "Name": "Name",
                    "Icon": "general",
                    "Group": "Alias"
                },
                {
                    "Hdl": "ID",
                    "Name": "ID",
                    "Icon": "general",
                    "Group": "Alias"
                },
                {
                    "Hdl": "Description",
                    "Name": "Description",
                    "Icon": "general",
                    "Group": "Alias"
                }
            ],
            "columns": [],
            "cache": "Alias",
            "type": "templates",
            "sequence": true
        },
        {
            "key": "associations",
            "label": "Associations",
            "list": [
                {
                    "Hdl": "Object Type",
                    "Name": "Object Type",
                    "Icon": "general",
                    "Group": "Associations"
                },
                {
                    "Hdl": "Class Library",
                    "Name": "Class Library",
                    "Icon": "general",
                    "Group": "Associations"
                }
            ],
            "columns": [],
            "cache": "Associations",
            "type": "templates",
            "sequence": true
        },
        {
            "key": "metadata",
            "label": "Metadata",
            "list": [
                {
                    "Hdl": "Icon",
                    "Name": "Icon",
                    "Icon": "general",
                    "Group": "Metadata"
                },
                {
                    "Hdl": "Data Type",
                    "Name": "Data Type",
                    "Icon": "general",
                    "Group": "Metadata"
                },
                {
                    "Hdl": "Status",
                    "Name": "Status",
                    "Icon": "general",
                    "Group": "Metadata"
                },
                {
                    "Hdl": "Applicable to Commissioning",
                    "Name": "Applicable to Commissioning",
                    "Icon": "general",
                    "Group": "Metadata"
                }
            ],
            "columns": [],
            "cache": "Metadata",
            "type": "templates",
            "sequence": true
        },
        {
            "key": "mapping",
            "label": "Mapping",
            "list": [],
            "columns": [],
            "cache": "Mapping",
            "type": "templates",
            "sequence": true
        },
        {
            "key": "data",
            "label": "Data",
            "list": [
                {
                    "Hdl": "Validation Rules",
                    "Name": "Validation Rules",
                    "Icon": "general",
                    "Group": "Data"
                },
                {
                    "Hdl": "Lookup Values",
                    "Name": "Lookup Values",
                    "Icon": "general",
                    "Group": "Data"
                }
            ],
            "columns": [],
            "cache": "Data",
            "type": "templates",
            "sequence": true
        }
    ],
    "associations": [
        {
            "label": "Object Type",
            "value": "Template",
            "options": [
                {
                    "label": "Template",
                    "value": "Template"
                }
            ]
        },
        {
            "label": "Class Library",
            "value": "MAKZvz1eTQSvaQdvlHsYNw",
            "options": [
                {
                    "label": "CFIHOS v1.5.1",
                    "value": "MAKZvz1eTQSvaQdvlHsYNw"
                }
            ]
        }
    ]
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Matching item has been found and successfully returned.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**404** |Requested item can't be found. Check that the handle has been provided and is correct.|
|**500** |Internal Server Error|


