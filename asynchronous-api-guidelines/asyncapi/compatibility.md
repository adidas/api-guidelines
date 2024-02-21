# Compatibility

The Schema Registry server enforce compatibility rules when new schemas are registered in a subject. These are the compatibility types:

* `BACKWARD`: consumers using the new schema can read data written by producers using the latest registered schema.This means that new schema versions are backward compatible with older versions.
* `BACKWARD_TRANSITIVE`: consumers using the new schema can read data written by producers using all previously registered schemas. This ensures backward compatibility across all schema versions, not just the latest one.
* `FORWARD`: consumers using the latest registered schema can read data written by producers using the new schema. This means that new schema versions are compatible with older consumer versions.
* `FORWARD_TRANSITIVE`: consumers using all previously registered schemas can read data written by producers using the new schema. Similar to BACKWARD_TRANSITIVE, this ensures forward compatibility across all schema versions.
* `FULL`: the new schema is forward and backward compatible with the latest registered schema. This ensures both backward and forward compatibility with the latest schema version.
* `FULL_TRANSITIVE`: the new schema is forward and backward compatible with all previously registered schemas. 
* `NONE`: schema compatibility checks are disabled. This means there are no enforced compatibility rules, which can lead to potential issues with data compatibility between producers and consumers.

**SHOULD** use`FULL_TRANSITIVE`, it is the default option when a new schema is registered.

Others compatibility mode **MAY** be used but you **SHOULD** use a different topic when not FULL is ensure.