# Schemas

Kafka messages **SHOULD** use schemas (AVRO, JSON, Protobuf) registered in the Schema Registry to ensure compatibility between producers/consumers.

If so, always refer to the schema definitions directly in the schema registry instead of duplicating the schema definitions inline. This is to avoid double maintenance.&#x20;

An example directly taken from reference spec is shown below

```yaml
...
channels:
  namespace.source.event.topic-name:
    ...
    publish:
      ...
      message:
        $ref: '#/components/messages/namespace.source.event.topic-name'

components:
  ...
  messages:
    namespace.source.event.topic-name:
      $ref: '#/components/schemas/namespace.source.event.topic-name'
  ...
  schemas:
    namespace.source.event.topic-name:
      description: 'Schema[s] retrieved from Schema Registry'
      schemaFormat: 'application/vnd.apache.avro;version=1.9.0'
      payload:
        $ref: 'https://dev-fdp-playground-schema-registry.api.3stripes.io/subjects/namespace.source.event.topic-name-value/versions/latest/schema'
      bindings:
        kafka:
          key:
            $ref: 'https://dev-fdp-playground-schema-registry.api.3stripes.io/subjects/namespace.source.event.topic-name-key/versions/latest/schema'
```

**Important note** The used schema is a very simple one, it is only used to illustrate how to refer to it. In case the message doesn't use schema for the key, _bindings_ field can be omitted from the schema.
