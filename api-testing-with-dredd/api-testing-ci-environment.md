# Jenkins CI Environment for Apiary Project

This guide describes steps necessary for testing an API with Dredd in a CI Environment (Jenkins, TeamCity). 

## Preparation
1. The CI environment MUST have a Node.js runtime:

    ```
    $ node -v
    v7.5.0
    ```

2. [Dredd](https://github.com/apiaryio/dredd) MUST be installed globally in the CI environment:


    ```
    $ npm install -g dredd --no-optional 
    ```

    ```
    $ dredd --version
    dredd v2.2.5 (Darwin 16.4.0; x64)
    ```
