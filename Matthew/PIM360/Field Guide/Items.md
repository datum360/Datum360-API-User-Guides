# Items API Field Guide

The items APIs can be used for retrieving information about the different item types available in PIM360, these item types are:
* TAGGED ITEM
* DOCUMENT
* EQUIPMENT MODEL
* EQUIPMENT ITEM
* EIC

The information that is available includes, the items themselves, the change history of an item and item associations.

## Retrieving an item from PIM360

* There are a number of different APIs available for retrieving items from PIM360, each one returns the same detail but their usefulness can vary depending on what information you have available on hand when calling the API. For example `/objects/{type}/{handle}` can be useful if you have the handle (unique identifier) of the item you want to get, as this way there is no possible ambiguity on what will be returned. 
* `/objects/{type}/ID/{id}` is useful if you only have the name of the item that you want to retrieve, however as an item is uniquely identified by its combination of 'ID', 'Class Name' and 'Facility' it is possible for a different item to be returned than expected. **Note: ** There is currently a limitation with this API where it will only return the newest item that matches the `type` and `ID` combination, this is expected to be resolved in V2 of the API. 
* Finally `/objects/{type}/Facility/{facility}/ID/{id}` solves the issue with the previous API by allowing the 'Facility' of the item in question to be specified.
