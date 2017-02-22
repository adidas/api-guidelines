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




