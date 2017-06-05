# Rate Limiting
The API rate limiting is provided by the selected adidas API management platform – Mashery. 

Rate limit informations are provided in the for of HTTP headers. There are two types of rate limits: **Quota** and **Throttle**. Quota is a limit enforced per a longer period (typically a day). Throttle is the limit of calls per second. 

## Quota Limit
The limit on the number of call per a period (day). The default quota limit is 5000 calls per day. 

#### Example 
Example response to a request over the quota limit: 

```
HTTP/1.1 403 Forbidden
Content-Type: text/xml

X-Error-Detail-Header: Account Over Rate Limit
X-Mashery-Error-Code: ERR_403_DEVELOPER_OVER_RATE

<h1>Developer Over Rate</h1>
```

## Throttle Limit
The limit on the number of call per second. The default throttle limit is 2 calls per second. 

#### Example
Example response to a request over the throttle limit:

```
HTTP/1.1 403 Forbidden
Content-Type: text/xml

Retry-After: 1
X-Error-Detail-Header: Account Over Queries Per Second Limit
X-Mashery-Error-Code: ERR_403_DEVELOPER_OVER_QPS

<h1>Developer Over Qps</h1>
```

> NOTE: The `Retry-After` gives a hint how long before the same request should be repeated (in seconds).


## Detail Information

By default the headers do not contain details about the current usage and quotas. This can be changed in the API management.

#### Example
A successful response with the details about throttle (`X-Plan-QPS`) and quota (`X-Plan-Quota`) rate limits:

```
HTTP/1.1 200 OK

X-Plan-QPS-Allotted: 10
X-Plan-QPS-Current: 1
X-Plan-Quota-Allotted: 1000
X-Plan-Quota-Current: 2
X-Plan-Quota-Reset: Tuesday, June 6, 2017 12:00:00 AM GMT
```
  



