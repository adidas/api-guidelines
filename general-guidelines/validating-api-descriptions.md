# Validating API Description

If you want to follow adidas API design guidelines for REST APIs you MAY validate your OAS file using [Spectral](https://github.com/stoplightio/spectral) and the adidas ruleset file.

## Installing Spectral

To install Spectral you will need Node.js and a package manager (npm or yarn).

```
npm install -g @stoplight/spectral

# OR

yarn global add @stoplight/spectral
```

### Docker

Spectral is also available as a Docker image, which can be handy for all sorts of things, like if you're contributing code to Spectral, want to integrate it into your CI build.

```
docker run --rm -it stoplight/spectral lint "${url}"
```

If the file you want to lint is on your computer, you'll need to mount the directory where the file resides as a volume

```
docker run --rm -it -v $(pwd):/tmp stoplight/spectral lint "/tmp/file.yaml"
```

## Using Spectral

Once installed Spectral, you can validate an OAS file (in YAML or JSON format) according to a given set of rules. Spectral has a predefined set of rules validating OpenAPI 2.x (Swagger) and OpenAPI 3.x files.

Spectral comes with a CLI and can be run from your command line:

```
spectral lint <oas-file>
```

For more details about how to utilize Spectral CLI you can check the CLI built-in help:

```
spectral lint -h
```

or go to the official [Spectral documentation](https://stoplight.io/p/docs/gh/stoplightio/spectral/docs/guides/cli.md).

Spectral can also be used from within JavaScript. For details on how to accomplish this, please refer to the [documentation](https://stoplight.io/p/docs/gh/stoplightio/spectral/docs/guides/javascript.md).

## Validating with Adidas API Guidelines

To check whether your API Specification complies with Adidas API Guidelines copy the `.spectral` file from this repository ([here](https://github.com/adidas/api-guidelines/blob/master/.spectral.yml)).

Once it is in the same directory as the one from which you are calling spectral it will be used automatically.

``` 
spectral lint <oas-file>
```

### Validation problems

Spectral defines 4 levels of problem severity:

1. error - the specification either does not pass standard YAML/JSON structure validation, standard OAS2/OAS3 validation or is not compliant with core adidas guidelines.
2. warning - the specification lacks certain important validation check (e.g. `hosts` for OAS2) which are not required, but you should be cautious about them.
3. information - there are some best practices which you did not implement in your specification and should consider doing so.
4. hint - you should be aware that there are some additional best practices which you can consider implementing in your specification.

Currently any problem of severity of error or warning will cause a failure status code of `1`. This means that any `error` or `warning` in your specification will prevent your CI/CD pipeline from succeeding. During design process you may want to ignore certain warnings, such as the runtime information (e.g. `hosts` or `servers`). In order to do that you can add a `--skip-rule` flag:

```
spectral lint my-api-spec.yaml --skip-rule=protocol-https-only-oas3
```
