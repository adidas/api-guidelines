# Versioning
> _The fundamental principle is that you can’t break existing clients, because you don’t know what they implement, and you don’t control them. In doing so, you need to turn a backwards-incompatible change into a compatible one._
>
> _– [Mark Nottingham](https://www.mnot.net/blog/2011/10/25/web_api_versioning_smackdown)_

Any change to an API MUST NOT break existing clients.


## Representation Format Change
> A representation format is the serialization format (media type) used in request and response bodies and typically it represents a resource or its part, possibly with additional hypermedia controls.

A change to a representation format MUST follow the [Rules for Extending](core-principles/rules-for-extending.md). 

If the change can't follow the Rules for Extending the representation format media type MUST be changed. If the media type has been changed the previous media type MUST be available via [Content Negotiation](core-principles/content-negotiation.md). 

#### Example

Media type _before_ a breaking change:

```
application/vnd.example.resource+json; version=2
```

Media type _after_ a breaking change:

```
application/vnd.example.resource+json; version=3
```

## Resource Change