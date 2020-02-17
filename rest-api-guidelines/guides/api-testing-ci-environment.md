# API Testing CI Environment

This guide describes steps necessary for testing an API described in a swagger file with the [Dredd API Testing Framework](https://github.com/apiaryio/dredd) in a CI Environment \(Jenkins, TeamCity\).

## Environment Prerequisites

The following must be available in the CI environment before testing:

1. **Node.js** runtime MUST be available in the CI environment:

   ```text
    $ node -v
    v7.5.0
   ```

3. [**Dredd**](https://github.com/apiaryio/dredd) MUST be installed globally in the CI environment:

   ```text
    $ npm install -g dredd --no-optional
   ```

   ```text
    $ dredd --version
    dredd v2.2.5 (Darwin 16.4.0; x64)
   ```

## Testing an API

### Test Run Prerequisites

To test an API within the CI environment provisioned as mentioned in the environment prerequisites, you will need the following:

1. A `swagger.yaml` file with the description of API being tested

   The OpenAPI Specifciation file should be fetched from [API Design Platform](design-plaform.md). In the case of SwaggerHub API Design Platform, the file can be fetched manually or via their API. Refer to [Integrating with the SwaggerHub API](https://swagger.io/blog/api-development/integrating-with-the-swaggerhub-api/), for details how to use SwaggerHub API.

2. The host \(address\) of the service being tested

   ```text
     $ export API_HOST=http://deheremap7336.emea.adsint.biz:8004`
   ```

### Running the Test

Run:

```text
$ dredd swagger.yaml $API_HOST
```

> See [Dredd Command-line Interface](https://dredd.readthedocs.io/en/latest/usage-cli/).

The Dredd will perform the tests and exits usually if the tests have passed. You can check the test result as with any other Unix tools with:

```text
$ echo $?
```

Everything else but `0` should break the build. The test results will be visible in the CLI \(log\)
