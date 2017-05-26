# Jenkins CI Environment for Apiary Project



1. The CI Environment MUST have a Node.js runtime:

    ```
    $ node -v
    v7.5.0
    ```

2. For the testing, [Dredd](https://github.com/apiaryio/dredd) MUST be installed globally:

    ```
    $ npm install -g dredd --no-optional 
    ```

    ```
    $ dredd --version
    dredd v2.2.5 (Darwin 16.4.0; x64)
    ```
