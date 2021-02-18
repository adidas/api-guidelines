# JSON

Any JSON-based message **MUST** conform to the following rules:

1. All JSON field names **MUST** follow the [Naming Conventions ](../rest-api-guidelines/evolution/naming-conventions.md)\(`camelCase`, American English, etc.\)
2. Field names **MUST** be ASCII alpha num characters, underscore \(`_`\) or dollar sign \(`$`\)
3. Boolean fields **MUST NOT** be of `null` value
4. Fields with `null` value **SHOULD** be omitted
5. Empty arrays and objects **SHOULD NOT**  be `null` \(use `[]` or `{}` instead\)
6. Array field names **SHOULD** be plural \(e.g. `"orders": []`\)

