# Long Running Tasks

This section includes the recommended approaches to handling long running tasks (LRTs) in REST APIs. 

You can identify a LRT quite easily. The main factor to consider are the metrics from latency of the endpoint. If it requiress tens of seconds even minutes we are facing a problem related to LRTs.

LRTs cannot be handled in a regular straight synchronous call. The amount of commited recources at the network, client and server levels are huge when connections are blocked for several minutes.  

It is strongly recommended to follow a non-blocking solution as it is proposed in this section.

