# Backward Compatibility

There are two variants here:

* BACKWARD - Consumers using a new version (X) of a schema can read data produced by the previous version (X - 1)
* BACKWARD\_TRANSITIVE - Consumers using a new version (X) of a schema can read data produced by any previous version (X - 1, X - 2, ....)

The operations that preserve backward compatibility are:

* Deleting fields
  * Consumers with the newer version will just ignore the non-existing fields
* Adding optional fields (with default values)
  * Consumers will set the default value for the missing fields in their schema version

<figure><img src="../../../.gitbook/assets/spaces_PQHX3w20BF4lnkckLJzC_uploads_git-blob-17547da367c50d28e6996ea1d3fab4d10625765b_sr_backward_compatibility.png" alt=""><figcaption></figcaption></figure>
