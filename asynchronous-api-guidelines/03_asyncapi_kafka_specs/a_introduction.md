# adidas Asynchronous API guidelines

## Introduction to AsyncAPI spec definitions for Kafka protocol

This section is specific to the definition of API specs with [AsyncAPI](https://www.asyncapi.com/) for Kafka protocol.

Also, take into account that across the section there will be multiple references to this [AsyncAPI reference spec](https://design.api.3stripes.io/apis/adidas/asyncapi-adoption-initiative/1.0.0) which is publicly available for reference. 

### Basic concepts about AsyncAPI

#### Why AsyncAPI?

Event-driven architectures are becoming increasingly popular for building scalable, responsive, and efficient applications. AsyncAPI plays a crucial role in this landscape by offering a standardized way to describe asynchronous APIs, similar to how OpenAPI does for REST APIs. AsyncAPI seeks to make the development, maintenance, and testing of asynchronous APIs easier by providing a machine-readable specification.

It supports various messaging protocols, including MQTT, WebSocket, Kafka, AMQP, and more, making it versatile for different use cases. In adidas, we will use it mainly to document Kafka resources created in FDP but nothing prevents you from using it for a different purpose.

The benefits of using AsyncAPI are, amongst others:

- Standardization
    - AsyncAPI defines a STANDARD format (YAML or JSON) for describing asynchronous APIs. 
    - By defining the structure of messages, channels, and events, you can ensure that all components adhere to the same conventions. 
    - Using a single standard ensures consistency in the design and documentation of all your asynchronous APIs. 
    - This simplifies integration, maintenance, and troubleshooting across different parts of your system.
- Improved Developer Experience
    - AsyncAPI documents the messages being exchanged, their structure, and the events triggered by them. 
    - It provides developers with a clear picture of how to interact with the API, what data to expect, and how to interpret responses without digging into the implementation details. 
- Code scaffolding
    - Using tools like asyncapi-generator allow to easily generate the skeleton of applications that can work with the resources described in the spec. 
    - This can be done in different programming languages (Python, Java, Node.js. ...), reducing significantly the development time and the coding errors.
- Design-first approach: It encourages designing the API first before writing code, leading to better planned and more reliable APIs.

In addition to those benefits, Platform & Engineering is working hard to create a data catalogue built upon AsyncAPI that allows to have a good level of discoverability, allowing teams to be able to find exactly the data they need with regards to any data object in the company.

Questions like:

- Who is responsible for a specific data object
- Where is that data hosted
- Which kind of information is available

Will be easy to answer once this catalogue is in place. Also, it is important to have a good discoverability and search & filtering capabilities.

#### Kafka to AsyncAPI concept mapping

|Kafka Concept|AsyncAPI Concept|
|-------------|----------------|
|broker|server|
|topic|channel|
|consumer|subscriber|
|producer|publisher|

#### First level items in AsyncAPI structure

|Element|Meaning|
|-------|-------|
|asyncapi|Specifies the AsyncAPI specification version|
|info|Provides metadata about the API such as the version, title and description|
|servers|Describes servers where the API is available|
|channels|Defines the channels through which messages are received/published|
|components|Reusable elements to be references across the spec|

