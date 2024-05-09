# adidas Asynchronous API guidelines

## AsyncAPI tools

### API Design platform

The current platform available in adidas to design, host, and render AsyncAPI specs is [Swaggerhub](https://design.api.3stripes.io/).

Every AsyncAPI spec **MUST** be hosted in Swaggerhub under the *adidas* organization.

In the future, some mechanisms will be provided to auto generate AsyncAPI specs automatically from the assets created in the Streaming Platform. Until then, those specs will be created manually in the platform following the API-first approach if possible.

**Important note** Swaggerhub has limited capabilities with regards to discoverability, search and filtering of APIs. Other alternatives are being evaluated. Any upcoming decision impacting this will be reflected in this document in the future.

### Editors

Aside from Swaggerhub editing capabilities, other alternative editor options are available:

- AsyncAPI Studio: A web-based editor designed specifically for creating and validating AsyncAPI documents.
- Visual Studio Code: VS Code can be extended with plugins like "AsyncAPI for VS Code" to provide AsyncAPI-specific features,  for editing AsyncAPI files.

### Command Line Interface (CLI) tool

Unfortunately, Swaggerhub is not offering a Command Line Interface (CLI) tool which allows including this capability as part of CICD workflows. 

For this, there is an official AsyncAPI CLI tool which can be checked here: https://www.asyncapi.com/tools/cli. This includes a validator against the AsyncAPI spec, templated generators, version conversion, spec optimizer, bundler, etc.

For example, to validate a yaml spec file:

```
asyncapi validate --file your-asyncapi-file.yaml
```

### Generators

These tools are capable of generate a variety of outputs from any valid AsyncAPI spec, including:

- API documentation in various formats like HTML, Markdown, or OpenAPI
- Code samples in various programming languages like Python, Java, and Node.js based on your API definition. 
- Functionally complete applications

There is an official generator tool which can be checked here: https://www.asyncapi.com/docs/tools/generator.