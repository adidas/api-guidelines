# Query Requests with Large Inputs
While HTTP doesn't impose any limit on the length of a URI, some implementation of server or client might have difficulties handling long URIs (usually URIs with many or large query parameters).

Every endpoint with such a URI **MUST** use the HTTP **POST** Request Method and send the query string in HTTP Request Message body using the `application/x-www-form-urlencoded` media type.


#### Example

```
POST /orders HTTP/1.1
Content-Type: application/x-www-form-urlencoded

search=attributes&color=white&size=56&...
```


> _NOTE: Since this operation is safe and idempotent, using the POST method violates the HTTP protocol semantics and results in loss of cache-ability._
