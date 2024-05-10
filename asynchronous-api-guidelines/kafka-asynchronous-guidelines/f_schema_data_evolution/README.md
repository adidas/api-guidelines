# Schema Data Evolution

All asynchronous APIs **SHOULD** leverage Schema Registry to ensure consistency across consumers/producers with regards to message structure and ensuring compatibility across different versions.

The default compatibility mode **SHOULD** be FULL\_TRANSITIVE, which is the default compatibility mode in adidas for Schema Registry. Check the sections below to know more about compatibility modes.

#### Compatibility modes

Once a given schema is defined, it is unavoidable that the schema evolves with time. Every time this happens, downstream consumers need to be able to handle data with both old and new schemas seamlessly.

Each new schema version is validated according to the configuration before being created as a new version. Namely, it is checked against the configured compatibility types.

**Important** The mere fact of enabling Schema Registry is not enough to ensure that there are no compatibility issues in a given integration. The right compatibility mode needs also to be selected and enforced.

As a summary, the available compatibility types are listed below:

| Mode                 | Description                                                                 |
| -------------------- | --------------------------------------------------------------------------- |
| BACKWARD             | new schema versions are backward compatible with older versions             |
| BACKWARD\_TRANSITIVE | backward compatibility across all schema versions, not just the latest one. |
| FORWARD              | new schema versions are compatible with older consumer versions             |
| FORWARD\_TRANSITIVE  | forward compatibility across all schema versions.                           |
| FULL                 | both backward and forward compatibility with the latest schema version      |
| FULL\_TRANSITIVE     | both backward and forward compatibility with all schema versions            |
| NONE                 | schema compatibility checks are disabled                                    |



#### Upgrading process of clients based on compatibility

Depending on the compatibility mode, the process of upgrading producers/consumers will be different based on the compatibility mode enabled.

* NONE
  * As there are no compatibility checks, no order will grant a smooth transition
  * In most of the cases this lead to having to create a new topic for this evolution
* BACKWARD / BACKWARD\_TRANSITIVE
  * Consumers **MUST** be upgraded first before producing new data
  * No forward compatibility, meaning that there's no guarantee that the consumers with older schemas are going to be able to read data produced with a new version
* FORWARD / FORWARD\_TRANSITIVE
  * Producers **MUST** be upgraded first and then after ensuring that no older data is present, upgrade the consumers
  * No backward compatibility, meaning that there's no guarantee that the consumers with newer schemas are going to be able to read data produced with an older version
* FULL / FULL TRANSITIVE
  * No restrictions on the order, anything will work

#### How to deal with breaking changes

If for any reason you need to use a less strict compatibility mode in a topic, or you can't avoid breaking changes in a given situation, the compatibility mode **SHOULD NOT** be modified on the same topic.

Instead, a new topic **SHOULD** be used to avoid unexpected behaviors or broken integrations. This allows a smooth transitioning from clients to the definitive topic, and once all clients are migrated the original one can be decommissioned.

Alternatively, instead of modifying existing fields it **MAY** be considered as an sub-optimal approach to add the changes in new fields and have both coexisting. Take into account that this pollutes your topic and it can cause some confusion.
