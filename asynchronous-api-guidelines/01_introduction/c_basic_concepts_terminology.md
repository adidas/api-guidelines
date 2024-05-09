# adidas Asynchronous API guidelines

## Basic concepts about asynchronous APIs

### Basic terminology

#### Events

An event is both a fact and a notification, something that already happened in the real world.

- No expectation on any future action
- Includes information about a status change that just happened
- Travels in one direction and it never expects a response (fire and forget)
- Very useful when...
    - Loose coupling is important
    - When the same piece of information is used by several services
    - When data needs to be replicated across application

A message in general is any interaction between an emitter and a receiver to exchange information. This implies that any event can be considered a messages but not the other way around.

#### Commands

A command is a special type of message which represents just an action, something that will change the state of a given system.

- Typically synchronous
- There is a clear expectation about a state change that needs to take place in the future
- When returning a response indicate completion
- Optionally they can include a result in the response
- Very common to see them in orchestration components 

#### Query

It is a special type of message which represents a request to look something up.

- They are always free of side effects (leaves the system unchanged)
- They always require a response (with the requested data)

#### Coupling

The term coupling can be understood as the impact that a change in one component will have on other components. In the end, it is related to the amount of things that a given component shares with others. The more is shared, the more tight is the coupling.

**Note** A tighter coupling is not necessarily a bad thing, it depends on the situation. It will be necessary to assess the tradeoff between provide as much information as possible and to avoid having to change several components as a result of something changing in other component.

The coupling of a single component is actually a function of these factors:

- Information exposed (Interface surface area)
- Number of users
- Operational stability and performance
- Frequency of change 

Messaging helps bulding loosely coupled services because it moves pure data from a highly coupled location (the source) and puts it into a loosely coupled location (the subscriber). 

Any operations that need to be performed on the data are done in each subscriber and never at the source. This way, messaging technologies (like Kafka) take most of the operational issues off the table.

All business systems in larger organizations need a base level of essential data coupling. In other words, functional couplings are optional, but core data couplings are essential.

#### Bounded context

A bounded context is a small group of services that share the same domain model, are usually deployed together and collaborate closely.

It is possible to put an analogy here with a hierarchic organization inside a company : 

- Different departments are loosely coupled
- Inside departments there will be a lot more interactions across services and the coupling will be tighter

One of the big ideas of Domain-Driven Design (DDD) was to create boundaries around areas of a business domain and model them separately. So within the same bounded context the domain model is shared and everything is available for everyone there. 

However, different bounded contexts don't share the same model and if they need to interact they will do it through more restricted interfaces.

#### Stream processing

It can be understood as the capability of processing data directly as it is produced or received (hence, in real-time or near to real-time).