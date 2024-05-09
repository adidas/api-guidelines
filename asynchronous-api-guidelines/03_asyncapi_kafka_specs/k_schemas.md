# adidas Asynchronous API guidelines

## AsyncAPI guidelines for Kafka

### Schemas

Kafka messages **SHOULD** use schemas (AVRO, Json, Protobuf) registered in the Schema Registry to ensure compatibility between producers/consumers. 

If so, always refer to the schema definitions directly in the schema registry instead of duplicating the schema definitions inline. This is to avoid double maintenance. 

An example directly taken from reference spec is shown below

```yaml
...
channels:
  namespace.source.event.topic-name:
    ...
    publish:
      ...
      message:
         $ref: '#/components/messages/topic1Payload'
components:
  ...
  schemas: 
    ...
    topic1SchemaValue:
        schemaFormat: 'application/vnd.apache.avro;version=1.9.0'
        payload:
          $ref: https://sit-fdp-pivotal-schema-registry.api.3stripes.io/subjects/pea_fd_fdp.sample.test-value/versions/latest/schema 
  messages:
    topic1Payload:
        $ref: '#/components/schemas/topic1SchemaValue'
```

**Important note** The used schema is a very simple one, it is only used to illustrate how to refer to it.