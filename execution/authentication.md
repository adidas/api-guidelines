# Authentication
Every API exposed outside of the adidas network **MUST** be available to authenticated clients only. Every unauthenticated HTTP request to exposed API **MUST** result in the **403 – Forbidden** HTTP Status code.

Based on whether user authorization is required an API call can be authenticated in two ways:

1. OAuth2 token
1. API key

# OAuth 2 Token
Every API that requires user authentication or authorization **MUST** use OAuth 2 tokens to authenticate the client.

## API Key
An API **MAY** use simple the API token instead of the OAuth 2 token if it doesn't need to authorize the user . The key **MUST** be provided in the `Adidas-API-Key` HTTP header.

#### Example

Request:

```
GET /demo-approval-api/ HTTP/1.1
Adidas-API-Key: 9kfapap6612jkfd3ja9323q
Host: adidas.api.mashery.com
```

> NOTE: See more details in the [[Demo] Approval API](http://docs.demoapprovalapi.apiary.io) example.
