# adidas Asynchronous API guidelines

## AsyncAPI guidelines for Kafka

### AsyncAPI version

Any version of AsyncAPI **MAY** be used for spec definitions. 

However, to be aligned with adidas tooling, spec versions **SHOULD** be *v2.6.0*, because to the date of this document creation (April 2024) this is the highest supported version on Swaggerhub, the current API portal to render, discover and publish specs.

```yaml
asyncapi: 2.6.0
...
```

### Internal vs public specs

AsyncAPI specs **MAY** be created both for public APIs or for internal APIs. 

- Public APIs are those who are created to be consumed by others
- Internal APIs are only for development teams for a particular project

There are no differences with regards to the spec definition, but internal APIs **SHOULD** have restricted access limited only to the internal development team for a particular project or product. 

This access control is handled through Role-Based Access Control (RBAC) implemented in Swaggerhub.

### Spec granularity

In Fast Data Platform (FDP) all resources are grouped by namespace. 

For that reason specs **SHOULD** be created with a relation 1:1 with namespaces. In other words, every namespace will have an AsyncAPI spec including all the assets belonging to that namespace.

Different granularities **MAY** be chosen depending on the needs. 

### Meaningful descriptions

All fields included in the specs **MUST** include a proper description. 

### Self-contained specs

All AsyncAPI specs **SHOULD** include as much information as needed in order to make the spec self-contained and clearly documented

### Contact information

AsyncAPI specs **MUST** include at least one main contact under the info.contact section. 

The spec only allows to include one contact there, but it **MAY** also include additional contacts using extension fields. In case this is done, it **MUST** use the extension field *x-additional-responsibles*.

For example:

```yaml
...
info:
  ...
  contact:
    name: "Main point of contact"
    email: "team_dl@adidas.com"
  x-additional-responsibles:
    - person2@adidas.com
    - person3@adidas.com
    - person4@adidas.com
```

### AsyncAPI ID

According to [AsyncAPI documentation](https://v2.asyncapi.com/docs/reference/specification/v2.6.0#A2SIdString), every AsyncAPI spec **SHOULD** use a unique identifier for the application being defined, following RFC-3986.

More concretely, ASyncAPI specs created in adidas should use the following pattern

```yaml
...
id: urn:fdp:adidas:com:namespace:asyncapi_reference_spec
...
```


### Servers

All AsyncAPI specs **MUST** include a servers section including references to the right Kafka clusters, defined and maintained by FDP team and made available through domains in Swaggerhub.

Those definitions are handled in Swaggerhub as reusable domains publicly available: 

https://design.api.3stripes.io/domains/adidas/asyncapi_adoption_commons/1.0.0

that can be referred from any spec, picking the right kafka servers as required (see example below).

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
**Important note** Don't forget to include '*/v1/*' in the URL of the domain

### Channels

All AsyncAPI specs **MUST** include definitions for the channels (kafka topics) including: 

- Description of the topic
- Servers in which the topic is available
    - This is a reference to one of the server identifiers included in the servers section
- publish/subscribe operations
    - Operation ID
    - Summary or short description for the operation
    - Description for the operation
    - Security schemes
    - Tags
    - External Docs
    - Message details

In addition to those supported fields, it **MAY** be possible to use extension attributes (using the x- prefix) to specify specific configuration parameters and metadata. In so, the recommended attributes to use are :

- x-metadata
    - To include additional configuration specific to your team or project
- x-configurations
    - To include Kafka configuration parameters and producers/consumers

As the parameters can be different per environment, it is very convenient to add an additional level for the environment

As part of the publish/subscribe operations, the spec **SHOULD** specify the different kafka clients currently consuming from the different topics for each cluster/environment. For this, the extended attributes x-producers and x-consumers will be used.

```yaml
...
channels:
  namespace.source.event.topic-name:
    description: A description of the purpose of the topic and the contained information
    servers: ["pivotalDev", "pivotalSit", "pivotalPro"]
    x-metadata:
      myField1: myValue1
      myField2: myValue2
    x-configurations:
      pivotal.dev:
        kafka:
          partitions: 12
          replicas: 1
          topicConfiguration:
            min.insync.replicas: "1"
            retention.ms: "2592000000"
      pivotal.sit:
        kafka:
          partitions: 12
          replicas: 2
          topicConfiguration:
            min.insync.replicas: "1"
            retention.ms: "2592000000"
     publish:
      operationId: "producer"
      summary: "Description for the operation"
      description: "An extensive explanation about the operation"
      security:
        - producerAcl: []
      tags:
        - name: tagA
        - name: tagB
      x-producers:
        pivotal.dev:
          - producer1
          - producer2
        pivotal.sit:
          - producer1
          - producer2
        pivotal.pro:
          - producer3
          - producer4
      externalDocs:
        description: documentation
        url: http://confluence.adidas.fdp/catalogue/myTopic
	  ...
    subscribe:
      operationId: "consumer"
	  ...
      x-consumers:
        pivotal.dev:
          - consumer1
          - consumer2
        pivotal.sit:
          - consumer1
          - consumer2
        pivotal.pro:
          - consumer3
...
```


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

### Security Schemes

Specs **MAY** use security schemas to reflect the fact that the kafka servers use mTLS. It is something quite static at the moment so the recommendation is reuse the ones specified in the reference spec.

```yaml
channels:
  namespace.source.event.topic-name:
    ...
    publish:
      ...
      security:
        - producerAcl: []
      ...
components:
  securitySchemes:
    ...
    consumerAcl:
      type: X509
    producerAcl:
      type: X509
```

### External docs

The external docs **SHOULD** be used to refer to LeanIX factsheet associated to the spec.

```yaml
...
externalDocs:
  description: LeanIX
  url: https://adidas.leanix.net/adidasProduction/factsheet/Application/467ff391-876c-49ad-93bf-facafffc0178
```