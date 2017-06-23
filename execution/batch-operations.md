# Batch Operations

## Processing Similar Resources
An operation that needs to process several similar resource in bulk **SHOULD** use a collection resource with the appropriate HTTP Request Method. When processing existing resource the request message body **MUST** contain the URLs of the respective resources being processed.

#### Example
##### Create Multiple Orders at Once

```
POST /orders
Content-Type: application/json

{
  "order": [
    {
      "itemCount": 42
    },
    {
      "itemCount": 2
    }
  ]
}
```


##### Update Multiple Orders at Once
> NOTE: The self link relation clearly identifies the existing resource being edited.

```
PATCH /orders
Content-Type: application/json

{
  "order": [
    {
      "_links": {
        "self": { "href": "/order/1"}
      },
      "itemCount": 42
    },
    {
      "_links": {
        "self": { "href": "/order/2"}
      },      
      "itemCount": 2
    }
  ]
}
```

## Results of Bulk Operation
Every bulk operation **MUST** be atomic and treated as any other operation.

> _The server must implement bulk requests as atomic. If the request is for creating 10 addresses, the server should create all 10 addresses before returning a successful response code. The server should not commit changes partially in the case of failures._


## DO NOT USE "POST Tunneling"
Every API **MUST** avoid tunneling multiple HTTP Request using one POST request. Instead provide an application-specific resource to process the batch request.


## Non-atomic Bulk Operations
Non-atomic bulk operations are **strongly discouraged** as they bring additional burden and confusion to the client and are difficult to consume, debug, maintain and evolve over the time.

The suggestion is to **split** a non-atomic operation into several atomic operations. The cost of few more calls will be greatly outweighed but the cleaner design, clarity and easier maintainability.

However, in such an operation has to be provided such an non-atomic bulk operation **MUST** conform to the following guidelines.

1. Non-atomic bulk operation **MUST** return a success status code (e.g. **200 OK**) only if every and all sub-operation succeded.

1. If any single one sub-operation fails the whole non-atomic bulk operation **MUST** return the respective **4xx** or **5xx** status code.

1. In the case of a failure the response **MUST** contain the [problem detail](https://adidas-group.gitbooks.io/api-guidelines/content/message/error-reporting.html) information about every sub-operation that has failed.

1. **The client MUST be aware that the operation is non-atomic and the even the operation might have failed some sub-operations were processed successfully.**


#### Example

Non-atomic request for creating four orders:

```
POST /orders
Content-Type: application/json

{
  "order": [
    {
      "itemCount": 42
    },
    {
      "itemCount": -100
    },        
    {
      "itemCount": 42
    },
    {
      "itemCount": 1.3232
    }
  ]
}
```

And the error response: 

```
HTTP/1.1 400 Bad Request
Content-Type: application/problem+json

{
  "type": "https://example.net/partial_operation_failure",
  "title": "Partial Failure",
  "detail": "Some orders couldn't be created, other orders were created.",
  
  "errors": [
    {
      "type": "https://example.net/invalid-params",
      "instance": "/orders/1",
      "title": "Invalid Parameter",
      "detail": "item_count must be a positive integer",
      "status": 400
    },
    {
      "type": "https://example.net/invalid-params",
      "instance": "/orders/3",
      "title": "Invalid Parameter",
      "detail": "item_count must be a positive integer",
      "status": 400
    }
  ],

  "processed": ...
}

```

The `processed` field should contain the result of processed sub-operations as if they were returned in a 200 OK.





