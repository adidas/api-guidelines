# Choosing Fields & Embedded Resources


## Choosing Response Message Fields
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
    "self": {
      "href": "/orders/1234"
    },
    "author": {
      "href": "/users/john"
    }
  },
  "orderNumber": 1234,
  "status": "pending"
}
```
