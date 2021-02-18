# Rate Limiting

Rate limit means how many HTTP requests can be made in a given period of time.

The API rate limiting is provided by the selected adidas API Gateway – [Kong](https://konghq.com/kong/). It can be applied to 1 or more endpoints or to the whole API.

Rate limit information is provided in the for of HTTP headers.

## Settings (adidas API Gateway)

The limit on the number of calls per a time period \(second, minute, hour, day, month, year\). The configuration settings have to be obtained from the Non-Functional Requirements of the API to be included as part of the settings of the API Gateway.

A complete reference for configuration can be seen [here](https://adidas.gitbook.io/api-guidelines/rest-api-guidelines/execution/rate-limiting).


## Rate Limit

When this feature is enabled, the API Gateway will send some additional headers back to the client telling what are the limits allowed, how many requests are available and how long it will take until the quota will be restored. For instance (successful response):

```text
RateLimit-Limit: 6
RateLimit-Remaining: 4
RateLimit-Reset: 47
X-RateLimit-Limit-Minute: 10
X-RateLimit-Remaining-Minute: 9
```

## Rate Limit Exceeded

If any of the limits configured in the API Gateway is being reached, it will return a HTTP/1.1 429 status code to the client:

```text
HTTP/1.1 429 Too Many Requests
Content-Type: application/json

Retry-After: 1


{ "message": "API rate limit exceeded" }
```

> NOTE: The response header `Retry-After` gives a hint how long before the same request should be repeated \(in seconds\).

