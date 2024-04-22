# adidas Asynchronous API guidelines

## Basic concepts about asynchronous APIs

### Event-driven architectures

An Event-Driven Architecture (EDA) uses events to trigger and communicate between services and is common in modern applications built with microservices. An event is a change in state, or an update, like adding a shopping item in a cart on an e-commerce website.

![EDA overview](../../assets/eda_overview.png)

In most cases, EDAs are broker-centric, as seen in the diagram above. There are some new concepts in that diagram, so let's go through them now.

In Event-Driven Architecture (EDA), an application must be a producer, a consumer, or both. Applications must also use the protocols the server supports if they wish to connect and exchange messages.

### Messages and events

A message carries information from one application to another, while an event is a message that provides details of something that has already occurred. One important aspect to note is that depending on the type of information a message contains, it can fall under an event, query, or command.

Overall, events are messages but not all messages are events.