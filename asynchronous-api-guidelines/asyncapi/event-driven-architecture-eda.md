# Event Driven Architecture (EDA)

An Event-Driven Architecture (EDA) uses events to trigger and communicate between services and is common in modern applications built with microservices. An event is a change in state, or an update, like adding a shopping item in a cart on an e-commerce website.

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

In most cases, EDAs are broker-centric, as seen in the diagram above. There are some new concepts in that diagram, so let's go through them now.

In Event-Driven Architecture (EDA), an application must be a `producer`, a `consumer`, or both. Applications must also use the protocols the server supports if they wish to connect and exchange messages.

### Messages vs Events <a href="#messages-vs-events" id="messages-vs-events"></a>

A `message` carries information from one application to the other, while an `event` is a message that provides details of something that has already occurred. One important aspect to note is that depending on the type of information a `message` contains, it can fall under an _event_, _query_, or _command_.&#x20;

Overall, `events` are `messages` but not all `messages` are `events`.

### Command, Query and  Event <a href="#messages-vs-events" id="messages-vs-events"></a>

* Commands modify the data, often don't need to be real time and hence can scale well, and should only be handled in one specific way.
* Queries retrieve the data, need to be real time and hence need some creativity to somewhat scale.
* Events describe a fact that has happened in the past, don't need to be handled real time and hence can scale well, and can be handled by many subscribers in many different ways.
