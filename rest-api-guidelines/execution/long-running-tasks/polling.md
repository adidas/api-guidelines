# Polling

If an API operation can be considered as a long running task (LRT) and the API Consumer can track its progress, the response to the LRT **MUST** return, in the case of success, the **202 Accepted** status code together with an `application/hal+json` representation of a new **task-tracking resource**.

## Task Tracking Resource

The task-tracking resource **SHOULD** convey the information about the status of an asynchronous task.

Retrieval of such a resource using the HTTP GET Request Method **SHOULD** be designed as follows:

1. Task is Still Processing

   Return **200 OK** and representation of the current status.

2. Task Successfully Completed

   Return **303 See Other** together with [HTTP Location Header](https://tools.ietf.org/html/rfc7231#section-7.1.2) with URI or a outcome resource.

3. Task Failed

   Return **200 OK** and `application/problem+json` with the problem detail information on the task has failed.

## Design Note

The polling (task-tracking) operation requires a clear adaptation on the API Consumer side:

- Polling requests frequency depend on the type of operation and specific latency of thre resource.
- The identification of the resource has to be correlated along the series of polling requests. The API Consumer has to be able to save this ID and the API Producer has to be able to identify the progress of the operation with that ID. 
- A security problem can be raised if a non-authorized client retrieves the response for a different resource ID. The authorization data and tasks in progress have to be strongly correlated and controlled to avoid consistency issues.


### Example

1. **Initiate the polling task**
  
    ```
    POST /feeds/tasks/ HTTP/1.1
    Content-Type: application/json
    ...

    HTTP/1.1 202 Accepted
    Content-Type: application/hal+json
    Retry-After: 60

    {
      "_links": {
        "self": { "href": "/feeds/tasks/1" }
      },
      "message": "Your task to generate feed has been accepted. Try query for result after 60 seconds.",
      "retryAfter": 60
    }
    ```

1. **Poll the task status: In progress**

    ```
    GET /feeds/tasks/1 HTTP/1.1
    ...

    HTTP/1.1 200 Ok
    Content-Type: application/hal+json
    Retry-After: 30

    {
      "_links": {
        "self": { "href": "/feeds/tasks/1" }
      },
      "message": "Your feed is being generated. Try query for result after 30 seconds.",
      "retryAfter": 30
    }
    ```

1. **Poll the task status: Finished**

    ```
    GET /feeds/tasks/1 HTTP/1.1
    ...

    HTTP/1.1 303 See Other
    Location: /feeds/1
    Content-Location: /feeds/tasks/1
    Content-Type: application/hal+json

    {
      "_links": {
        "self": { "href": "/feeds/tasks/1" },
        "feed": { "href": "/feeds/1" }
      },
      "message": "Your feed is ready."
    }
    ```

1. **Poll the task status: Failure**

    ```
    GET /feeds/tasks/1 HTTP/1.1
    ...

    HTTP/1.1 200 OK
    Content-Type: application/problem+json

    {
      "title": "Wrong input parameters",
      "detail: "Missing required input parameter XYZ.",
      "status": 400
    }
    ```

