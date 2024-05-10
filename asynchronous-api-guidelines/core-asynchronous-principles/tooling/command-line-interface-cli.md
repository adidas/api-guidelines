# Command Line Interface (CLI)

Unfortunately, Swaggerhub is not offering a Command Line Interface (CLI) tool which allows including this capability as part of CICD workflows.&#x20;

For this, there is an official AsyncAPI CLI tool which can be checked here: https://www.asyncapi.com/tools/cli. This includes a validator against the AsyncAPI spec, templated generators, version conversion, spec optimizer, bundler, etc.

For example, to validate a yaml spec file:

```
asyncapi validate --file your-asyncapi-file.yaml
```
