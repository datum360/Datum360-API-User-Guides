# GET /domains/{domHdl}/classes/{classHdl}

## Description
Retrieves the class specified by the class handle from the Domain/Class Library specified.

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **domHdl** (required) (path) The handle of the Domain/Class Library to get the class from

* **classHdl** (required) (path) The handle of the class to get

* **version** (query) Which version of the Class Library to get the Class from. The latest version will be used by default.

## Example Request
```
curl --location 'https://{{systemName}}.cls360.io/api/domains/MAKZvz1eTQSvaQdvlHsYNw/classes/_CU46pvVSd-i3KkyPfVkVg' \
--header 'Authorization: ••••••'
```

## Response Body
JSON object containing the full class details

## Example Response
``` JSON
{
    "data": [],
    "checksum": "a215ff9a707a914f122ba5bd1cef61c126c65493cda94e3761cf9050d2e8e305",
    "version": {
        "Ts": "2024-07-09T08:33:44.730Z",
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
        "date": "2024-07-09T08:33:44Z",
        "version": 50
    },
    "alias": [
        {
            "label": "Name",
            "value": "cabinet"
        }
    ],
    "metadata": [
        {
            "label": "Status",
            "value": "STANDARD",
            "options": [
                {
                    "label": "STANDARD",
                    "value": "STANDARD"
                },
                {
                    "label": "TERMINATED",
                    "value": "TERMINATED"
                }
            ]
        },
    ],
    "permissions": {
        "edit": true,
        "editAliases": true,
        "copy": true,
        "clone": false,
        "kill": true
    },
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
                    "label": "CFIHOS v1.5.1",
                    "value": "MAKZvz1eTQSvaQdvlHsYNw"
                }
            ]
        },
        {
            "label": "Discipline",
            "value": "OQJopgrVTkGR-HuaMFiSPA",
            "options": [
                {
                    "label": "construction",
                    "value": "67QvS4ceQ8ybUAJHGHtpyQ"
                }
            ]
        }
    ],
    "usedby": {
        "key": "usedby",
        "label": "Used By",
        "list": []
    },
    "history": {
        "key": "history",
        "label": "History",
        "list": [
            {
                "id": 3,
                "Version": 1,
                "Type": "Created Object",
                "Field": "",
                "Initial": "",
                "Updated": "",
                "User": "Test Runner",
                "Ts": "2024-06-11T07:45:47.975Z"
            }
        ]
    },
    "mapping": [
        {
            "key": "attributes",
            "label": "Attributes",
            "list": [
                {
                    "Hdl": "YR0DQgwsQ6qzYxVh-i_F2Q",
                    "Name": "explosion protection gas group",
                    "Icon": "ATTR-INFO",
                    "Status": "STANDARD",
                    "Group": "2 Design Information, 4 Ready for Handover, RDL - class properties, Stage 3 Detail Design, Stage 4 Construction, Stage 5 Commission/Handover"
                },
                {
                    "Hdl": "4J9Br2OvQD6Stvhm5IgF8Q",
                    "Name": "designed by company name",
                    "Icon": "facility",
                    "Status": "STANDARD",
                    "Group": "1 Core Information, 4 Ready for Handover, data model - entity attributes"
                }
            ],
            "columns": [],
            "cache": "Attributes",
            "type": "classes",
            "sequence": false
        },
        {
            "key": "mappedtophysical",
            "label": "Mapped To Physical",
            "list": [
                {
                    "Hdl": "M8FEfCCVQemKiqvhER0iKg",
                    "Name": "cabinet",
                    "Icon": "EQ-ITEM",
                    "Status": "STANDARD",
                    "Group": "electrical engineering"
                }
            ],
            "columns": [],
            "cache": "Mapped To Physical",
            "type": "classes",
            "sequence": false
        },
        {
            "key": "normaldocuments",
            "label": "Normal Documents",
            "list": [
                {
                    "Hdl": "1ZHD6vFqRCi6D3JlRd5Zmg",
                    "Name": "maintenance management - spare part list",
                    "Icon": "general",
                    "Status": "STANDARD",
                    "Group": "Document"
                }
            ],
            "columns": [],
            "cache": "Normal Documents",
            "type": "classes",
            "sequence": false
        },
        {
            "key": "superclass",
            "label": "Superclass",
            "list": [
                {
                    "Hdl": "rgOOsbKRS9CVOHH0Rdb8jg",
                    "Name": "H_enclosure",
                    "Icon": "TAG",
                    "Status": "STANDARD",
                    "Group": "Functional"
                }
            ],
            "columns": [],
            "cache": "Superclass",
            "type": "classes",
            "sequence": false
        }
    ]
}
```


## Response Status Codes
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


