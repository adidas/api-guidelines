# Changes and Versioning

> _The fundamental principle is that you can’t break existing clients, because you don’t know what they implement, and you don’t control them. In doing so, you need to turn a backwards-incompatible change into a compatible one._
>
> _– _[_Mark Nottingham_](https://www.mnot.net/blog/2011/10/25/web_api_versioning_smackdown)

Any change to an API **MUST NOT** break existing clients.

Any change to:  
1. **Resource identifier** \(resource name / URI\) including any **query parameters** and their semantics  
1. **Resource metadata** \(e.g. HTTP headers\)  
1. **Action** the resource affords \(e.g. available HTTP Methods\)  
1. **Relation** with other resources \(e.g Links\)  
1. **Representation format** \(e.g. HTTP request and response bodies\)

**MUST** follow the [**Rules for Extending**](https://adidas-group.gitbooks.io/api-guidelines/content/core-principles/rules-for-extending.html).

## Identifier Stability \(No URI Versioning\)

A change **MUST NOT** affect **existing** resource identifiers \(name / URI\). Furthermore, a resource identifier **MUST NOT** contain a semantic version to convey a version of resource or its representation format.

> _The reason to make a real REST API is to get evolvability … a "v1" is a .... to your API customers, indicating RPC/HTTP \(not REST\)_
>
> _– _[_Roy T. Fielding_](https://twitter.com/fielding/status/376835835670167552)

#### Example

Adding a new action to existing resource with identifier `/greeting` doesn't change its identifier to `/v2/greeting` \(or `/greeting-with-new-action` etc.\).

## Backward-incompatible Changes

A change to _resource identifier_, _resource metadata_, _resource actions_ and _resource relations_ that can't follow the [Rules for Extending](https://adidas-group.gitbooks.io/api-guidelines/content/core-principles/rules-for-extending.html) **MUST** result into a **new resource variant**. Existing resource variant **MUST** be preserved.

A change to _representation format_ **SHOULD NOT** result into a new resource variant.

#### Example

Currently, optional URI Query Parameter `first` on an existing resource `/greeting?first=John&last=Appleseed` needs to be made required. Since this change violates the 3rd rule of extending and could break existing clients a new variant of the resource is created with different URI `/named-greeting?first=John&last=Appleseed`.

### Representation Format Changes

> A representation format is the serialization format \(media type\) used in request and response bodies, and typically it represents a resource or its part, possibly with additional hypermedia controls.

If a change can't follow the Rules for Extending the representation format media type **MUST** be changed. If the media type has been changed the previous media type, **MUST** be available via [Content Negotiation](https://adidas-group.gitbooks.io/api-guidelines/content/message/content-negotiation.html).

If the media type conveys the version parameter, the version parameter **MUST** follow [Semantic versioning](http://semver.org/).

#### Example

Media type _before_ a breaking change:

```
application/vnd.example.resource+json; version=2
```

Media type _after_ a breaking change:

```
application/vnd.example.resource+json; version=3
```

> NOTE: In the case of technical limitations with parsing semicolon-separated HTTP header values, the semantic version might be incorporated in the identifier of the media type, for example: `application/vnd.example.resource.v2+json` .

## API Description Versioning

API Description in the OpenAPI specification format **MUST** have the `version` field. The `version` field **MUST** follow [Semantic versioning](http://semver.org/):

> Given a version number MAJOR.MINOR.PATCH, increment the:
>
> * MAJOR version when you make **incompatible** API changes,
> * MINOR version when you add functionality in a **backwards-compatible** manner
> * PATCH version when you make **backwards-compatible bug fixes**

The API Description version **SHOULD** be updated accordingly to API design change.

#### Example

Following API Description

```yaml
swagger: '2.0'
info:
  version: '2.1.3'
  title: '[Demo] Inventory API'
  description: 'Inventory service API'
```

Has MAJOR version 2, MINOR version 1 and PATCH version 3.

#### Demo

API description \(OAS2\) files demonstrating a proposal of an backward-incompatible change turned into a backward compatible change are available at [Bitbucket \(diff\) ](https://bitbucket.org/apidesigner/demo-versioning-api/pull-requests/1/add-name-parameter/diff)and documented in Apiary:

* [Production version](https://demoversioningproduction.docs.apiary.io/#) as being consumed by clients
* [Development version](https://demoversioningdevelopment.docs.apiary.io/#) proposing a backward incompatible change

#### Recommended Reading 

* [Evolving HTTP APIs](https://www.mnot.net/blog/2012/12/04/api-evolution)





