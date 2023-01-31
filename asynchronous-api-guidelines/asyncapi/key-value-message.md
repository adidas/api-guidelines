# Key/Value message

Kafka messages are key-value pairs. Message keys and message values can be serialized independently. For example, the value may be using an Avro `record`, while the key may be a primitive (`string`, `integer`, and so forth). Typically message keys, if used, are primitives. How you set the key is up to you and the requirements of your implementation.

**SHOULD** keep key value schema complexity to a minimum. Use either a simple, non-serialized data type such as a string UUID or long ID.&#x20;
