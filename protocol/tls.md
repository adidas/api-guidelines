# Transport Layer Security (TLS)
Every API MUST require secure connections with TLS. That is, an API using the HTTP protocol MUST use **HTTPS**.

Any non-TLS requests SHOULD be ignored. In HTTP environments where this is not possible, a non-TLS request SHOULD result in the **403 Forbidden** response.