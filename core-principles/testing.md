# Testing – Contract Validation
Every API description (contract) SHOULD be tested against its API implementation. The tests MUST be concluded using the [Dredd testing framework](https://github.com/apiaryio/dredd). The Dredd MUST [report the test results to Apiary](https://help.apiary.io/tools/automated-testing/testing-reporter/). 

In addition to local runs, the tests SHOULD be an integral part the API implementation's CI/CD pipeline.


