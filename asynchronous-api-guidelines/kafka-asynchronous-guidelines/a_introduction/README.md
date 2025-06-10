# Introduction

This section is specific to the definition of API specs with [AsyncAPI](https://www.asyncapi.com/) for Kafka protocol.

Also, take into account that across the section there will be multiple references to this [AsyncAPI reference specification](https://design.api.3stripes.io/apis/adidas/asyncapi-adoption-initiative/1.0.0) which is publicly available for reference.

#### Kafka to AsyncAPI concept mapping

| Kafka Concept | AsyncAPI Concept |
| ------------- | ---------------- |
| broker        | server           |
| topic         | channel          |
| consumer      | subscriber       |
| producer      | publisher        |

#### First level items in AsyncAPI structure

| Element    | Meaning                                                                    |
| ---------- | -------------------------------------------------------------------------- |
| asyncapi   | Specifies the AsyncAPI specification version                               |
| info       | Provides metadata about the API such as the version, title and description |
| servers    | Describes servers where the API is available                               |
| channels   | Defines the channels through which messages are received/published         |
| components | Reusable elements to be references across the spec                         |
