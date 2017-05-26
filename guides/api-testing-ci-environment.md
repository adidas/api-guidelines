# Jenkins CI Environment for Apiary Project

This guide describes steps necessary for testing an API described in a swagger file with Dredd in a CI Environment (Jenkins, TeamCity). 

## Environment Prerequisites
The following must be available in the CI environment prior to testing:

1. **Node.js** runtime MUST be available in the CI environment:

    ```
    $ node -v
    v7.5.0
    ```
    
1. **Ruby** runtime MUST be available in the CI environment:

    ```
    $ ruby -v
    ruby 2.4.0p0 (2016-12-24 revision 57164) [x86_64-darwin16]
    ```

1. [**Dredd**](https://github.com/apiaryio/dredd) MUST be installed globally in the CI environment:

    ```
    $ npm install -g dredd --no-optional 
    ```

    ```
    $ dredd --version
    dredd v2.2.5 (Darwin 16.4.0; x64)
    ```
    
1. [**Apiary CLI Tool**](https://help.apiary.io/tools/apiary-cli) MUST be intalled globally in the CI environment:

    ```
    $ gem install apiaryio
    ```

    ```
    $ apiary version
    0.8.0
    ```
    
1. **Apiary API Key** MUST be set in the CI Environment environment variables:

    ```
    $ export APIARY_API_KEY=xyz
    ```
    
    To obtain an Apiary API key, head to <https://login.apiary.io/tokens>.

## Testing an API

1. A `swagger.yaml` file with the description of API being tested.

1.

