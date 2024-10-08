# PIM360 API Field Guide

## Best Practices

### Avoiding expensive operations
Some APIs in PIM360 can be considered "expensive" either in the time they take to run, the amount of processing required or the impact on the system overall. Expensive operations should be used carefully, with consideration, and where possible less intense operations should be used.

An example of this is exporting large amounts of data. If you want to export the full contents of a liveview, you could run an export activity which will dump the results out into an xlsx/txt file available on the timeline. However, this can block up the activity queue if the export activity is taking a long time. Alternatively running an export activity also relies on the queue being free for the activity to run, so if there is already a long running activity when your request is submitted, you will have to wait for that to finish before yours completes.

To avoid this Query APIs such as `queryresults/{handle}` and `queryresults/views/{handle}` should be used, these do not use the activity queue and they can handle large exports by utilising the paging capabilities of these APIs.

Another example of an expensive operation would be a snapshot or publish. If you have code that calls these APIs, try and schedule it so that it runs at a time when the system is not being used as these activities can hold up the activity queue for a long time. This can impact other users of the system from running import and export activities.

In some cases expensive operations can't be avoided, for example import activities. The only way to import data is to use the activity timeline. In this scenario the best thing to do is make sure that each call is meaningful. If there are multiple objects of the same type to update in the same EIC, make sure that they are all batched up into one activity, rather than an activity per object.

