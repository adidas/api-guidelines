---
description: Guidelines for the API design and development at adidas
---

# adidas API Guidelines

![adidas logo](https://adidas-group.gitbooks.io/api-guidelines/content/assets/adidas-logo.svg)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

[Read online at GitBook](https://adidas.gitbook.io/api-guidelines/)

### Motivation

The goal of this document is to facilitate the work and minimize the effort of all API users at adidas while protecting their investment and encouraging API adoption.

These guidelines lay down the foundation for collaboration, stability, and extensibility.

### Guidelines

The API Guidelines are split into two main parts:

* [General Guidelines](general-guidelines/general-guidelines.md)
* API type-specific Guidelines
  * [REST APIs Guidelines](rest-api-guidelines/rest.md)
  * [Kafka Guidelines](kafka-guidelines/kafka.md)

The general guidelines section discusses the core principles relevant to any kind of API. The API type-specific section further defines the guidelines specific to a given architectural style or API technique \(such as REST, Kafka or GraphQL APIs\).

### How to read the Guidelines

These Guidelines are available for online reading at [GitBook](https://adidas.gitbook.io/api-guidelines/) its source can be found on [GitHub](https://github.com/adidas/api-guidelines).

The CAPITALIZED words throughout these guidelines have a special meaning:

> ```text
> The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",
> "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL" in 
> this document are to be interpreted as described in RFC2119.
> ```

Refer to [RFC2119](https://www.ietf.org/rfc/rfc2119) for details.

### Validating your API Guidelines against OpenAPI Specification

In the `ruleset.md` file you can find a digest of API Guidelines rules which you can validating your API description documents with. If you are using OpenAPI Specification as the API description format you can also leverage the `.spectral.yaml` ruleset to automatically verify your specification compliance using [Spectral](github.com/stoplightio/spectral).

To install Spectral you will need Node.js and a package manager (npm or yarn).

```
npm install -g @stoplight/spectral

# OR

yarn global add @stoplight/spectral
```

Once installed, to verify your OAS file with spectral execute `spectral lint PATH_TO_YOUR_OAS` having the `.spectral.yaml` file inside the directory from which you are calling the command.

For further documentation on Spectral refer to their [documentation](https://stoplight.io/p/docs/gh/stoplightio/spectral/README.md).

### Questions & Comments

_Please contact_ [_Zdenek.Nemec@externals.adidas-group.com_](mailto:Zdenek.Nemec@externals.adidas-group.com), [_andrzej.jarzyna@adidas.com_](mailto:andrzej.jarzyna@adidas.com) or [_samir.amzani@adidas.com_](mailto:samir.amzani@adidas.com) _in case of questions._

## Intended Use Cases

This project is intended to provide the guidelines for design & development of APIs at adidas.

adidas is not responsible for the usage of this software for different purposes that the ones described in the use cases.

## License and Software Information

© adidas AG

adidas AG publishes this software and accompanied documentation \(if any\) subject to the terms of the MIT license with the aim of helping the community with our tools and libraries which we think can be also useful for other people. You will find a copy of the MIT license in the root folder of this package. All rights not explicitly granted to you under the MIT license remain the sole and exclusive property of adidas AG.

NOTICE: The software has been designed solely for the purpose of providing API design and development guidelines. The software is NOT designed, tested or verified for productive use whatsoever, nor or for any use related to high risk environments, such as health care, highly or fully autonomous driving, power plants, or other critical infrastructures or services.

If you want to contact adidas regarding the software, you can mail us at _software.engineering@adidas.com_.

For further information open the [adidas terms and conditions](https://github.com/adidas/adidas-contribution-guidelines/wiki/Terms-and-conditions) page.

### License

[MIT](https://github.com/adidas-group/api-guidelines/tree/657bc6fd49f1499f10c30ab18420f4bdb7cd841b/LICENSE/README.md)

