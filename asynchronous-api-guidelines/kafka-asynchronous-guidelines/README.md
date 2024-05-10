# Kafka Asynchronous Guidelines

There are several technologies to implement event-driven architectures, but this section is going to focus on the predominant technology on this subject : Apache Kafka.

**Apache Kafka** can be considered as a Streaming Platform which relies on the several concepts:

* Super high-performance, scalable, highly-available cluster of brokers
  * Availability
    * Replication of partitions across different brokers
  * Scalability
    * Partitions
    * Ability to re-balance partitions across consumers automatically when adding/removing them
  * Performance
    * Partitioned, re-playable log (collection of messages appended sequentially to a file)
    * Data copied directly from disk buffer to network buffer (zero copy) without even being imported to the JVM
    * Extreme throughput by using the concept of consumer group
  * Security
    * Secure encrypted connections using TLS client certificates
    * Multi-tenant management through quotas/ACLs
  * Client APIs on different programming languages : Go, Scala, Python, REST, JAVA, ...
  * Stream processing APIs like Kafka Streams
  * Ecosystem of connectors to pull/push data from/to Kafka
  * Clean-up processes for storage optimization
    * Retention periods
    * Compacted topics
