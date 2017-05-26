# Jenkins CI Environment for Apiary Project

This guide describes steps necessary for testing an API described in a swagger file with [Dredd](https://github.com/apiaryio/dredd) in a CI Environment (Jenkins, TeamCity). 

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
    
    To obtain an Apiary API key, head to <https://login.apiary.io/tokens> (NOTE: You will need the "ALL" Scope)

## Testing an API


### Test Run Prerequisites
To test an API within the CI environment provisioned as mentioned in the environment prerequisites you will need the following: 

1. The name (subdomain) of API project at Apiary

    ```
    $ export APIARY_API_NAME=bomapi3
    ```
    
    See [How to find the Apiary API name](https://help.apiary.io/faq/find-api-name/)

1. A `swagger.yaml` file with the description of API being tested

    To fetch the swagger.yaml file from Apiary run the following command before the test:

    ```
    $ apiary fetch --api-name=$APIARY_API_NAME --output="swagger.yaml"
    ```

1. The host (address) of the service being tested

     ```
     $ export API_HOST=http://deheremap7336.emea.adsint.biz:8004`
     ```
     
### Running the Test
 
With all of the above (`APIARY_API_KEY`, `APIARY_API_NAME`, `API_HOST`, set up and `swagger.yaml` file present in the current directory), run:


```
$ dredd swagger.yaml $HOST -r apiary
```
    
The Dredd will perform the tests and exits normally if the tests has passed. You can check the test result as with any other Unix tools with: 

``` 
$ echo $?
```
    
Everything else but `0` should break the build. The test results will be visible in the CLI (log) as well as in Apiary.
    
    









