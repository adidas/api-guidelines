# Caching
Include an ETag header in all responses, identifying the specific version of the returned resource. This allows users to cache resources and use requests with this value in the If-None-Match header to determine if the cache should be updated.


ETag
ETags are unique identifiers for a specific version of a resource found by a URL. They are used for cache validation, to quickly check for modifications.
This is how it works:
A client requests a resource from the serve at a specific URI. The server responds with the specific ETag value in the HTTP ETag header field. This and the resource will be stored locally by the client.
subsequent requests from the client are done with the If-None-Match header, which now contains the ETag value from the previous request
the server now compares the values. If they are the same, it responds with HTTP Status Code 304. If not, the resource is sent.
Further reading
Find below a list of great articles on the topic Caching
https://www.mnot.net/cache_docs/
http://restcookbook.com/Basics/caching/
http://odino.org/rest-better-http-cache/
https://www.subbu.org/blog/2005/01/http-Caching