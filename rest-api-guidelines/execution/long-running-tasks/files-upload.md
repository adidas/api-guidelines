# Files Upload

The upload of files using a REST API endpoint is a common practice. It implies certain concerns taht have to be addressed in the design phase of the API.

The API Consumer performs a key role in this case. The MIME type in the Content-Type header of the request is an important factor for a successful operation. An operation that needs to upload binary files **SHOULD** uses a collection resource with the POST HTTP Request Method. When processing an existing resource the request message body **MUST** contain the right MIME type of the resources being processed.


## Main Issues

- Too long time periods in timeout settings, blocking open HTTP connections for too long. It makes the API less reliable and more error-prone as it is more vulnerable to network-related issues. 
- Interrupted connections that can result into corrupted files and false response status to the API Consumer.
- No size limit in server can suppose an unacceptable load to the API operation in terms of resources, security and robustness as well as a huge increase in operational cost.

## Checklist in File Upload Operations

### Use the right MIME Type in the API Consumer Side

It is a common practice to use 
[IANA](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types) distinguishes between two main generic types, **discrete** and **multipart**:

- Discrete types are types which represent a single file or medium, such as a single text, video, or music file.
- Multipart type represents a document that is comprised of multiple component parts, each of which may have its own individual MIME type. It can also encapsulate multiple files being sent together in one single transaction. 

#### Using a Multipart Type

- multipart/form-data
- multipart/byteranges

Frameworks like Spring offfer support for multipart files sending like the [MultipartFile](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/web/multipart/MultipartFile.html) interface.

#### Using a Discrete Type
It is recommended to upload the file alone, with no other content in the request. This approach allows to include the MIME type corresponding to the specific type of file. For instance:

- Graphical file -> image/jpeg, image/gif, image/bmp, etc.
- Data file -> text/csv, 
- Text file -> text/plain
- PDF -> application/pdf
etc.

It is also recommended to compress the file to be uploaded, then using these MIM types (examples):

 - gzip -> application/gzip
 - zip -> application/zip
 - 7z -> application/x-7z-compressed
 - tar -> application/x-tar
 etc.

> You can find a complete reference about the MIME types [here](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Common_types).

### Set Maximum Size Limit in the API Producer Side

The maximum size of the whole file **MUST** be set for the given endpoint/s in the APi upstream/backend service side.

The maximum size value depends on the use case and the expected payload in upload requests.

The settings **MUST** included in the upstream/backend service as a part of the configuration.

Otherwise, the API Gateway (Kong) **COULD** be configured enabling a maximum size of the payload for specific endpoint/s.

Frameworks like Spring includes configuration settings for multipart file uploading. The operation **SHOULD** be constrained as follows:

```
spring.servlet.multipart.enabled=true # enables multipart uploads
spring.servlet.multipart.file-size-threshold=2KB  # the threshold after which files are written to disk.
spring.http.multipart.max-file-size=128KB  # the total file size cannot exceed the amount o.
spring.http.multipart.max-request-size=128KB # the total request size for a multipart/form-data cannot exceed 128KB.
```


### Configure Properly all the Components

Load tests should give you metrics about the average latency of the operations. Use these metrics to calcuate the best value for the timeout settings in the upstream/backend service.

The API Gateway timeout settings have to be considered for the expected timeout values, aligned with the values in the upstream/backend service. Al other components in the infrastructure **MUST** be considered for the calculation of the final metrics.
git commit 
```
|API Consumer/Client Timeout| --->  |External Load Balancer|  ---> |API Gateway Timeout|  --->  |Internal Load Balancer|   ---> |Upstream/Backend Service Tiemout|
```

The approach based on too long timeout values is not acceptable. You **MUST** follow a fast-fail approach with a expected duration of the upload. If this time is exceeded a timeout error **SHOULD** be sent to the API Consumer. The maximum size limit **SHOULD** be consistent with the timeout value.

> Please also consider the client and API Gateway Timeout settings. In this case the lack of retrieval of a response during a too long upload operation can trigger a timeout error.