# Status Codes

Every API **MUST** use the appropriate [HTTP Status Codes](https://github.com/for-GET/know-your-http-well/blob/master/status-codes.md) to communicate the result of a request operation.

Every API designer, implementer and consumer **MUST** understand the semantic of the HTTP Status Code she is using.

At a minimum everyone **MUST** be familiar with the semantics of ["Common" HTTP Status Codes](https://github.com/for-GET/know-your-http-well/blob/master/status-codes.md#common).

## Example

## Use Codes 4xx or 5xx to Communicate Errors

A request:

```text
GET /orders/1234 HTTP/1.1
...
```

resulting in the **200 OK** response, when the requested resource \(as identified by request URI\) couldn't be found:

```text
HTTP/1.1 200 OK
Content-Type: application/json
...


{
    "code": "NOT_FOUND_ERR_CODE"
    "message" "Order 1234 wasn't found"
}
```

is **not acceptable**.

Instead the

```text
HTTP/1.1 404 Not Found
...
```

should be returned.

## Recommended Reading

* [How to Think About HTTP Status Codes](https://www.mnot.net/blog/2017/05/11/status_codes)

