# Siren
[Siren](https://github.com/kevinswiber/siren) is a simple, JSON-based format for representing entities and hypermedia controls. It is capable of transferring a JSON representation of a resource, related resources, link relations and actions ([HATEOAS](https://en.wikipedia.org/wiki/HATEOAS) controls).

Every Siren API response message SHOULD contain the `properties` field. If present, a representation of an entity MUST be under the `properties` field.

A Siren message SHOULD contain the `class` field to denot 


## Example
At minimum a response message might include some properties of resource it represents. In Siren, all the resource properties (data) are nested under the `properties` key.

A minimal Siren document that transfer some data looks like:

```json
{
  "properties": {
    ...
  }
}
```

Let's say the example response  should represent an "Order" resource:

```json
{
  "properties": {
    "orderNumber": 42,
    "itemCount": 3,
    "status": "pending"
  }
}
```



