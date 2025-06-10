# Servers

All AsyncAPI specs **MUST** include a _servers_ section including references to the right Kafka clusters, defined and maintained globally.

For example, in Swaggerhub it is possible to refer to those reusable definitions through:

[https://design.api.3stripes.io/domains/adidas/cluster-landscape/1.0.0](https://design.api.3stripes.io/domains/adidas/cluster-landscape/1.0.0)

more specifically, it is possible to add the right Kafka servers like this:

```yaml
...
servers:
  playground-dev:
    $ref: 'https://design.api.3stripes.io/v1/domains/adidas/cluster-landscape/1.0.0#/components/servers/playground-dev'
  playground-sit:
    $ref: 'https://design.api.3stripes.io/v1/domains/adidas/cluster-landscape/1.0.0#/components/servers/playground-sit'
  playground-pro:
    $ref: 'https://design.api.3stripes.io/v1/domains/adidas/cluster-landscape/1.0.0#/components/servers/playground-pro'
...
```

**Important note** Don't forget to include '_/v1/_' in the URL of the domain.
