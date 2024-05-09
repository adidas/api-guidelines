# adidas Asynchronous API guidelines

## AsyncAPI guidelines for Kafka

### AsyncAPI version

Any version of AsyncAPI **MAY** be used for spec definitions. 

However, to be aligned with adidas tooling, spec versions **SHOULD** be *v2.6.0*, because to the date of this document creation (April 2024) this is the highest supported version on Swaggerhub, the current API portal to render, discover and publish specs.

```yaml
asyncapi: 2.6.0
...
```