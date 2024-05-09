# adidas Asynchronous API guidelines

## AsyncAPI guidelines for Kafka

### Internal vs public specs

AsyncAPI specs **MAY** be created both for public APIs or for internal APIs. 

- Public APIs are those who are created to be consumed by others
- Internal APIs are only for development teams for a particular project

There are no differences with regards to the spec definition, but internal APIs **SHOULD** have restricted access limited only to the internal development team for a particular project or product. 

This access control is handled through Role-Based Access Control (RBAC) implemented in Swaggerhub.