# Message Formats

## Response Message Format
All **response** messages MUST support the [`application/vnd.siren+json`](https://github.com/kevinswiber/siren) (Siren) format. 

The Siren format MUST NOT be used **directly**, instead it MUST be used as the **base format** for every application or domain-specific format to convey specific semantics. E.g. `application/vnd.example.siren+json`

### Error Response Format
A
The [`application/problem+json`](https://tools.ietf.org/html/rfc7807) (Problem Detail) MUST be used in conjunction with Siren to communicate details about an error.

## Request Message Format
Data body **request** messages MUST support the [`application/json`](http://www.json.org) (JSON) format. 

The JSON format MUST NOT be used **directly**, instead it MUST be used as the **base format** for every application or domain-specific format to convey specific semantics. `application/vnd.example+json`

Data body **request** messages SHOULD also support the [`application/x-www-form-urlencoded`](https://tools.ietf.org/html/rfc1866#section-8.2.1) (URL Encoded) format.








