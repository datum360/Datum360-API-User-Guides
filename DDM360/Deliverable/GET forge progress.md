# GET /deliverables/{delHdl}/files/{fileHdl}/forgeupload

## Description
Gets the progress of a file that has been submitted to BIM360/ACC

## Required Capabilities
* CanUseAPI
* CanSubmitForge
## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **delHdl** (required) (path) Handle of the deliverable to use.

* **fileHdl** (required) (path) Handle of the file.

## Example Request
```
curl --location 'https://{{systemName}}.ddm360.io/api/deliverables/XaVlSbewT7qLr53fgCtVgw/files/v8JNBCMdR8--dFZNPoiq3g/forgeupload' \
--header 'Authorization: ••••••'
```

## Response Body
JSON object describing the file in BIM360/ACC. Progress can be found on the `progress` attribute. Contents may differ depending on if BIM360 or ACC is used.

## Example Response
```JSON
{
    "guid": "dXJuOmFkc2sud2lwZW1lYTpmcy5maWxlOnZmLnZkUl9RRmJSUmQ2cTl2TlRQanFJV2c_dmVyc2lvbj02",
    "owner": "dXJuOmFkc2sud2lwZW1lYTpmcy5maWxlOnZmLnZkUl9RRmJSUmQ2cTl2TlRQanFJV2c_dmVyc2lvbj02",
    "hasThumbnail": "true",
    "startedAt": "Thu Sep 05 05:14:33 UTC 2024",
    "type": "design",
    "urn": "dXJuOmFkc2sud2lwZW1lYTpmcy5maWxlOnZmLnZkUl9RRmJSUmQ2cTl2TlRQanFJV2c_dmVyc2lvbj02",
    "success": "100%",
    "progress": "complete",
    "region": "EMEA",
    "status": "success",
    "registerKeys": {
        "{\"CommandId\":\"4d68d59b-3d3a-476a-acaa-44b4a6d0a999\"}": [
            "3c6a7e71-c7c0-42d8-b24b-1d1aaf9b85b3",
            "cb73c076-d3cd-a725-754f-a64cd8c07648",
            "36658f73-31af-4098-9a59-5e0284817ae2",
            "b1888752-4b5b-3c51-9752-e4760db37817"
        ]
    },
    "children": [
        {
            "guid": "aa85aad6-c480-4a35-9cbf-4cf5994a25ba",
            "role": "viewable",
            "hasThumbnail": "true",
            "progress": "complete",
            "type": "folder",
            "status": "success",
            "version": "2.0",
            "urn": "dXJuOmFkc2sud2lwZW1lYTpmcy5maWxlOnZmLnZkUl9RRmJSUmQ2cTl2TlRQanFJV2c_dmVyc2lvbj02",
            "inputFileSize": 607824,
            "inputFileType": "dwg",
            "name": "TKF-NEE-10001-E-M2D-017.dwg",
            "success": "100%",
            "properties": {
                "Document Information": {
                    "DWGVersion": "2013",
                    "Date Created": "12/16/2010 12:01:58 AM",
                    "FileSize": "607824",
                    "Last Author": "rappr",
                    "Last Write": "11/16/2015 1:17:35 AM",
                    "Name": "TKF-NEE-10001-E-M2D-017.dwg"
                }
            },
            "children": [
                {
                    "guid": "3c6a7e71-c7c0-42d8-b24b-1d1aaf9b85b3",
                    "type": "resource",
                    "urn": "urn:adsk.viewing:fs.file:dXJuOmFkc2sud2lwZW1lYTpmcy5maWxlOnZmLnZkUl9RRmJSUmQ2cTl2TlRQanFJV2c_dmVyc2lvbj02/output/designDescription.json",
                    "role": "Autodesk.CloudPlatform.DesignDescription",
                    "mime": "application/json"
                },
                {
                    "guid": "cb73c076-d3cd-a725-754f-a64cd8c07648",
                    "type": "resource",
                    "urn": "urn:adsk.viewing:fs.file:dXJuOmFkc2sud2lwZW1lYTpmcy5maWxlOnZmLnZkUl9RRmJSUmQ2cTl2TlRQanFJV2c_dmVyc2lvbj02/output/properties.db",
                    "role": "Autodesk.CloudPlatform.PropertyDatabase",
                    "mime": "application/autodesk-db",
                    "status": "success",
                    "size": 349184
                },
                {
                    "guid": "36658f73-31af-4098-9a59-5e0284817ae2",
                    "type": "folder",
                    "name": "Sheets",
                    "role": "viewable",
                    "hasThumbnail": "true",
                    "status": "success",
                    "progress": "complete",
                    "success": "100%",
                    "children": [
                        {
                            "guid": "98e1f155-3bdd-f0d4-facd-9f410d382daf",
                            "type": "geometry",
                            "role": "2d",
                            "name": "PID ANSI D Title Block",
                            "viewableID": "PID ANSI D Title Block",
                            "status": "success",
                            "size": 45580,
                            "hasThumbnail": "true",
                            "progress": "complete",
                            "success": "100%",
                            "children": [
                                {
                                    "guid": "21bade81-b151-8fcd-5ec6-51a48fa5db3d",
                                    "type": "resource",
                                    "mime": "application/autodesk-f2d",
                                    "role": "graphics",
                                    "size": 38340,
                                    "status": "success",
                                    "urn": "urn:adsk.viewing:fs.file:dXJuOmFkc2sud2lwZW1lYTpmcy5maWxlOnZmLnZkUl9RRmJSUmQ2cTl2TlRQanFJV2c_dmVyc2lvbj02/output/f9cd70d4-af6f-403f-7dd1-36c7a490f024_f2d/primaryGraphics.f2d"
                                }
                            ]
                        }
                    ]
                },
                {
                    "guid": "b1888752-4b5b-3c51-9752-e4760db37817",
                    "type": "folder",
                    "name": "Model",
                    "role": "viewable",
                    "hasThumbnail": "true",
                    "status": "success",
                    "progress": "complete",
                    "success": "100%",
                    "children": [
                        {
                            "guid": "6882be48-6626-5238-d3df-94e9f0a0019d",
                            "type": "geometry",
                            "role": "2d",
                            "name": "2D View",
                            "viewableID": "Model",
                            "status": "success",
                            "size": 40078,
                            "hasThumbnail": "true",
                            "progress": "complete",
                            "success": "100%",
                            "children": [
                                {
                                    "guid": "b422c6ee-cc30-66a6-51c8-ff7951e2dd59",
                                    "type": "resource",
                                    "mime": "application/autodesk-f2d",
                                    "role": "graphics",
                                    "size": 33584,
                                    "status": "success",
                                    "urn": "urn:adsk.viewing:fs.file:dXJuOmFkc2sud2lwZW1lYTpmcy5maWxlOnZmLnZkUl9RRmJSUmQ2cTl2TlRQanFJV2c_dmVyc2lvbj02/output/833c0b8c-2a2d-ad5d-5322-00ffbd241064_f2d/primaryGraphics.f2d"
                                }
                            ]
                        }
                    ]
                }
            ]
        },
        {
            "guid": "dd74e41f-584f-48e2-b6f7-57a3068e1825",
            "role": "metadata",
            "hasThumbnail": "false",
            "success": "100%",
            "progress": "complete",
            "type": "folder",
            "status": "success",
            "children": [
                {
                    "guid": "37732a95-fe94-4836-8104-35041c1879db",
                    "urn": "urn:adsk.viewing:fs.file:dXJuOmFkc2sud2lwZW1lYTpmcy5maWxlOnZmLnZkUl9RRmJSUmQ2cTl2TlRQanFJV2c_dmVyc2lvbj02/ds/db887801-c0df-43fe-a5ec-a873918d27bf/designdescription.json",
                    "role": "Autodesk.CloudPlatform.DesignDescription.Registered",
                    "type": "resource"
                }
            ]
        }
    ]
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
**200** |Matching item has been found and successfully returned.
**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.
**404** |Requested item can't be found. Check that the handle has been provided and is correct.
**500** |Internal Server Error.


