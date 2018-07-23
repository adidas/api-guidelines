# Loose Coupling

In addition to the [robustness principle](https://github.com/adidas-group/api-guidelines/tree/af88d15fd04ef18d6724fa65943901aab7328e7f/rest/clients/core-principles/robustness.md), API consumers \(clients\) **MUST** **operate independently** on API implementation's internals. Similarly the API consumers **MUST NOT** **assume** or **rely on** any knowledge of the API service internal implementation.

Where available, the clients **SHOULD** utilize **hypermedia controls as the engine of the application state**, and rely on the **protocol, message and vocabulary semantics**.

