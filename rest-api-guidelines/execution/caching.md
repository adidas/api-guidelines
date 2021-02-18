# Caching

Every API implementation **SHOULD** return both the cache expiry information \([`Cache-Control` HTTP header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control)\) and specific resource version information \([`ETag` HTTP Header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/ETag)\).

## Cache-Control

Every API implementation's response **SHOULD** include information about cache-ability and cache expiration of the response. For HTTP 1.1 this is achieved using the `Cache-Control` header.

### Common Cache-Control Scenarios

Two, most common scenarios for controlling the cache-ability of a response includes \(1\) Setting expiration and revalidation and \(2\) disabling the caching of a response. Refer to the [Cache-Control Documentation](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control) for additional controls.

#### 1. Cache Expiration & Revalidation

The common scenario to set cache expiration and revalidation policy is to use the `max-age` and `must-revalidate` directives:

```text
HTTP/1.1 200 OK
Date: Mon, 19 Aug 2017 00:00:00 CEST
Last-Modified: Mon, 19 Aug 2017 00:00:00 CEST
Cache-Control: max-age=3600,must-revalidate
Content-Type: application/hal+json; charset=UTF-8

...
```

#### 2. Disabling Cache

To disable caching completely API implementation **SHOULD** use the `no-cache` and `no-store` directives:

```text
HTTP/1.1 200 OK
Date: Mon, 19 Aug 2017 00:00:00 CEST
Last-Modified: Mon, 19 Aug 2017 00:00:00 CEST
Cache-Control: no-cache, no-store, must-revalidate
Content-Type: application/hal+json; charset=UTF-8

...
```

## ETag

Every API implementation's response to a [cacheable request](https://github.com/for-GET/know-your-http-well/blob/master/methods.md#cacheable) **SHOULD** include the [`ETag` HTTP Header](https://tools.ietf.org/html/rfc7232#section-2.3) to identify the specific version of the returned resource.

Every API client **SHOULD** use [`If-None-Match` HTTP header](https://tools.ietf.org/html/rfc7232#section-3.2) whenever it's performing a cacheable request. The value of `If-None-Match` should be the value of the `ETag` header stored from a previous request. The client **MUST** be ready to handle the **304 Not Modified** response from the server to use the legal copy.

#### How ETag works

ETags are unique identifiers for a particular version of a resource found by a URL. They are used for cache validation, to check for modifications quickly.

A client requests a resource from the server at a particular URI. The server responds with the specific ETag value in the HTTP ETag header field. ETag and the resource will be stored locally by the client. Subsequent requests from the client are done with the If-None-Match header, which now contains the ETag value from the previous request. The server now compares the values. If they are the same, it responds with HTTP Status Code 304 Not Modified. If not, the resource is sent.

