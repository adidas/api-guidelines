# Error Reporting
The [`application/problem+json`](https://tools.ietf.org/html/rfc7807) (Problem Detail) **MUST** be used to communicate details about an error.

Problem Detail is intended for use with the HTTP status codes 4xx and 5xx. Problem Detail **MUST NOT** be used with 2xx status code responses.

At minimum, any Problem Detail response **MUST** have the `title` and `detail` fields. 

#### Example

```json
{
  "title": "Authentication required",
  "detail": "Missing authentication credentials for the Greeting resource."
}
```

## Optional Fields
It **SHOULD** have the `type` field with the identifier of the error, in addition it **MAY** have the `instance` field with the URI of the resource in question. If the Problem Details responses has the `status` field it **MUST** have the same value as HTTP Status code from of the response.


```json
{
  "type": "https://adidas-group.com/problems/scv/unauthorized",
  "title": "Authentication required",
  "detail": "Missing authentication credentials for the Greeting resource.",
  "instance": "/greeting",
  "status": 401
}
```

## Additional Fields
If needed, the Problem Detail **MAY** include additional fields, refer to [RFC7807](https://tools.ietf.org/html/rfc7807) for details. 


#### Example
A request is made to retrieve a resource representation:

```
GET /greeting HTTP/1.1
Accept: application/hal+json
```

However in order to make this request the client needs to be authorized. Since the request is made without the authorization credentials the **401 Unauthorized** response is returned together with details using the `application/problem+json` media type:

```
HTTP/1.1 401 Unauthorized
Content-Type: application/problem+json
Content-Language: en

{
  "type": "https://adidas-group.com/problems/scv/unauthorized",
  "title": "Authentication required",
  "detail": "Missing authentication credentials for the Greeting resource.",
  "instance": "/greeting",
  "status": 401
}
```




