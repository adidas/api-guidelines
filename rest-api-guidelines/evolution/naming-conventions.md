# Naming Conventions

## General Naming Rules

* Use American English
* Don't use acronyms
* Use `camelCase` unless stated otherwise
* Reconcile terms with adidas CDM

Every identifier **MUST** be in American English and written in `lowercase`. An identifier **SHOULD NOT** contain acronyms. CamelCase \(`camelCase`\) **MUST** be used to delimit combined words.

## URI

Every URI **MUST** follow the General Rules except for the `camelCase` rule. Instead, a hyphen \(`-`\) **SHOULD** be used to delimit combined words \(kebab-case\). Besides, a URI **MUST NOT** end with a trailing slash \(`/`\).

#### Example

A well-formed URI:

```text
/system-orders/1234/author
```

### Query Parameters and Path Fragments

Every URI query parameter or fragment **MUST** follow the General Rules. Also, they **MUST NOT** clash with the [reserved query parameter names](reserved-identifiers.md#query-parameters).

### URI Template Variables

In addition to General Naming Rules, URI Template Variable names **MUST** follow the [RFC6570](https://tools.ietf.org/html/rfc6570#section-2.3). That is, the variable names can consist only from `ALPHA / DIGIT / "_" / pct-encoded`.

> NOTE: Per RFC6570 Hyphen \(`-`\) is NOT legal URI Template variable name character.

#### Example

A well-formed URI Template Variable:

```text
/system-orders/{orderId}/author
```

## Representation Format Fields

Every representation format field **MUST** conform to the General Naming Rules.

#### Example

A well-formed resource representation:

```javascript
{
  "_links": {
    "self": {
      "href": "/orders/1234"
    },
    "author": {
      "href": "/users/john"
    }
  },
  "orderNumber": 1234,
  "itemCount": 42,
  "status": "pending"
}
```

## Relation Type Identifier

Every custom [relation identifier](https://github.com/for-GET/know-your-http-well/blob/master/relations.md) **MUST** be in `lowercase` with words separated by the hyphen \(`-`\).

#### Example

A well-formed resource representation with custom relation `fulfillment-provider`:

```javascript
{
  "_links": {
    "fulfillment-provider": {
      "href": "/users/natalie"
    }
  }
}
```

## HTTP Headers

Every HTTP Header should use `Hyphenated-Pascal-Case`. A custom HTTP Header **SHOULD NOT** start with `X-` \([RFC6648](https://tools.ietf.org/html/rfc6648)\).

#### Example

```text
Order-Metadata-Header: 42
```

## API Description

Naming conventions within API Description document.

### API Name

Every API Description API name **MUST** start with API domain enclosed in square brackets \(e.g. `[API Domain] My API`\). Words **MUST** be separated by space.

#### Example

```yaml
swagger: '2.0'
info:
  version: '1.0.0'
  title: '[Demo] Orders API'
```

### Resource Name

Every resource **MUST** have a name \(defined by `x-summary` field\). Resource name **MUST** be in `Title Case`. Words **MUST** be separated by a space.

#### Example

```yaml
/orders:
  x-summary: List of Orders
```

### Action Name

Every action \(operation\) **MUST** have a name \(defined by `summary` field\). Action name **MUST** be in `Title Case`. Words **MUST** be separated by a space.

#### Example

```yaml
get:
  summary: Retrieve List of Orders
```

