# CLS360 Field Guide

## Getting Data From CLS360
The main point to consider when retrieving data from CLS360 is that almost everything is a class. Anything that is available in the object browser can be accessed using one of the `class` APIs. The object types available in CLS360 are:
* Activities
* Classes
* Domains
* Files
* Schema
* Templates

## CLS360 Snapshot Structure

The CLS360 snapshot is a JSON representation of the entire CLS360 class library and is used for configuring the structure of data loaded into PIM360. If a large number of API calls need to be made against CLS360 to retrieve data, then it can be better to call the API `GET /domains/{domHdl}/snapshot` to retrieve the entire class library. The below describes each section of the CLS360 snapshot

### domain

#### Example
```JSON
"domain": {
        "Hdl": "MAKZvz1eTQSvaQdvlHsYNw",
        "Name": "CFIHOS v1.5.1",
        "Label": "CFIHOS v1.5.1",
        "Company": "Deprecated",
        "Logo": "img/logo.png",
        "Lock": false,
        "Version": 61
    }
```

This section contains a summary of the class library/domain including its handle, name and the current version.

### schema

#### Example
```JSON
"schema": {
        "_id": "616eddc41de47d290f146be5",
        "Version": 13,
        "API": "clsio-api"
    },
```

Schema shows the version of a class library. This can be useful if you want to be able to compare 2 different class libraries, it is best to ensure they are on the same version so the structure is the same.

### CL4CL

#### Example
```JSON
"CL4CL": [
        {
            "Hdl": "izqjbxwJTYinfI1KYs3qbQ",
            "Alias": [
                {
                    "Lbl": "Name",
                    "Val": "UoM ID"
                }
            ],
            "Associations": [
                {
                    "Typ": "Object Type",
                    "ObjHdl": "Alias"
                },
                {
                    "Typ": "Class Library",
                    "ObjHdl": "MAKZvz1eTQSvaQdvlHsYNw"
                }
            ],
            "Metadata": [
                {
                    "Lbl": "Icon",
                    "Val": "general"
                }
            ],
            "Mapping": {},
            "Data": {},
            "Version": {
                "Ts": "2024-06-11T07:45:47.975Z",
                "Current": true,
                "Number": 1,
                "User": {
                    "Hdl": "j9q65-fBQ9aJ_Hpx_C76Bw",
                    "Name": "Test Runner",
                    "Role": "Test Runner"
                },
                "Seed": {
                    "Hdl": "_Z7lBGqcSUuOwKn3P7mEzg",
                    "Number": 1
                },
                "Origin": {
                    "Hdl": "_Z7lBGqcSUuOwKn3P7mEzg",
                    "Number": 1
                }
            }
        }
]
```

CL4CL contains an object array where each object is a different item from CL4CL. These object types are:
* Template
* Alias
* Associations
* Metadata
* Mappings
* Data

### Classes

#### Example
```JSON
 "classes": [
        {
            "Hdl": "G-XKmmPARbuRAWVuqj3BIg",
            "Alias": [
                {
                    "Lbl": "Name",
                    "Val": "pressure"
                },
                {
                    "Lbl": "ID",
                    "Val": "CFIHOS-45000017"
                },
                {
                    "Lbl": "unit of measure dimension code",
                    "Val": "PRESS"
                },
                {
                    "Lbl": "synonym",
                    "Val": ""
                },
                {
                    "Lbl": "created date",
                    "Val": "2019-03-06T16:01:12.715Z"
                },
                {
                    "Lbl": "modified date",
                    "Val": "2019-10-14T17:01:30.284Z"
                },
                {
                    "Lbl": "change request number",
                    "Val": "CR0022"
                }
            ],
            "Associations": [
                {
                    "Typ": "Object Type",
                    "ObjHdl": "UoM Group"
                },
                {
                    "Typ": "Class Library",
                    "ObjHdl": "MAKZvz1eTQSvaQdvlHsYNw"
                }
            ],
            "Metadata": [
                {
                    "Lbl": "Icon",
                    "Val": "UOM-GRP"
                },
                {
                    "Lbl": "Status",
                    "Val": "STANDARD"
                }
            ],
            "Mapping": {
                "UoMs": [
                    "u6ZKAZGfS7q4RCopGTDM7g",
                    "hgOtwgOvRlaYocVZb3-1Ow",
                    "1MsKfBsMSd6eDT-rSMzecg",
                    "om03fXxfR2WlDGMXq48XBw",
                    "9Q7s1xhdR5-ewyFC73akZg",
                    "spGQqQ2UTI2FBR1AGmn7Uw",
                    "25VNzPUpTnWKzccy_hzerA",
                    "RwpHj3nwRZ23GkhIiwn3Tw",
                    "hE36j8RqQMmhvEnxNVaJlQ"
                ]
            },
            "Data": {},
            "Version": {
                "Ts": "2024-06-11T07:45:47.975Z",
                "Current": true,
                "Number": 1,
                "User": {
                    "Hdl": "j9q65-fBQ9aJ_Hpx_C76Bw",
                    "Name": "Test Runner",
                    "Role": "Test Runner"
                },
                "Seed": {
                    "Hdl": "Ju8R6Nc8QD63-T66qAXmIg",
                    "Number": 98
                },
                "Origin": {
                    "Hdl": "Ju8R6Nc8QD63-T66qAXmIg",
                    "Number": 95
                }
            }
        }
 ]
```

Classes is the final section of the snapshot and it contains an array of every object available in the "Object Browser" view of CLS360. The detail in each one of these objects is the same as calling `GET /domains/{domhdl}/classes/{classHdl}` for each individual class.