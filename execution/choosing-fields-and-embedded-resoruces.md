# Choosing Fields & Embedded Resources


## Response Message Fields
Every request that may result into a response with a non-trivial body **SHOULD** implement the the `fields` query parameter. If provided, the value of this parameter must be a comma-separated list of top-level response message fields. 

Upon receiving such a request, in the event of a 2xx response, the service **SHOULD** respond with a message that includes only top-level fields specified in the `fields` parameter. This includes HAL-specific fields (`_links` and `_embedded`).

#### Example
Retrieve only some details of an Order resource:

HTTP Request
```
GET /order/1234?fields=_links,orderNumber,status HTTP/1.1
Accept: application/hal+json
```

HTTP Response
```
HTTP/1.1 200 OK
Content-Type: application/hal+json

{
  "_links": {
    "self": { "href": "/orders/1234" },
    "author": { "href": "/users/john" },
    "items": [ ... ]
  },
  "orderNumber": 1234,
  "status": "pending"
}
```

## Embedded Resources
Similarly to the the `fields` query parameter, every request that might result into a response containing related embedded resource representations **SHOULD** implement the `embedded` query parameter. If, provided the value of the `embedded` query parameter **MUST** be comma-separated list of relation identifiers.

Upon receiving such a request, in the event of a 2xx response, the service **SHOULD** respond with a message that "embeds" (see HAL `_embedded` field) only the related resources specified in the `embedded` parameter. 


#### Example
Embed only information about the Author of an Order resource, we are not interested in Items that are in this order.

HTTP Request

```
GET /order/1234?embed=author HTTP/1.1
Accept: application/hal+json
```

HTTP Response
```
HTTP/1.1 200 OK
Content-Type: application/hal+json

{
  "_links": {
    "self": { "href": "/orders/1234" },
    "author": { "href": "/users/john" },
    "items": [ ... ]
  },
  "orderNumber": 1234,
  "itemCount": 42,
  "status": "pending",
  "_embedded": {
    "author": {
      "_links": { "self": "/users/john" },
      "name": "John Appleseed",
      "email": "john@apple.com"
    }
  }
}
```






