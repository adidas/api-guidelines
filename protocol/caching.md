# Caching
Every API implementation response to a [cacheable request]((https://github.com/for-GET/know-your-http-well/blob/master/methods.md#cacheable) SHOULD include the [`ETag` HTTP Header](https://tools.ietf.org/html/rfc7232#section-2.3) to identify the specific version of the returned resource.

Every API client SHOULD use [`If-None-Match` HTTP header](https://tools.ietf.org/html/rfc7232#section-3.2) whenever it's performing a cacheable request. The value of `If-None-Match` should be the value of the `ETag` header stored from a previous request. The client MUST be able to handle the **304 Not Modified** response from the server.

#### How ETag works
ETags are unique identifiers for a specific version of a resource found by a URL. They are used for cache validation, to quickly check for modifications.

A client requests a resource from the serve at a specific URI. The server responds with the specific ETag value in the HTTP ETag header field. This and the resource will be stored locally by the client. Subsequent requests from the client are done with the If-None-Match header, which now contains the ETag value from the previous request. The server now compares the values. If they are the same, it responds with HTTP Status Code 304 Not Modified. If not, the resource is sent.
