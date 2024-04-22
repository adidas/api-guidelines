# adidas Asynchronous API guidelines

## Asynchronous API guidelines

### Contract

Approved API Design, represented by its API Description or schema, **MUST** represent the contract between API stakeholder, implementers, producers and consumers.

That contract **MUST** contain enough information to use the API (servers, URIs, credentials, contact information, etc).

### API First

Asyncrhonous APIs **SHOULD** use the API First principle :

- The API designs **SHOULD** involve all relevant stakeholders (developers, consumers, ...) to ensure that final design fulfil requirements from different perspectives
- The resulting API specification will be the source of truth rather than the API implementation

### Immutability

After agreement with the stakeholders the contract **MUST** be published in order to do it immutable. Changes to the API related to the data model, **MUST** be published in a schema registry. 

Schema registry acts as a central location for storing and accessing the schemas of all published APIs.

### Common data types

The API types **MUST** adhere to the formats defined below:

| Data type | Standard | Example |
| --------- | -------- | ------- |  
| Date and Time | [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) | 2017-06-21T14:07:17Z (Always use UTC) |
| Date | [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) | 2017-06-21 |
| Duration | [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) | P3Y6M4DT12H30M5S |
| Time interval | [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) | 2007-03-01T13:00:00Z/2008-05-11T15:30:00Z |
| Timestamps | [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) | 2017-01-01T12:00:00Z |
| Language Codes | [ISO 639](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) | en <-> English |
| Country Code | [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) | DE <-> Germany |
| Currency | [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) | EUR <-> Euro |

### Schemas and data evolution

All asynchronous APIs **SHOULD** leverage Schema Registry to ensure consistency across consumers/producers with regards to message structure and ensuring compatibility across different versions. 

The default compatibility mode in Schema Registry is FULL_TRANSITIVE. This is the more restrictive compatibility mode, but others are also available.

| Mode | Description |
|------|-------------|
|BACKWARD|new schema versions are backward compatible with older versions|
|BACKWARD_TRANSITIVE|backward compatibility across all schema versions, not just the latest one.|
|FORWARD|new schema versions are compatible with older consumer versions|
|FORWARD_TRANSITIVE|forward compatibility across all schema versions.|
|FULL|both backward and forward compatibility with the latest schema version|
|FULL_TRANSITIVE|both backward and forward compatibility with all schema versions|
|NONE|schema compatibility checks are disabled|

If for any reason you need to use a less strict compatibility mode in a topic, that compatibility mode **SHOULD NOT** be modified on the same topic. Instead, a new topic **SHOULD** be used to avoid unexpected behaviors or broken integrations.

Applications **MUST NOT** enable automatic registration of schemas because FDP's operational model for the Schema Registry relies on GitOps (every operation is done through GIT PRs + automated pipelines)

 Please refer to  [Kafka_Schema_Registry-Default_Requirements](https://confluence.tools.3stripes.net/display/FDP/Kafka_Schema_Registry-Default_Requirements) for more information about Schema Registry.

 ### Key/Value message format

 Kafka messages **MAY** include a key, which needs to be properly designed to have a good partition balanceare key-value pairs.

The message key and the payload (often called value) can be serialized independently and can have different formats. For example, the payload of the message can be sent in AVRO format, while the message key can be a primitive type (string). 

Message keys **SHOULD** be kept as simple as possible and use a primitive type when possible.

### Naming conventions

As general naming conventions, asynchronous APIs **MUST** adhere to the following conventions

- Use of english
- Avoid acronyms or explain them when used
- Use camelCase unless stated otherwise

### Protocols

Protocols define how clients and servers communicate in an asynchronous architecture.

The accepted protocols for asynchronous APIs are:

- Kafka
- HTTPs
- WebSockets
- MQTT

This version of the guidelines focuses on Kafka protocol, but it could be extended in the future. In any case, this document will be updated to reflect the state of the art.

### Security

The [security guidelines](https://github.com/adidas/api-guidelines/blob/feature/asyncapi-guidelines/general-guidelines/security.md) for regular APIs **MUST** be followed strictly when applicable.

