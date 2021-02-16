# Caching

> From an architectural point of view, the API cache strategy can be defined at two main levels: backend service and API Gateway. These guidelines handle the cache strategy in the backend service as part of the API implementation. Please consider additional cache settings to be defined in the **API Gateway** can dramatically improve the performance and API consumer experience but they have to be defined in a specific way in the adidas product.

As a general guideline, every API implementation **SHOULD** return both the cache expiry information \([`Cache-Control` HTTP header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control)\) and specific resource version information \([`ETag` HTTP Header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/ETag)\).


## Cache-Control 

Every API implementation's response **SHOULD** include information about cache-ability and cache expiration of the response. For HTTP 1.1 this is achieved using the `Cache-Control` header.


### Settings

#### adidas API Gateway
The configuration of cache in the adidas API Gateway is mainly based on:

- Cacheable HTTP methods
- When to cache. Response content types, headers to be considered for the cache key, relevant query parameters, etc.
- Expiration time, meaning the number of seconds to keep resources in the storage backend.
- Strategy. This means, which is the backing data store in which to hold cache entities. The only accepted values are `memory` and `redis`.

> A complete reference for configuration can be seen [here](https://docs.konghq.com/hub/kong-inc/proxy-cache/).

#### API Consumer
Clients **SHOULD** be capable of using `max-age` and `max-stale` headers to exclude the entity from being cached entirely or request stale copies of data if necessary.



### Common Cache-Control Scenarios

Most common scenarios for controlling the cache-ability of a response includes:

1. Setting expiration and revalidation.
2. Disabling the caching of a response. Refer to the [Cache-Control Documentation](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control) for additional information.

> Remember the adidas API Gateway identifies the status of the request’s proxy cache behavior via the `X-Cache-Status` header. There are several possible values for this header:

> - `Miss` The request could be satisfied in cache, but an entry for the resource was not found in cache, and the request was proxied upstream.
> - `Hit` The request was satisfied and served from cache.
> - `Refresh` The resource was found in cache, but could not satisfy the request, due to Cache-Control behaviors or reaching its hard-coded cache_ttl threshold.
> - `Bypass` The request could not be satisfied from cache based on plugin configuration.

#### 1. Cache Expiration & Revalidation
You **SHOULD** define the expiration time and the case for revalidation in your API.

`max-age` is the oldest that a response can be, as long as the Cache-Control from the origin server indicates that it is still fresh. The value means seconds.

From the semantic point of view `no-cache` and `max-age=0`, `must-revalidate` indicates same meaning: The backend service has to be contacted to get a stale result.

Clients can cache a resource but must revalidate each time before using it. This means HTTP request occurs each time though, it can skip downloading HTTP body if the content is valid.

The common scenario to set cache expiration and revalidation policy is to use the `max-age`, `must-revalidate` or `max-age` as part of the `Cache-Control` directives.

The TTL is set to 5 minutes:

```text
Cache-Control: max-age=300
```

The cached response has to be refreshed:

```text
Cache-Control: must-revalidate
```

#### 2. Disabling Cache

To disable caching completely the API consumer implementation **SHOULD** use the `no-cache` directive:

```text
Cache-Control: no-cache
```


## ETag

Every API implementation's response to a [cacheable request](https://github.com/for-GET/know-your-http-well/blob/master/methods.md#cacheable) **SHOULD** include the [`ETag` HTTP Header](https://tools.ietf.org/html/rfc7232#section-2.3) to identify the specific version of the returned resource.

Every API client **SHOULD** use [`If-None-Match` HTTP header](https://tools.ietf.org/html/rfc7232#section-3.2) whenever it's performing a cacheable request. The value of `If-None-Match` should be the value of the `ETag` header stored from a previous request. The client **MUST** be ready to handle the **304 Not Modified** response from the server to use the legal copy.

#### How ETag works

ETags are unique identifiers for a particular version of a resource found by a URL. They are used for cache validation, to check for modifications quickly.

A client requests a resource from the server at a particular URI. The server responds with the specific ETag value in the HTTP ETag header field. ETag and the resource will be stored locally by the client. Subsequent requests from the client are done with the If-None-Match header, which now contains the ETag value from the previous request. The server now compares the values. If they are the same, it responds with HTTP Status Code 304 Not Modified. If not, the resource is sent.

