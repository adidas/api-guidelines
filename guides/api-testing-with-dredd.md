# API Testing with Dredd

1. Ruby 

    ```
    $ ruby -v
    ruby 2.4.0p0 (2016-12-24 revision 57164) [x86_64-darwin16]
    ```

2. Node.js

    ```
    $ node -v
    v7.5.0
    ```

3. Install Apiary CLI

    ```
    $ gem install apiaryio
    ```

    ```
    $ apiary version
    0.8.0
    ```


4. Install Dredd

    ```
    $ npm install -g dredd --no-optional 
    ```

    ```
    $ dredd --version
    dredd v2.2.5 (Darwin 16.4.0; x64)
    ```

5. Fetch API Description (Swagger) from Apiary

    <https://help.apiary.io/tools/apiary-cli>
    
    <https://login.apiary.io/tokens>

    ```
    $ APIARY_API_KEY=<APIARY_API_KEY> apiary fetch --api-name="<API_NAME>" --output="swagger.yaml"
    ```
    
    EXAMPLE: `API_NAME=bomapi3`, `APIARY_API_KEY=122131212121212112`
    
    
6. Run Tests

    ```
    $ dredd swagger.yaml <HOST>
    ```
    
    EXAMPLE: `HOST=deheremap7336.emea.adsint.biz:8004` 

7. Run Tests (The preferred alternative connected to Apiary)

    NOTE: You have to have a `dredd.yml` generated before hand: `$ dredd init -r apiary -j apiaryApiKey:<APIARY_API_KEY> -j apiaryApiName:<API_NAME>`. 
    
    ```
    $ dredd
    ```