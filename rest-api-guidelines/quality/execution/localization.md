# Localization

## Language Variants

If a resource has multiple language variants and the difference between variants is only in the language of human-readable fields, then the [`Accept-Language`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Accept-Language) request HTTP header **SHOULD** be used to select the desired language variant.

### Example

```text
GET /article HTTP/1.1
Accept-Language: en,en-US,fr;q=0.6
```

```text
HTTP/1.1 200 OK
Content-Type: application/hal+json;charset=UTF-8 
Content-Language: en
Vary: Accept-Language

...
```

## Language or Country-specific Data Structure

If the difference between language or country specific variants of a resource is bigger than just in the content of human readable strings, for example, the data structure of the resource representation is different, then a query parameter **SHOULD** be used to communicate the requested variant.

### Example

```text
GET /article?market=en_US HTTP/1.1
```

```text
HTTP/1.1 200 OK
Content-Type: application/hal+json;charset=UTF-8 
Content-Language: en
Vary: Accept-Language

...
```

