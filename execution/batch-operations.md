# Batch Operations
> _When a client needs to submit a number of similar requests for different resources, as long as the operations on each resource are the same and the resources are “similar,” you can combine them into a single operation on a collection resource_
>
> _– [RESTful Web Services Cookbook]()_

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
      "item_count": 42
    },
    {
      "item_count": 2
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
      "item_count": 42
    },
    {
      "_links": {
        "self": { "href": "/order/2"}
      },      
      "item_count": 2
    }
  ]
}
```




