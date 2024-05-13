# Key/Value Format

Kafka messages **MAY** include a key, which needs to be properly designed to have a good balance of data across partitions.

The message key and the payload (often called value) can be serialized independently and can have different formats. For example, the value of the message can be sent in AVRO format, while the message key can be a primitive type (string).&#x20;

Message keys **SHOULD** be kept as simple as possible and use a primitive type when possible.
