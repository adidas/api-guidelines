# Authentication

Every API exposed outside of the adidas network **MUST** be available to authenticated clients only. Every unauthenticated HTTP request to exposed API **MUST** result in the **403 – Forbidden** HTTP Status code.

There are two was how to authenticate a call to an API: 

1. OAuth2 token
1. API key

# OAuth 2 Token
Every API that requires user authentication or authorization **MUST** use OAuth 2 tokens to authenticate the user.

## API Key
If an API doesn't need to authorize users the API **MAY** use simple API token instead of the OAuth 2 token. The key **MUST** be provided in the `Adidas-API-Key` HTTP header.

#### Example

Request:

```
GET /demo-approval-api/ HTTP/1.1
Adidas-API-Key: 9kfapap6612jkfd3ja9323q
Host: adidas.api.mashery.com
```



