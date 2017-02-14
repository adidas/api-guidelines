# Message Formats

## Response Message Format
All **response** messages **MUST** support an [`application/hal+json`](http://stateless.co/hal_specification.html) (HAL) format.

### Error Response Format
The [`application/problem+json`](https://tools.ietf.org/html/rfc7807) (Problem Detail) **MUST** be used to communicate details about an error.

## Request Message Format
Data body **request** messages **SHOULD** support a [`application/json`](http://www.json.org) (JSON) format. Where applicable, the data body request message **SHOULD** also support the `application/hal+json` format.

Data body **request** messages **SHOULD** also support the [`application/x-www-form-urlencoded`](https://tools.ietf.org/html/rfc1866#section-8.2.1) (URL Encoded) format.


