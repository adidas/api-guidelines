# Bounded Context

A bounded context is a small group of services that share the same domain model, are usually deployed together and collaborate closely.

It is possible to put an analogy here with a hierarchic organization inside a company :

* Different departments are loosely coupled
* Inside departments there will be a lot more interactions across services and the coupling will be tighter

One of the big ideas of Domain-Driven Design (DDD) was to create boundaries around areas of a business domain and model them separately. So within the same bounded context the domain model is shared and everything is available for everyone there.

However, different bounded contexts don't share the same model and if they need to interact they will do it through more restricted interfaces.
