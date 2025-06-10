# Why AsyncAPI?

Event-driven architectures are becoming increasingly popular for building scalable, responsive, and efficient applications. AsyncAPI plays a crucial role in this landscape by offering a standardized way to describe asynchronous APIs, similar to how OpenAPI does for REST APIs. AsyncAPI seeks to make the development, maintenance, and testing of asynchronous APIs easier by providing a machine-readable specification.

It supports various messaging protocols, including MQTT, Web Socket, Kafka, AMQP, and more, making it versatile for different use cases. In adidas, AsyncAPI is used mainly to document Kafka resources created across the company in the scope of the Streaming Platform, but nothing prevents you from using it for a different purpose.

The benefits of using AsyncAPI are, amongst others:

* Standardization
  * AsyncAPI defines a STANDARD format (YAML or JSON) for describing asynchronous APIs
  * By defining the structure of messages, channels, and events, you can ensure that all components adhere to the same conventions
  * Using a single standard ensures consistency in the design and documentation of all your asynchronous APIs
  * This simplifies integration, maintenance, and troubleshooting across different parts of your system
* Improved Developer Experience
  * AsyncAPI documents the messages being exchanged, their structure, and the events triggered by them
  * It provides developers with a clear picture of how to interact with the API, what data to expect, and how to interpret responses without digging into the implementation details
* Code scaffolding
  * Using tools like asyncapi-generator allow to easily generate the skeleton of applications that can work with the resources described in the spec
  * This can be done in different programming languages (Python, Java, Node.js. ...), reducing significantly the development time and the coding errors
* Design-first approach: It encourages designing the API first before writing code, leading to better planned and more reliable APIs

In addition to those benefits, Platform & Engineering is working hard to create a data catalogue built upon AsyncAPI that allows to have a good level of discoverability, allowing teams to be able to find exactly the data they need with regards to any data object in the company.

Questions like:

* Who is responsible for a specific data object?
* Where is that data hosted?
* Which kind of information is available?

Will be easy to answer once this catalogue is in place. Also, it is important to have a good discoverability and search & filtering capabilities.
