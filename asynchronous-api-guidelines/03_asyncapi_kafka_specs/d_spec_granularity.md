# adidas Asynchronous API guidelines

## AsyncAPI guidelines for Kafka

### Spec granularity

In Fast Data Platform (FDP) all resources are grouped by namespace. 

For that reason specs **SHOULD** be created with a relation 1:1 with namespaces. In other words, every namespace will have an AsyncAPI spec including all the assets belonging to that namespace.

Different granularities **MAY** be chosen depending on the needs. 