# HAL
> HAL is a simple format that gives a consistent and easy way to hyperlink between resources in your API.

This is an informal introduction for the HAL media type. For details see [HAL - Hypertext Application Language Specification](http://stateless.co/hal_specification.html).

## Simple Document Example
The simplest Hal document looks like an empty JSON (it is an empty JSON!):

```json
{
}
```

A document representing a "Greeting" resource might look like:

```json
{
  "message": "Hello World!",
  "_links": {
    "self": {
      "href": "/greeting"
    }
  }
}
```
The field `_links` has a special meaning in HAL. It denotes a list of link relations - a pair if a relation identifier and a link (URI). 

These link relations are used to express the relation of a resource with other resources.

In our case the "Greeting" resource isn't related to other resources but itself-hence the `self` relation pointing to the Greeting resource. 

It is **customary** for every resource representation to include the `self` link relation. 

## Relation Example
A more complex document example could be an "Order" resource that has a related resource "Author" (a person who created the order. It might look like:

```json
{
  "_links": {
    "self": {
      "href": "/orders/1234"
    },
    "author": {
      "href": "/users/john"
    }
  },
  "orderNumber": 1234,
  "itemCount": 42,
  "status": "pending"
}
```


#### Real-world Examples

Some APIs using HAL:

- [Amazon AppStream REST API](http://docs.aws.amazon.com/appstream/latest/developerguide/appstream-api-rest.html)
- [FoxyCart](https://wiki.foxycart.com/v/2.0/start)
- [Clarify.io](http://docs.clarify.io/overview/)
- [University of Oxford / Mobile Oxford](http://api.m.ox.ac.uk/browser/#/)