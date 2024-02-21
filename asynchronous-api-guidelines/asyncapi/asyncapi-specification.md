# AsyncAPI Specification

## AsyncAPI specification

A async api **MUST** use the [AsyncAPI specification](https://v2.asyncapi.com/docs/reference/specification/v2.6.0)

### API Design Platform

1. [SwaggerHub](https://design.api.3stripes.io/) is the primary platform supporting API first approach. SwaggerHub **MUST** be used during API Design.
2. Every API description **MUST** be stored in [SwaggerHub](https://design.api.3stripes.io/) under the adidas team.
3. SwaggerHub **MUST** be the **single source of truth** to learn about existing APIs within the organization.

> NOTE: SwaggerHub supports API-first approach in multiple ways:\
> For example, it validates API description for correctness and automatically generates API documentation to drive the discussion between stakeholders. (No more emails with API description flying between stakeholders)

### Immutable version <a href="#inmutable" id="inmutable"></a>

After agreement with the stakeholders the contract **MUST** be published in order to do it immutable. Changes in the data **MUST** be published in schema registry.
