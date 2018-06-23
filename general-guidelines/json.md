# JSON Format Conventions
Any JSON-based message **MUST** conform to the following rules:

1. All JSON field names **MUST** follow the [Naming Conventions](https://adidas-group.gitbooks.io/api-guidelines/content/evolution/naming-conventions.html) (`camelCase`, American English, etc.)
1. Field names **MUST** be ASCII alpha num characters, underscore (`_`) or dollar sign (`$`)
1. Boolean fields **MUST NOT** be of `null` value
1. Fields with `null` value **SHOULD** be omitted
1. Empty arrays and objects **SHOULD NOT ** be `null` (use `[]` or `{}` instead)
1. Array field names **SHOULD** be plural (e.g. `"orders": []`)
