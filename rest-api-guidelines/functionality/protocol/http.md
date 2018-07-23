# HTTP

Every API MUST support [HTTP/1.1](https://tools.ietf.org/html/rfc7230) and **MUST** adhere to its **semantic**.

## HTTP Protocol Quick Start

The understanding of HTTP starts with the understanding of [HTTP message](https://developer.mozilla.org/en-US/docs/Web/HTTP/Messages) and its routing.

Once you are familiar with the **HTTP message structure** learn about the **HTTP request methods**, **HTTP response status codes** and **HTTP headers**.

Each HTTP request method, status code, and header have its semantics defined, and every API **MUST** strictly adhere to it.

Follow the [Robustness Principle](https://github.com/adidas-group/api-guidelines/tree/af88d15fd04ef18d6724fa65943901aab7328e7f/rest/protocol/core-principles/robustness.md). Use only the HTTP request methods, response codes and HTTP headers you understand, be liberal in accepting others.

## Know HTTP

The following documents are great overview of the HTTP protocol and related standards:

* [HTTP Headers](https://github.com/for-GET/know-your-http-well/blob/master/headers.md)
* [HTTP Request Methods](https://github.com/for-GET/know-your-http-well/blob/master/methods.md)
* [HTTP Response Status Codes](https://github.com/for-GET/know-your-http-well/blob/master/status-codes.md)
* [HTTP Link Relations](https://github.com/for-GET/know-your-http-well/blob/master/relations.md)

Alternatively, you can download HTTP cheat sheets at [HTTP posters](https://github.com/bigcompany/know-your-http).

## RFCs

The HTTP protocol semantics is defined in the following RFCs:

> 1. [RFC 7230, HTTP/1.1: Message Syntax and Routing](https://tools.ietf.org/html/rfc7230)
> 2. [RFC 7231, HTTP/1.1: Semantics and Content](https://tools.ietf.org/html/rfc7231)
> 3. [RFC 7232, HTTP/1.1: Conditional Requests](https://tools.ietf.org/html/rfc7232)
> 4. [RFC 7233, HTTP/1.1: Range Requests](https://tools.ietf.org/html/rfc7233)
> 5. [RFC 7234, HTTP/1.1: Caching](https://tools.ietf.org/html/rfc7234)
> 6. [RFC 7235, HTTP/1.1: Authentication](https://tools.ietf.org/html/rfc7234)

