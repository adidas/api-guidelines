# Coupling

The term coupling can be understood as the impact that a change in one component will have on other components. In the end, it is related to the amount of things that a given component shares with others. The more is shared, the more tight is the coupling.

**Note:** A tighter coupling is not necessarily a bad thing, it depends on the situation. It will be necessary to assess the trade-off between providing as much information as possible and to avoid having to change several components as a result of something changing in other component.

The coupling of a single component is actually a function of these factors:

* Information exposed (Interface surface area)
* Number of users
* Operational stability and performance
* Frequency of change

Messaging helps building loosely coupled services because it moves pure data from a highly coupled location (the source) and puts it into a loosely coupled location (the subscriber).

Any operations that need to be performed on the data are done in each subscriber and never at the source. This way, messaging technologies (like Kafka) take most of the operational issues off the table.

All business systems in larger organizations need a base level of essential data coupling. In other words, functional couplings are optional, but core data couplings are essential
