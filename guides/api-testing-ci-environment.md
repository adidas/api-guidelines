# Jenkins CI Environment for Apiary Project

This guide describes steps necessary for testing an API described in a swagger file with Dredd in a CI Environment (Jenkins, TeamCity). 

## Prerequisites
The following must be available in the CI environment prior to testing:

1. Node.js runtime:

    ```
    $ node -v
    v7.5.0
    ```

1. [Dredd](https://github.com/apiaryio/dredd) MUST be installed globally in the CI environment:

    ```
    $ npm install -g dredd --no-optional 
    ```

    ```
    $ dredd --version
    dredd v2.2.5 (Darwin 16.4.0; x64)
    ```
    
1. Apiary API Key

    ```
    $ export APIARY_API_KEY=xyz
    ```

## Testing an API

1. A `swagger.yaml` file with the description of API being tested.

1.

