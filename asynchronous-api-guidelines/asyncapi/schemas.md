# Schemas

### AVRO

Every event **MUST** be describe as AVRO schema. The schema has to be attached to the data in the AsyncAPI document

Example of object with `externalDocs` added with the AVRO schema

```yaml
  schemas:
    lightMeasuredPayload: 
      externalDocs:
        description: "Keyobject"
        url: https://registry.confluent.cloud/subjects/LightMeasuredPayload-key/versions/1.0.1     
      externalDocs:
        description: "Value object"
        url: https://registry.confluent.cloud/subjects/LightMeasuredPayload-value/versions/1.0.1
```

**MUST** [use schema naming convention](naming-conventions.md#subject-naming-strategies)

### Automatic Schema Registration

The producer **MUST** disable automatic schema registration

