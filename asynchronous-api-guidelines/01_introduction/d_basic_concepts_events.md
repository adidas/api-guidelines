# adidas Asynchronous API guidelines

## Basic concepts about asynchronous APIs

### Using events in an EDA

There are several ways to use events in a EDA:

- Events as notifications
- Events to replicate data


#### Events as notifications

When a system uses events as notifications it becomes a pluggable system. The producers have no knowledge about the consumers and they don't really care about them, instead every consumer can decide if it is interested in the information included in the event. 

This way, the number of consumers can be increased (or reduced) without changing anything on the producer side.

This pluggability becomes increasily important as systems get more complex.

#### Events to replicate data

When events are used to replicate data across services, they include all the necessary information for the target system to keep it locally so that it can be queried with no external interactions. 

This is usually called event-carried state transfer which in the end is a form of data integration. 

The benefits are similar to the ones implied by the usage of a cache system

- Better isolation and autonomy, as the data stays under service's control
- Faster data access, as the data is local (particularly important when combining data from different services in different geographies)
- Offline data availability
