# Separate Concerns
Every API using HTTP/S API MUST clearly follow the concern separation of a HTTP message:

1. A _resource identifier_–URI MUST be used to indicate **identity** only (related: [Content Negotiation](protocol/content-negotiation), [Changes and Versioning](core-principles/versioning.md))
1. _HTTP request method_ MUST be used to communicate the **action semantics** (intent and safety)
1. _HTTP response status_ code MUST be used to communicate the **information about the result** of the attempt to understand and satisfy the request
1. _HTTP message body_ MUST be used to transfer the **message content**
1. _HTTP message headers_ MUST be used to transfer the **metadata** about the message and its content
1. _URI query parameter_ SHOULD NOT be used to transfer metadata

> NOTE: Rule No.1 means there MUST be NO information about the media type or version of resource in the URI (e.g. `/greeting.json` or `/v2.1.3/greeting` are **illegal**).

---

> _Keep things simple while designing by separating the concerns between the different parts of the request and response cycle. Keeping simple rules here allows for greater focus on larger and harder problems._
>
> _Requests and responses will be made to address a particular resource or collection. Use the path to indicate identity, the body to transfer the contents and headers to communicate metadata. Query params may be used as a means to pass header information also in edge cases, but headers are preferred as they are more flexible and can convey more diverse information._
>
> _– [Heroku HTTP API Design Guide](https://geemus.gitbooks.io/http-api-design/content/en/foundations/separate-concerns.html)_