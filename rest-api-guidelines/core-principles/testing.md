# Testing

## DREDD

Every API description \(contract\) using HTTP\(S\) protocol **MUST** be tested against its API implementation. The tests **MUST** be executed using the [Dredd testing framework](https://github.com/apiaryio/dredd). The Dredd **MUST** [report the test results to Apiary](https://help.apiary.io/tools/automated-testing/testing-reporter/).

In addition to local runs, the tests **SHOULD** be an integral part the API implementation's CI/CD pipeline. The CI/CD pipeline **SHOULD** be configured to run the test whenever there is a change to either API description \(contract\) or its implementation.

## PACT

Every adidas **CORE** API **MUST** be tested additionally applying Consumer Driven Contract Testing principles. The tests **MUST** be executed using the [PACT contract testing tool](https://docs.pact.io/). PACT tests **MUST** use adidas [PACT-Broker](http://pact.ati.adidas.com/) to store results and evidences.

In addition to local runs, PACT tests **SHOULD** be an integral part of the API implementation's CI/CD pipeline. The CI/CD pipeline **SHOULD** be configured to run the test whenever there is a change to either API description \(contract\) or its implementation.

Using Consumer Driven Contract Testing with PACT is *not mandatory* for adidas **NON-CORE** APIs, but strongly recommended due to the advantages this approach brings. It will be also a proof of our Software Engineering practices maturity.

More information, guides and seeds about how to use PACT can be found on (internal link)[adidas Consumer Driven Contract Testing guide](https://tools.adidas-group.com/confluence/display/DSBP/adidas+Consumer+Driven+Contract+Testing+guide) page.

