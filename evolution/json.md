# JSON Format Conventions
Any JSON-based message **MUST** conform to these rules


- All JSON field names **MUST** follow the [Naming Conventions](https://adidas-group.gitbooks.io/api-guidelines/content/evolution/naming-conventions.html) (`snake_case`, American English etc.)
- Field names **MUST** be ASCII alpha num characters, underscore (`_`) or dollar sign (`$`)
- Boolean fields **MUST NOT** be of `null` value
- Fields with `null` value **SHOULD** be omitted
- Empty arrays and objects **SHOULD NOT ** be `null` (use `[]` or `{}` instead)
- Array field names **SHOULD** be plural (e.g. `"orders": []`)

