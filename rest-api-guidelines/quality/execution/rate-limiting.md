# Rate Limiting

The API rate limiting is provided by the selected adidas API management platform – Mashery.

Rate limit information is provided in the for of HTTP headers. There are two types of rate limits: **Quota** and **Throttle**. The quota is a limit enforced per a longer period \(typically a day\). The throttle is the limit of calls per second.

## Quota Limit

The limit on the number of calls per a period \(day\). The default quota limit is 5000 calls per day.

### Example

Example response to a request over the quota limit:

```text
HTTP/1.1 403 Forbidden
Content-Type: application/problem+json

X-Error-Detail-Header: Account Over Rate Limit
X-Mashery-Error-Code: ERR_403_DEVELOPER_OVER_RATE

{
  "title": "Rate Limit Exceeded",
  "detail": "Account Over Rate Limit"
}
```

## Throttle Limit

The limit on the number of calls per second. The default throttle limit is two calls per second.

### Example

Example response to a request over the throttle limit:

```text
HTTP/1.1 403 Forbidden
Content-Type: application/problem+json

Retry-After: 1
X-Error-Detail-Header: Account Over Queries Per Second Limit
X-Mashery-Error-Code: ERR_403_DEVELOPER_OVER_QPS

{
  "title": "Quota Limit Exceeded",
  "detail": "Account Over Queries Per Second Limit"
}
```

> NOTE: The `Retry-After` gives a hint how long before the same request should be repeated \(in seconds\).

## Detail Information

By default, the headers do not contain details about the current usage and quotas. The default can be changed in the API management.

### Example

A successful response with the details about throttle \(`X-Plan-QPS`\) and quota \(`X-Plan-Quota`\) rate limits:

```text
HTTP/1.1 200 OK

X-Plan-QPS-Allotted: 10
X-Plan-QPS-Current: 1
X-Plan-Quota-Allotted: 1000
X-Plan-Quota-Current: 2
X-Plan-Quota-Reset: Tuesday, June 6, 2017 12:00:00 AM GMT
```

