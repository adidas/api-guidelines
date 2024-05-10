# Event Driven Architectures

Event-Driven Architectures (EDAs) are a paradigm that promotes the production, consumption and reaction to events.

This architectural pattern may be applied by the design and implementation of applications and systems that transmit events amongst loosely coupled software components and services.

An event-driven system typically consists of event emitters (or agents), event consumers (or sinks), and event channels.

* Producers (or publishers) are responsible for detecting, gathering and transferring events
  * Are not aware of consumers
  * Are not aware of how the events are consumed
* Consumers (or subscribers) react to the events as soon as they are produced
  * The reaction can be self-contained or it can be a composition of processes or components
* Event channels are conduits in which events are transmitted from emitters to consumers

**Note** Producer and Consumer role is not exclusive. In other words, the same client or application can be producer and consumer at the same time.

In most cases, EDAs are broker-centric, as seen in the diagram below.

![EDA overview](../../assets/eda\_overview.png)

_The figure above was taken from AsyncAPI official documentation_

#### Problem statement

Typically, the architectural landscape of a big company grows in complexity and as a result of that it is possible to end up with a bunch of direct connections between a myriad of different components or modules.

![Typical architecture diagram](../../assets/eda\_problem\_statement\_1.png)

By using streaming patterns, it is possible to get a much cleaner architecture

![EDA architecture diagram](../../assets/eda\_problem\_statement\_2.png)

It is important to take into account that EDAs are not a silver bullet, and there are situations in which this kind of architectures might not fit very well.

One example is systems that heavily rely on transactional operations... of course it might be possible to use EDA but most probably the complexity of the resulting architecture would be too high.

Also, it is important to note that it is possible to mix request-driven and event-driven protocols in the same system. For example,

* Online services that interact directly with a user fits better into the synchronous communication but they also can generate events.
* On the other hand, offline services (billing, fulfillment, etc) are typically built purely with events.

