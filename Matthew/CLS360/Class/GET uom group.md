# GET /domains/{domHdl}/classes/{classHdl}/uom-group

## Description
Gets the details of the uom specified by the class handle.

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **domHdl** (required) (path) The handle of the Domain/Class Library to get the class from

* **classHdl** (required) (path) The handle of the class to get. This must be a class of type "UoM Group", if any other handle is used then a 404 error will be returned.

* **version** (query) Which version of the Class Library to get the Class from. The latest version will be used by default.


## Example Request
```
curl --location 'https://{{systemName}}.cls360.io/api/domains/MAKZvz1eTQSvaQdvlHsYNw/classes/6ONugQvXQbqoOm0nvxBrcw/uom-group' \
--header 'Authorization: ••••••'
```

## Response Body
JSON object containing the full UoM class details. The UoMs within the UoM Group can be found in the `mapping` array.

## Example Response
``` JSON
{
    "data": [],
    "checksum": "2ba9b4e76e991dc18f8842084f227e2217089dd75e288f18187a7f35bda7ce22",
    "version": {
        "Ts": "2024-06-11T07:45:47.975Z",
        "Seed": {
            "Hdl": "1XIlspoMRge5YsgkTJfjZA",
            "Number": 98
        },
        "Origin": {
            "Hdl": "1XIlspoMRge5YsgkTJfjZA",
            "Number": 95
        }
    },
    "detail": {
        "hdl": "6ONugQvXQbqoOm0nvxBrcw",
        "label": "count",
        "icon": "UOM-GRP",
        "key": "6ONugQvXQbqoOm0nvxBrcw",
        "date": "2024-06-11T07:45:47Z",
        "version": 1
    },
    "alias": [
        {
            "label": "Name",
            "value": "count"
        },
        {
            "label": "ID",
            "value": "CFIHOS-45000037"
        },
        {
            "label": "unit of measure dimension code",
            "value": "COUNT"
        },
        {
            "label": "synonym",
            "value": ""
        },
        {
            "label": "created date",
            "value": "2019-04-08T09:51:20.365Z"
        },
        {
            "label": "modified date",
            "value": "2019-08-13T21:33:32.292Z"
        },
        {
            "label": "change request number",
            "value": "CR0022"
        }
    ],
    "metadata": [
        {
            "label": "Icon",
            "value": "UOM-GRP",
            "options": [
                {
                    "label": "TAG",
                    "value": "TAG"
                },
                .
                .
                .
            ]
        },
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
        }
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
            "value": "UoM Group",
            "options": [
                {
                    "label": "UoM Group",
                    "value": "UoM Group"
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
    ],
    "usedby": {
        "key": "usedby",
        "label": "Used By",
        "list": [
            {
                "Hdl": "Vvgf53h2TEONfJ2JYvZD9Q",
                "Name": "cold side number of passes",
                "Icon": "ATTR-MEAS",
                "Status": "STANDARD",
                "Type": "Measure Attribute"
            },
            .
            .
            .
        ]
    },
    "history": {
        "key": "history",
        "label": "History",
        "list": [
            {
                "id": 0,
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
            "key": "uoms",
            "label": "UoMs",
            "list": [
                {
                    "Name": "piece",
                    "ID": "CFIHOS-60000932",
                    "Unit": "",
                    "Description": "",
                    "Symbol": "pce",
                    "Database Representation": "pce",
                    "unit of measure code": "H87",
                    "unit of measure dimension code": "COUNT",
                    "measurement system code": "",
                    "synonym": "",
                    "created date": "2017-02-13T20:14:08.497Z",
                    "modified date": "2019-06-28T12:09:09.344Z",
                    "change request number": "CR0022;CR0025",
                    "POSC CAESAR": "RDS2228979",
                    "ISO 15926 part4": "",
                    "STEPLIB": "",
                    "Hdl": "XuR3g5M1QbmqJywogtR0aQ",
                    "Icon": "UOM",
                    "Status": "STANDARD"
                }
            ],
            "columns": [],
            "cache": "UoMs",
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


