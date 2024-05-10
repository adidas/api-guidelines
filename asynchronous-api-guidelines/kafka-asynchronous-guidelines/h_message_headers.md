# Message Headers

In addition to the key and value, a Kafka message **MAY** include _**headers**_, which allow to extend the information sent with some metadata as needed (for example, source of the data, routing or tracing information or any relevant information that could be useful without having to parse the message).

Headers are just an ordered collection of key/value pairs, being the key a String and the value a serialized Object, the same as the message value itself.
