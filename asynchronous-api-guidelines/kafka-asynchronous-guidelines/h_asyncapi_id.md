# AsyncAPI ID

According to [AsyncAPI documentation](https://v2.asyncapi.com/docs/reference/specification/v2.6.0#A2SIdString), every AsyncAPI spec **SHOULD** use a unique identifier for the application being defined, following RFC-3986.

More concretely, ASyncAPI specs created in adidas should use the following pattern

```yaml
...
id: urn:fdp:adidas:com:namespace:asyncapi_reference_spec
...
```
