# GET /eic/list

## Description
Gets a summary of all EICs

## Required Capabilities
* CanUseAPI
* CanSeeEicExplorer
* CanSeeAllPages

## Request Headers

**Authorization** OAuth2 bearer token, obtained from the Authorisation endpoint (2-legged or 3-legged flow)

## Parameters



## Example Request
`
curl --location 'https://{{systemName}}.pim360.io/api/eic/list' \
--header 'Authorization: ••••••'
`

## Response Body
A JSON object with a property `rows` containing an object for each EIC. Each EIC object contains basic information such as ID (number), status and id (hdl), as well as all of the attributes on that EIC. EIC attributes are stored as key-value pairs on the object, where the key is the attribute handle, and the value is the value of the attribute. To convert an attribute handle to a name, it must be passed to the `GET classes` CLS360 API. 

## Example Response
```JSON
{
    "pos": 0,
    "rows": [
        {
            "id": "XYSp3hn0TDuJV-NX6MrTBQ",
            "ID": 1,
            "Status": "Active",
            "cmp": 8.97,
            "typed_cmp": 8.97,
            "wHq8duseQeiKHFTEq6zoog": "Commissioning Demo",
            "WzGMbejhR5i8FFPJ8354iQ": "Seed ACC (This EIC)",
            "XzY91ULiQn2TBSLpfhMO2w": "Unable to get required info from ACC",
            "L48ZcUL6RWeDwDZeAkLvwQ": 1,
            "vQPCnBpNRwSAjFbTbu_vxw": "Commissioning Demo",
            "crBhwt7JTAGGZNHDeUucVg": "Submitted",
            "XO19QrZgSjqurYdGbfMvdA": "Commissioning Integration"
        },
        {
            "id": "tJsy-BtWQbe2SoaTeNVAcQ",
            "ID": 2,
            "Status": "Active",
            "cmp": 0,
            "typed_cmp": 0,
            "vRMDPN4QRQGlKBx7lDyglg": "BIM360 Integration",
            "3pMgzO5fTXy18iYQMggnZw": "dwg;rvt",
            "EylyaKO2QNmv3sKhYWTppA": "architectural engineering - approval certificate",
            "C3WE86Y7SOWvszM5B3N23w": "architectural engineering - approval certificate",
            "SAJViqiRTqu7iBnHTPAkbw": "standard attributes",
            "cJvtxdNSRmK9mrRZTjWncA": "Standard ENS",
            "GNSRrBUZTUCw01SimoC2EQ": "actuator",
            "QlTaiX6jQZez38iQi8tcag": "TKF",
            "63puB0_HTzKgD-bgfsnByg": "Yes",
            "uuXIWcXoStqe_rQfXy13Hw": "standard attributes",
            "Ngo_Ehy2ReKjOlGF_eY2cg": "General Plant.Tag",
            "L48ZcUL6RWeDwDZeAkLvwQ": 2,
            "vQPCnBpNRwSAjFbTbu_vxw": "BIM360 Document Scraping",
            "crBhwt7JTAGGZNHDeUucVg": "Open",
            "XO19QrZgSjqurYdGbfMvdA": "BIM360 Integration"
        },
        {
            "id": "UBzA9lXTQzmWtC2mketjdA",
            "ID": 3,
            "Status": "Active",
            "cmp": 39.29,
            "typed_cmp": 39.29,
            "L48ZcUL6RWeDwDZeAkLvwQ": 3,
            "XO19QrZgSjqurYdGbfMvdA": "Contract Data Collection",
            "vQPCnBpNRwSAjFbTbu_vxw": "GIS",
            "crBhwt7JTAGGZNHDeUucVg": "Submitted"
        }
    ]
}
```

## Response Status Codes
**200** Matching item has been found and successfully returned
**401** Unauthorised, authentication is missing or invalid. Check that the token has not expired
**404** Requested item can't be found. Check that the handle has been provided and is correct.
**500** Internal Server Error


