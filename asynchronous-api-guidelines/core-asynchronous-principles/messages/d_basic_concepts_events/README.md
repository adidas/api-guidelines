# Events

An event is both a fact and a notification, something that already happened in the real world.

* No expectation on any future action
* Includes information about a status change that just happened
* Travels in one direction and it never expects a response (fire and forget)
* Very useful when...
  * Loose coupling is important
  * When the same piece of information is used by several services
  * When data needs to be replicated across application

A message in general is any interaction between an emitter and a receiver to exchange information. This implies that any event can be considered a messages but not the other way around.

There are several ways to use events in a EDA:

* Events as notifications
* Events to replicate data
