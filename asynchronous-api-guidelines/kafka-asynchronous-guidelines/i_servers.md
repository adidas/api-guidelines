# Servers

All AsyncAPI specs **MUST** include a _servers_ section including references to the right Kafka clusters, defined and maintained globally.

For example, in Swaggerhub it is possible to refer to those reusable definitions through:

[https://design.api.3stripes.io/domains/adidas/asyncapi\_adoption\_commons/1.0.0](https://design.api.3stripes.io/domains/adidas/asyncapi\_adoption\_commons/1.0.0)

more specifically, it is possible to add the right Kafka servers like this:

```yaml
...
servers:
  pivotalDev:
    $ref: https://design.api.3stripes.io/v1/domains/adidas/asyncapi_adoption_commons/1.0.0#/components/servers/pivotalDev
  pivotalSit:
    $ref: https://design.api.3stripes.io/v1/domains/adidas/asyncapi_adoption_commons/1.0.0#/components/servers/pivotalSit
  pivotalPro:
    $ref: https://design.api.3stripes.io/v1/domains/adidas/asyncapi_adoption_commons/1.0.0#/components/servers/pivotalPro
...
```

**Important note** Don't forget to include '_/v1/_' in the URL of the domain
