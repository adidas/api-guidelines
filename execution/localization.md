# Localization

## Language Variants
If a resource has multiple language variants and the difference between variantsis only in the language of human readable fields then the [`Accept-Language`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Accept-Language) request HTTP header **SHOULD** be used to communicate the desired language variant.

#### Example

```
GET /article HTTP/1.1
Accept-Language: en,en-US,fr;q=0.6
```

```
HTTP/1.1 200 OK
Content-Type: application/hal+json;charset=UTF-8 
Content-Language: en
Vary: Accept-Language

...
```

## Language or Country-specific Data Structure