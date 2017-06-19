# Design & Implementation Maturity

## API Design Maturity
> How to design an API


Every API design **MUST** be **resource-centric** ([Web API Design Maturity Model Level 2](http://amundsen.com/talks/2016-11-apistrat-wadm/2016-11-apistrat-wadm.pdf)). That is an API design **MUST** revolve around Web-styled _resources_, _relations_ between the resources and the _actions_ the resources may afford. 

An API design **MAY** be **affordance-centric** ([Web API Design Maturity Model Level 3](http://amundsen.com/talks/2016-11-apistrat-wadm/2016-11-apistrat-wadm.pdf)).

## API Design Implementation
> How to implement the API design

Every API design implementation using the HTTP(S) protocol **MUST** use the appropriate **HTTP Request Method** ([Richardson Maturity Model Level 2](https://martinfowler.com/articles/richardsonMaturityModel.html#level2)) to implement an action afforded by a resource.

An API design implementation **SHOULD** include **hypermedia controls** (HATEOAS) ([Richardson Maturity Model Level 3](https://martinfowler.com/articles/richardsonMaturityModel.html#level3)).
