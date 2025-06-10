# Security Schemes

Specs **MAY** use security schemas to reflect the fact that the Kafka servers use mTLS or SASL. It is something quite static at the moment so the recommendation is refer to reusable definitions

Below example includes references to other security schemas used by the Kafka servers

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
      $ref: 'https://design.api.3stripes.io/v1/domains/adidas/cluster-landscape/1.0.0#/components/securitySchemes/consumerAcl'
    producerAcl:
      $ref: 'https://design.api.3stripes.io/v1/domains/adidas/cluster-landscape/1.0.0#/components/securitySchemes/producerAcl'
    mtlsV1Server:
      $ref: 'https://design.api.3stripes.io/v1/domains/adidas/cluster-landscape/1.0.0#/components/securitySchemes/mtlsV1Server'
    mtlsV2Server:
      $ref: 'https://design.api.3stripes.io/v1/domains/adidas/cluster-landscape/1.0.0#/components/securitySchemes/mtlsV2Server'
    saslV1Server:
      $ref: 'https://design.api.3stripes.io/v1/domains/adidas/cluster-landscape/1.0.0#/components/securitySchemes/saslV1Server'
    saslV2Server:
      $ref: 'https://design.api.3stripes.io/v1/domains/adidas/cluster-landscape/1.0.0#/components/securitySchemes/saslV2Server'
```
