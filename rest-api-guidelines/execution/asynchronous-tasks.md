# Asynchronous Tasks

If an API operation is asynchronous, but a client could track its progress, the response to such an asynchronous operation **MUST** return, in the case of success, the **202 Accepted** status code together with an `application/hal+json` representation of a new **task-tracking resource**.

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

The asynchronous operation task-tracking resource can be either **polled** by client or the client might initially provide a **callback** to be executed when the operation finishes.

In the case of callback, the API and its client MUST agree on what HTTP method and request format is used for the callback invitation. If built within adidas, the "client" API is also the subject of the adidas API guidelines.

### Example

1. **Initiate the asynchronous task**
  
    ```
    POST /feeds/tasks/ HTTP/1.1
    Content-Type: application/json
    ...

    HTTP/1.1 202 Accepted
    Content-Type: application/hal+json

    {
      "_links": {
        "self": { "href": "/feeds/tasks/1" }
      },
      "message": "Your task to generate feed has been accepted. Try query for result after 60 seconds.",
      "pingAfter": 60
    }
    ```

1. **Poll the task status: In progress**

    ```
    GET /feeds/tasks/1 HTTP/1.1
    ...

    HTTP/1.1 200 Ok
    Content-Type: application/hal+json

    {
      "_links": {
        "self": { "href": "/feeds/tasks/1" }
      },
      "message": "Your feed is being generated. Try query for result after 30 seconds.",
      "pingAfter": 30
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

