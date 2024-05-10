# Events to Replicate Data

When events are used to replicate data across services, they include all the necessary information for the target system to keep it locally so that it can be queried with no external interactions.

This is usually called event-carried state transfer which in the end is a form of data integration.

The benefits are similar to the ones implied by the usage of a cache system

* Better isolation and autonomy, as the data stays under service's control
* Faster data access, as the data is local (particularly important when combining data from different services in different geographies)
* Offline data availability
