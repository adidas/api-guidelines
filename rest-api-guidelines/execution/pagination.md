# Pagination

A collection resource **SHOULD** provide the [`first`, `last`, `next` and `prev` link](https://tools.ietf.org/html/rfc5988#section-6.2.2)s for navigation within the collection.

## Example

The Collection of Orders using the collection navigation link and `offset` and `limit` query parameters:

```javascript
{
  "_links": {
    "self": { "href": "/orders?offset=100&limit=10" },
    "prev": { "href": "/orders?offset=90&limit=10" },
    "next": { "href": "/orders?offset=110&limit=10" },
    "first": { "href": "/orders?limit=10" },
    "last": { "href": "/orders?offset=900&limit=10" }
  },
  "totalCount": 910,
  "_embedded": {
    "order": [
      { ... },
      { ... },

      ... 
    ]
  }
}
```

