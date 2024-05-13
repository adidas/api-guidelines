# Channels

All AsyncAPI specs **MUST** include definitions for the channels (Kafka topics) including:

* Description of the topic
* Servers in which the topic is available
  * This is a reference to one of the server identifiers included in the servers section
* publish/subscribe operations
  * Operation ID
  * Summary or short description for the operation
  * Description for the operation
  * Security schemes
  * Tags
  * External Docs
  * Message details

In addition to those supported fields, it **MAY** be possible to use extension attributes (using the x- prefix) to specify specific configuration parameters and metadata. In so, the recommended attributes to use are :

* x-metadata
  * To include additional configuration specific to your team or project
* x-configurations
  * To include Kafka configuration parameters and producers/consumers

As the parameters can be different per environment, it is very convenient to add an additional level for the environment

As part of the publish/subscribe operations, the spec **SHOULD** specify the different Kafka clients currently consuming from the different topics for each cluster/environment. For this, the extended attributes x-producers and x-consumers will be used.

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
