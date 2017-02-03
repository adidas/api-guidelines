# Message Formats

## Response Message Format
All **response** messages MUST support an [`application/vnd.siren+json`](https://github.com/kevinswiber/siren) (Siren) **based** format. 

The Siren format MUST NOT be used **directly**, instead it MUST be used as the **base format** for every application or domain-specific format to convey specific semantics. E.g. `application/vnd.example.siren+json`

### Error Response Format
Siren-based format MUST be used to communicate a problem (error). This format SHOULD be application or domain-specific accordingly to non-error response format.  


## Request Message Format
Data body **request** messages MUST support a [`application/json`](http://www.json.org) (JSON) **based** format. 

The JSON format MUST NOT be used **directly**, instead it MUST be used as the **base format** for every application or domain-specific format to convey specific semantics. E.g. `application/vnd.example+json`.

Data body **request** messages SHOULD also support the [`application/x-www-form-urlencoded`](https://tools.ietf.org/html/rfc1866#section-8.2.1) (URL Encoded) format.



