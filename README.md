# adidas API Guidelines



<figure><picture><source srcset=".gitbook/assets/adidas_company_logo_BWr.png" media="(prefers-color-scheme: dark)"><img src=".gitbook/assets/adidas_company_logo_BWp.png" alt=""></picture><figcaption></figcaption></figure>

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

[Read online at GitBook](https://adidas.gitbook.io/api-guidelines/)

### Motivation

The goal of this document is to facilitate the work and minimize the effort of all API users at adidas while protecting their investment and encouraging API First adoption.

These guidelines lay down the foundation for collaboration, stability, and extensibility.

### Guidelines

The API Guidelines are split into two main parts:

* [General Guidelines](https://adidas.gitbook.io/api-guidelines/general-guidelines/general-guidelines)
* API type-specific Guidelines
  * [REST APIs Guidelines](https://adidas.gitbook.io/api-guidelines/rest-api-guidelines/rest)
  * [Asynchronous APIs Guidelines](https://adidas.gitbook.io/api-guidelines/asynchronous-api-guidelines/a_introduction)

The general guidelines section discusses the core principles relevant to any kind of API.&#x20;

The API type-specific section further defines the guidelines specific to a given architectural style or API technique (such as REST, Kafka or GraphQL APIs).

### How to read the Guidelines

These guidelines are available for online reading at [GitBook](https://adidas.gitbook.io/api-guidelines/). The source code can be found on [GitHub](https://github.com/adidas/api-guidelines).

The CAPITALIZED words throughout these guidelines have a special meaning:

> ```
> The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",
> "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL" in 
> this document are to be interpreted as described in RFC2119.
> ```

Refer to [RFC2119](https://www.rfc-editor.org/rfc/rfc2119) for details.

### Validating your API specification against OpenAPI & Async rules

In the `ruleset.md` file you can find a digest of API Guidelines rules which you can use to validate your API description documents.

If you are using OpenAPI or AsyncAPI specification as API description format, you can also leverage the `adidas-spectral.yaml` ruleset to automatically lint your specification compliance using [Spectral](https://meta.stoplight.io/docs/spectral/674b27b261c3c-overview).

> To install Spectral, you will need Node.js and a package manager (npm or yarn).

```bash
npm install -g @stoplight/spectral-cli

# OR

yarn global add @stoplight/spectral-cli
```

Once installed, to verify your _oas_ or _async_ file with spectral execute:

```bash
spectral lint <api-specification-file> --ruleset adidas-spectral.yaml
```

### Contact Us

In case you have any questions or comments, please utilize the appropriate GitHub collaboration tools, such as issues, pull requests, and discussions.

If you want to contact adidas API Team regarding these guidelines, you can mail us at

&#x20;_**api-team@adidas.com**_

## Intended Use Cases

This project is intended to provide the guidelines for design & development of APIs at adidas.

Adidas is not responsible for the usage of this software for different purposes that the ones described in the use cases.

## Last Review

February 2025

## License and Software Information

© adidas AG

adidas AG publishes this software and accompanied documentation (if any) subject to the terms of the MIT license with the aim of helping the community with our tools and libraries which we think can be also useful for other people. You will find a copy of the MIT license in the root folder of this package. All rights not explicitly granted to you under the MIT license remain the sole and exclusive property of adidas AG.

NOTICE: The software has been designed solely for the purpose of providing API design and development guidelines. The software is NOT designed, tested or verified for productive use whatsoever, nor or for any use related to high-risk environments, such as health care, highly or fully autonomous driving, power plants, or other critical infrastructures or services.

For further information open the [adidas terms and conditions](https://github.com/adidas/adidas-contribution-guidelines/wiki/Terms-and-conditions) page.
