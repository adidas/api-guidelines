# Use Appropriate Request Methods
Every API **MUST** use appropriate [HTTP request methods](https://github.com/for-GET/know-your-http-well/blob/master/methods.md) for every operation.

Every API designer, implementer and consumer **MUST** understand the semantic of the HTTP METHOD she is using.

At a minimum everyone **MUST** be familiar with the semantics of ["Common" HTTP Request Methods](https://github.com/for-GET/know-your-http-well/blob/master/methods.md#common): **DELETE**, **GET**, **HEAD**, **PUT**, **POST** and the [**PATCH** HTTP Request Method](https://tools.ietf.org/html/rfc5789#section-2). In addition, everyone **MUST** be aware which methods are **Safe**, **Idempotent** and **Cacheable**.

### Safe Methods
As per HTTP specification, the **GET** and **HEAD** methods should be used only for retrieval of resource representations – and they do not update/delete the resource on the server. Both methods are said to be considered “safe“.
This allows user agents to represent other methods, such as POST, PUT and DELETE, in a special way, so that the user is made aware of the fact that a possibly unsafe action is being requested – and they can update/delete the resource on the server and so should be used carefully.


### Idempotent Methods
The term idempotent is used more comprehensively to describe an operation that will produce the same results if executed once or multiple times. This is a beneficial property in many situations, as it means that a transaction can be repeated or retried as often as necessary without causing unintended effects. With non-idempotent operations, the algorithm may have to keep track of whether the operation was already performed or not.
In HTTP specification, The methods **GET**, **HEAD**, **PUT** and **DELETE** are declared idempotent methods. Other methods OPTIONS and TRACE **SHOULD NOT** have side effects, so both are also inherently idempotent.

### Cacheable Methods
Request methods are considered "cacheable" if it is possible and useful to answer a current client request with a stored response from a prior request. **GET** and **HEAD** are defined to be cacheable.

---

#### Example 1
> GET /user/new
> Description: Creates new user

Using GET for unsafe non-idempotent operations is **not acceptable**.

#### Example 2
> POST /status
> Description: Updates the status of a user approval request (to “Approved” or “Rejected”)

Using the POST method for a status update is **not acceptable** (use PATCH).

#### Example 3
> PUT /user
> Description: Creates a new user

Using the PUT method for creating a new resource is **not acceptable** (use POST).

#### Example 4
> PUT: /user
> Description: Updates some user details

Using the PUT method for a partial update is **not acceptable** (use PATCH).

