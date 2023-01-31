# Introduction

## adidas Asynchronous APIs Guidelines



# Summary

## adidas Asynchronous APIs Guidelines

General Guidelines

**MUST** [follow API First principle](asyncapi/api-first.md)\
**MUST** [use AsyncAPI specification](asyncapi/asyncapi-specification.md)\
**MUST** p[rovide API user help](asyncapi/user-information.md)\
**SHOULD** [follow Event-Driven Architecture (EDA)](asyncapi/event-driven-architecture-eda.md)\
**MUST** [publish immutable versions](asyncapi/asyncapi-specification.md#inmutable)\
**MUST** [use American English](asyncapi.md)

Protocol\
\
**MAY** [use HTTP protocol](asyncapi/protocols.md#http)\
**SHOULD** [Kafka protocol](asyncapi/protocols.md#kafka)\
**SHOULD** [use key-value message approach](asyncapi/key-value-message.md)

Security\
\
**MUST** [use authentication](asyncapi/security.md#authentication)\
**MUST** [use encrypted protocols](asyncapi/security.md#encrypted-comunication)

Basic Data format\
\
**MUST** [follow Common Data Types](asyncapi/common-data-types.md)\
**MUST**[ have a schema definition (AVRO)](asyncapi/schemas.md#avro)\
**MUST** [disable Automatic Schema Registration](asyncapi/schemas.md#automatic-schema-registration)\
**MUST** [follow naming convection](asyncapi/naming-conventions.md#naming-conventions)\
**SHOULD** [be full transitive](asyncapi/compatibility.md)\
**MAY** [use backward/forward compatibility](asyncapi/compatibility.md)\
**SHOULD** [use new topic when not full compatibly](asyncapi/compatibility.md)\
**MUST** [use schema naming convention](asyncapi/naming-conventions.md#subject-naming-strategies)
