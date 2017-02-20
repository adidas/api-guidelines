# Naming Conventions

## General Naming Rules

* Use lowercase
* Don't use acronyms
* Avoid trailing slashes
* Use underscore to delimit words

Every identifier **MUST** be in `lowercase` except for abbreviations. Abbreviations **MAY** be in `UPPERCASE`. An identifier **SHOULD NOT** contain acronyms. Underscore (`_`) **MUST** be used to delimit combined words.

## URI
Every URI **MUST** follow the General Rules. In addition, an URI **MUST NOT** end with a trailing slash (`/`).

### Query Parameters and Path Fragments
Every URI query parameter or fragment **MUST** follow the General Rules. In addition, they **MUST NOT** clash with the [reserved query parameter names](https://tools.adidas-group.com/confluence/display/EA/API+Interaction#APIInteraction-Query_Parameters).

### URI Template Variables
In addition to General Naming Rules, URI Template Variable names **MUST** follow the [RFC6570](https://tools.ietf.org/html/rfc6570#section-2.3). That is, the variable names can consist only from `ALPHA / DIGIT / "_" / pct-encoded`.

> NOTE: Per RFC6570 Hyphen (`-`) is NOT legal URI Template variable name character.

### Query Parameters

## Representation Format Fields

## Relation Type Identifier

## HTTP Headers



