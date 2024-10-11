# GET /activitylog/issues

## Description
Returns a list of issues related to a specific task of an activity.

## Required Capabilities
* CanUseAPI

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters
* **taskhdl** (required) (query) The handle of the task to get issues for.

* **acthdl** (query) optional filter to restrict to a specific activity.


## Example Request
```
curl --location 'https://{{systemName}}.pim360.io/api/activitylog/issues?taskhdl=Zs45Fsq5TAueyT-JICHklA' \
--header 'Authorization: ••••••' \
```

## Response Body
A JSON object containing the properties `total_count`, `pos`, `rows`. `total_count` is the count of individual issues on a task. `pos` indicates how many records have been skipped in the current request. `rows` is an array of objects where each object is a different type of issue. If no results are found then an empty array is returned with a successful response code.

## Example Response
```JSON
{
    "total_count": 1285,
    "pos": 0,
    "rows": [
        {
            "id": 1,
            "group": "Object ID either missing from import file or value is blank||1285",
            "class": "Object ID either missing from import file or value is blank",
            "count": 1285,
            "filter": "undefined||Object_ID_either_missing_from_import_file_or_value_is_blank--Object_ID_either_missing_from_import_file_or_value_is_blank||1285"
        }
    ]
}
```

## Response Status Codes
| Status Code | Description |
| -------- | ------- |
|**200** |Matching item has been found and successfully returned.|
|**401** |Unauthorised, authentication is missing or invalid. Check that the token has not expired.|
|**500**| Internal Server Error.|


