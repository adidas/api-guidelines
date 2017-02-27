# Rate Limiting
A HTTP Response to an HTTP Request API Endpoint that is under a rate limiting policy **MUST** include the following HTTP headers:

- `Rate-Limit-Limit`: The rate limit ceiling for that given endpoint
- `Rate-Limit-Remaining`: The number of requests left

An API **MUST** respond with the **429 Too Many Requests** HTTP Status code when a user agent exceeded the number for available calls. In addition, it **SHOULD** include the [`Retry-After`](https://tools.ietf.org/html/rfc7231#section-7.1.3) in the response. The `Retry-After` **MUST** represent the remaining time before the rate limit resets.


#### Example

```
HTTP/1.1 429 Too Many Requests
Content-Type: application/problem+json
Content-Language: en
Rate-Limit-Limit: 1000
Rate-Limit-Remaining: 0
Retry-After: 3600

{
    "type": "https://adidas-group.com/problems/rate_limit_exceeded",
    "title": "Too Many Requests",
    "detail": "The allowed rate limit has been exceeded, please try again in 3600 seconds",
    "status": 429
}
```