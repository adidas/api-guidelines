# Message Formats

## Response Message Format
All response messages MUST support the [`application/vnd.siren+json`](https://github.com/kevinswiber/siren) (Siren) format. 

The format MUST not be used directly but instead it MUST be used as the base format for every application or domain-specific format.

### Error Response Format
The [`application/problem+json`](https://tools.ietf.org/html/rfc7807) (Problem Detail) MUST be used in conjunction with Siren to communicate details about an error.

## Request Message Format
[`application/x-www-form-urlencoded`](https://tools.ietf.org/html/rfc1866#section-8.2.1)
[`application/json`](http://www.json.org)





