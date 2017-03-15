# Problem Detail
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
It **SHOULD** have the `type` field with the identifier of the error, in addition it **MAY** have the `instance` field with the URI of the resource in question. If the Problem Detail response has the `status` field it **MUST** have the same value as HTTP Status code from of the response.


```json
{
  "type": "https://adidas-group.com/problems/scv/unauthorized",
  "title": "Authentication required",
  "detail": "Missing authentication credentials for the Greeting resource.",
  "instance": "/greeting",
  "status": 401
}
```

> NOTE: The `type` field is identifier and as such it **MAY** be used to denote additional error codes. Keep in mind that the identifier should be an URI.

## Additional Fields
If needed, the Problem Detail **MAY** include additional fields, refer to [RFC7807](https://tools.ietf.org/html/rfc7807) for details. 

## Validation Errors
When necessary, a Problem Detail response **MAY** include additional error details about the problems that has occurred. 

These additiona errors **MUST** be under the `errors` and **MUST** follow the Problem Detail structure.

#### Example

Request:

```
POST /my_resource HTTP/1.1
Content-Type: application/json

{
  "age": -32,
  "color": "cyan"
}
```

Response:

```
HTTP/1.1 400 Bad Request
Content-Type: application/problem+json
Content-Language: en

{
  "type": "https://example.net/validation_error",
  "title": "Your request parameters didn't validate.",
  "instance": "/my_resource",
  "status": 400,
  
  "errors": [
    {
      "type": "https://example.net/invalid_params",
      "instance": "/age",
      "title": "Invalid Parameter",
      "detail": "age must be a positive integer"
    },
    {
      "type": "https://example.net/invalid_params",
      "instance": "/color",
      "title": "Invalid Parameter",
      "detail": "color must be 'green', 'red' or 'blue'"
    }
  ]
}
```



## Problem Detail and Content Negotiation
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

## No Stack Traces or Server Logs
> _Problem details are not a debugging tool for the underlying implementation; rather, they are a way to expose greater detail about the HTTP interface itself._
>
> _– [RFC7807](https://tools.ietf.org/html/rfc7807)_

A Problem Detail response **MUST NOT** contain a program stack trace or server log for debugging purposes. Instead provide a `logref` field with a reference to the particular server log.

## Working with Problem Detail
There is a whole plethora of libraries working with Problem Detail, for example see [Zalando / Problem](https://github.com/zalando/problem) (Java).