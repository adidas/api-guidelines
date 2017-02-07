# Error Reporting
The [`application/vnd.error+json`](https://github.com/blongden/vnd.error) (vnd.error) MUST be used to communicate details about an error.

> vnd.error media type is intended for use with the HTTP status codes 4xx and 5xx, though this does not exclude it from use in any other scenario.

#### Example
A request is made to retrieve a resource representation:

```
GET /greeting HTTP/1.1
Accept: application/hal+json
```

However in order to make this request the client needs to be authorized. Since the request is made without the authorization credentials the **401 Unauthorized** response is returned together with details using the `vnd.error+json` media type:

```
HTTP/1.1 401 Unauthorized
Content-Type: application/vnd.error+json

{
  "message": "Authentication required. Missing authentication credentials for the target resource.",
  "logref": "REQ0001,
  "_links": {
    "about": {
      "href": "/greeting"
    }
  }
}
```

The `about` link relation type is the resource (URI)  this vnd.error instance is about.


