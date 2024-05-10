# Servers

All AsyncAPI specs **MUST** include a servers section including references to the right Kafka clusters, defined and maintained globally and made available through domains in Swaggerhub.

Those definitions are handled in Swaggerhub as reusable domains publicly available:

[https://design.api.3stripes.io/domains/adidas/asyncapi\_adoption\_commons/1.0.0](https://design.api.3stripes.io/domains/adidas/asyncapi\_adoption\_commons/1.0.0)

that can be referred from any spec, picking the right Kafka servers as required (see example below).

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
