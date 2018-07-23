# Know your HTTP
Every API using HTTP **MUST** conform to the HTTP protocol semantics as defined in the following RFCs:

> 1. [RFC 7230, HTTP/1.1: Message Syntax and Routing](https://tools.ietf.org/html/rfc7230)
> 1. [RFC 7231, HTTP/1.1: Semantics and Content](https://tools.ietf.org/html/rfc7231)
> 1. [RFC 7232, HTTP/1.1: Conditional Requests](https://tools.ietf.org/html/rfc7232)
> 1. [RFC 7233, HTTP/1.1: Range Requests](https://tools.ietf.org/html/rfc7233)
> 1. [RFC 7234, HTTP/1.1: Caching](https://tools.ietf.org/html/rfc7234)
> 1. [RFC 7235, HTTP/1.1: Authentication](https://tools.ietf.org/html/rfc7234)

## HTTP Protocol Quick Start
The understanding of HTTP starts with the understanding of [HTTP message](https://developer.mozilla.org/en-US/docs/Web/HTTP/Messages) and its routing.

Once you are familiar with the structure of an HTTP/1.1 message learn about the _HTTP request methods, HTTP response status codes and HTTP headers_. Each _HTTP request method, status code and header_ has its semantics defined, and every API MUST adhere to it.

Follow the [Robustness Principle](core-principles/robustness.md). Use only the _HTTP request methods, response codes, and HTTP headers_ you understand but be liberal in accepting others, but make sure to follow those mentioned in the guidelines.

For quick information on _HTTP headers, media-types, methods, relations and status codes_, all summarized and linked to their specification visit [KNOW YOUR HTTP * WELL](https://github.com/for-GET/know-your-http-well).

Alternatively, you can download HTTP cheat sheets at [HTTP posters](https://github.com/bigcompany/know-your-http).
