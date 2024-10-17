# Datum360 API Field Guide

## Overview
Each one of the Datum360 services (CLS360, PIM360, DDM360) have their own set of APIs available allowing read/write capabilities to the connected data platform. The APIs allow code to be written to integrate with other external services, bringing in data to populate PIM360 and exporting data to update external data sources.

## Authorisation
To keep the connected data platform secure, any API calls with a valid authentication token will use the same capabilities as the logged in user. So if the user cannot do something in the UI it wil not be possible via the API. Therefore, it is recommended to test your proposed workflow through the UI using the same account that the API will use to confirm all required capabilities are present.

## Best Practices

* All API requests require an authentication token to be provided as part of the `Authentication` header. This token can be obtained from the `/oauth2/token` endpoint in ACL360. Tokens last for 30 minutes before expiring, therefore it is good practice to reuse the same token between requests. If you believe that your process will run for longer than 30 minutes, then it can be good to check for `403` response codes on requests you send. When a `403` is returned, this could indicate that the token you're using has expired and a new one should be obtained before retrying the call.

* When checking to see if an activity has completed, it is good practice to implement a delay of at least a few seconds between requests to the activity timeline rather than continuosly polling.

## Finding required information

A lot of API calls require handles to be provided and it can be difficult to know where to locate them. Below is a list of common handles that are required and where to find them:

* `eicHdl` This can easily be found by navigating to the EIC Explorer page in PIM360, then double clicking on the EIC you want the handle for. This should open up the EIC details page in its own tab, the handle can then be found in the address bar after `/EIC/` like so: https://{{systemName}}.pim360.io/object/EIC/XYSp3hn0TDuJV-NX6MrTBQ where `XYSp3hn0TDuJV-NX6MrTBQ` is the EIC handle. If you need to programmatically iterate over a number of EICs, then the best way to do that would be to call the `/eic/list` API.

* `liveviewHdl`/`pivotHdl` Handles of saved views such as liveview or pivot views can be found in the same way. Open the saved view in PIM360, then the handle should be in the address bar e.g https://{{systemName}}.pim360.io/liveview?viewhash=62utKNoWTlSkrFg14wYo6w where `62utKNoWTlSkrFg14wYo6w` is the view handle.

* `domainHdl` Most CLS360 APIs and some PIM360 APIs require the domain handle. The domain handle refers to the handle of a class library. This can be found using either PIM360 or CLS360 APIs. To find the handle of the class library currently being used by PIM360, call the `/snapshot` API, the `hdl` attribute in the response refers to the class library/domain handle. To get the handle of a class library/domain that is not currently synced to PIM360, call the `/domains` API in CLS360.
 
* `etlSourceHdl`/`etlTargetHdl` When running export and import activities, you will need the ETL Source for imports and the ETL Target for exports. This information is only held in CLS360 and can be retrieved either from the UI or API. To get the handle from the UI, navigate to CLS360, expand the `ETL` tab, single click on `ETL Sources` or `ETL Targets`, this should display a list of ETL Sources/Targets on the right hand side, double click on the required ETL Source/Target to open the details in a new tab. The handle should be in the address bar e.g  https://{{systemName}}.cls360.io/detail/classes/9hUV830ORX--xU99hZD-_g?ts=1724376997885 where `9hUV830ORX--xU99hZD-_g` is the handle. 
To get the handle using the CLS360 API, call the `/domains/{domainHdl}/classes` API and use the filter `Name eq [{ETL Name}] and [Object Type] eq [Data Source]` to get an ETL Source, for ETL Targets change `Data Source` to `Data Target`.