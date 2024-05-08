# adidas Asynchronous API guidelines

## AsyncAPI guidelines for Kafka

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