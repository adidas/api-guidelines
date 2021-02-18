# Callback

Callback or Webhooks are another way of handling long running tasks (LRTs). Callbacks are based on the subscription principle, whereas the API notifies the API Consumer in a different connection. This pattern is also applicable to the subscription to any kind of events to get notifications from your API.

The roles are:

- API Consumer / Subscriber
- API Producer / Publisher

If the chosen way is based on using callbacks, the response to such an asynchronous operation **MUST** return, in the case of success, the **202 Accepted** status code together with an `application/hal+json` representation of a new **task-tracking resource**.

> This pattern is described by [OAS v3.0.x](https://swagger.io/docs/specification/callbacks/).


## Subscription

The subscriber enrolls to specfic notifications. The subscriber resource **MUST** provide the information about the callback URL. Any data needed to require the execution of a task **MUST** be included in the request body.

The subscription is created by using the HTTP POST Request Method. It **SHOULD** be designed as follows:

1. Subscription is accepted

   Return **201 Created** and representation of the current status. Content type: `application/hal+json`
   The publisher resource **MUST** provide a UUID to identify the subscription.

2. Subscription is not accepted

   Return **403 Forbidden** . Content type: `application/problem+json` with the problem detail information.


## Notification

The publisher resource **MUST** use callback URL provided by the subscriber. Any data with the output of the requested task **SHOULD** be sent to the subscriber in this request.

The callback request has to use the HTTP POST Request Method **SHOULD** as follows:

1. The subscriber accepts the callback. Content type: `application/hal+json`

   Return **200 OK**.

2. The subscriber does not accept the callback

   Return **403 Forbidden** . Content type: `application/problem+json` with the problem detail information.


## Cancel Subscription

The subscriber resource **MUST**  include the UUID to identify the subscription.

It has to be used the HTTP PUT Request Method **SHOULD** as follows:

1. Subscription is accepted

   Return **202 Accepted**. Content type: `application/hal+json`

2. Subscription is not accepted

   Return **403 Forbidden** . Content type: `application/problem+json` with the problem detail information.


## Design Note

- The subscription pattern supports two main approaches:
  - On one side, it can be **only-once**. The callback will be invoked only once by the publisher and it will be cancelled automatically after.
  - On the other side, it can be **continuous**. In this case the subscription **MUST** be explicitly cancelled. Regarding the subscriber, its API is also the subject of the adidas API guidelines.

- The callback can be based on an Asynchronous/Streaming API topic. In this case the subscription is made as mentioned above but with the following differences in the workflow:
  - The API Consumer does not send a callback URL in the initial request.
  - The API Producer **SHOULD** provide the name of the topic and the UID of the task to correlate the input. 
  - It is up to the API Consumer to subscribe to the Asynchronous/Streaming API topic to receive the input from the provider. Please read the Asynchronous/Streaming API section.

### Example

1. **Settle the subscription**
  
    ```
    POST /items/tasks/ HTTP/1.1
    Content-Type: application/json

    {
      "callbackUrl": "https://myserver.com/send/callback/here"
    }

    ...

    HTTP/1.1 201 Created
    Content-Type: application/hal+json

    {
      "_links": {
        "self": { "href": "/items/tasks/4746" }
      },
      "message": "Your request to subscribe to the progress of the task has been accepted.",
      "UUID": "4746"
    }
    ```

2. **The Publisher sends the callback**

    ```
    POST https://myserver.com/send/callback/here HTTP/1.1

    {
      "_links": {
        "self": { "href": "/items/tasks/4746" }
      },
      "UUID": "4746",
      {
        <Data with the callback>
      }
    }

    ...

    HTTP/1.1 200 Ok
    Content-Type: application/hal+json

    ```

3. **Eventually the subscriber cancels the subscription**

    ```
    PUT /feeds/tasks/1 HTTP/1.1
    ...

    HTTP/1.1 202 Accepted
    Content-Type: application/hal+json

    {
      "_links": {
        "self": { "href": "/feeds/tasks/4746" }
      },
      "message": "Your subscription is cancelled."
    }
    ```

