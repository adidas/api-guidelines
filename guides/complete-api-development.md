# The Complete API Development Guide


1. **Design the API**
  1. Analyze business requirements
  
  1. Identify affordances
    
      > e.g.: Create user, Submit order, Search for an article
      
  1. Identify resources
  
      > e.g.: User, Order, Article
      
  1. Identify relations
    
     > e.g.: User has many Orders via order relation, all of the required affordances should be mapped to relations.
     
  1. Formalize the design in the [Open API Specification](http://swagger.io/specification/) (OAS, formerly known as "Swagger") format
  
  1. Follow the [adidas API guidelines](https://adidas-group.gitbooks.io/api-guidelines/content/)
  
  1. Make sure the OAS file passes all adidas API Apiary style guide checks
  
  1. Put the OAS file into [Apiary adidas group](https://apiary.io)
  
  1. Verify the design using Apiary Documentation and Apiary Mock Service
  
  1. Review the API Design
  
  1. Put the OAS file in a version control system (VCS) repository
  
  1. Set up a CD pipeline to push OAS file from VCS to Apiary, whenever the file is changed

1. **Develop the API**

  1. Check out the VCS repository with the OAS file 
  
  1. Set up the [Dredd API testing tool](https://github.com/apiaryio/dredd) locally
  
  1. Configure the Dredd for your project
    
      ```
      $ dredd init
      ```
    
  1. Run the Dredd test locally
  
      > Against locally running API implementation, Every test should fail.
      
  1. Implement the API
  
      > Keep running the Dredd locally to see the progress.
      
  1. Set up a [CI/CD pipeline](https://adidas-group.gitbooks.io/api-guidelines/content/guides/api-testing-ci-environment.html) to run the Dredd tests automatically
  
      > NOTE: Both TeamCity and Jenkis enviroments are available, contact adidas API evangelist for details.
  
1. **Deploy the API**

  1. Deploy the service
  
  1. Update the OAS file to add the deployment HOST
    
      > ```
      > host: adidas.api.mashery.com
      > basePath: /demo-approval-api
      > ```
    
  1. Verify the deployment with Dredd
    
      > Use dredd pointed towards the deployment host, be careful to NOT run it against the production OR using real production credentials.
      
  1. Monitor the API usage
    "From performance and technical standpoint"
    
1. **Expose the API using Mashery**

  1. **API**
  
    1. Create new API Definition in Mashery
    
    1. Create a new API Endpoint the API Definition
    
        > Set the "Your Endpoint Address" to the internal deployment HOST.
      
    1. Create a new API Package in Mashery
    
    1. Create a new API Plan within the API Package
    
    1. Use Mashery API Designer to add the newly created API Definitions' API Endpoint to the 
    API Plan
    
    1. Revisit the API Plan's API key default settings
    
    1. Revisit the API Plan's API default rate limits 
    
    1. Revisit the API Plan's access policy / authorization
    
  1. **API Documentation**
  
    1. Create new adidas API developer's portal page in the Mashery
    
      > Manage > Content > Documentation > APIs
      
    1. [Embed Apiary documentation](https://help.apiary.io/tools/embed/#apiary-embed-api-reference) on the newly created API Page
    
    1. Revisit the API documentation access policy / authorization
    
1. **Use the API**

   > This step can be done at the same time as "Develop the API" thank to Apiary hosted Mock, Inspector and Documentation.
   
  1. Read API documentation at Apiary
  
  1. Use API mock service provided by Apiary
  
  1. Use API call inspector provided by Apiary
  
  1. Obtain your API key
    
    > The key is part of the API Plan created in Mashery and can be requested from your dashboard in the adidas API developer's portal.
  
  1. When available use API implementation via Apiary proxy to debug the API calls

  1. Use production deployment
  
1. **Analyze the API**
  1. Analyze the use of production API Using Mashery
  
  1. Analyze the technical performance metrics
  
  1. Collect the feedback from users
  
1. **Update API Design**
  
  > Based on the analysis, new or changing business requirements
  
  1. Create a new branch in the VCS repository with OAS file
  
  1. Create a new project (alternative) in Apiary 
  
  1. Make sure the CI/CD pipeline is:
  
    1. Set to push the OAS file to Apiary but make sure to modify the Apiary project name
    
    1. Set to run Dredd test in the CI/CD
    
  1. Modify the design (OAS file) accordingly, follow the "Design API" step
  
  1. Follow the [**rules for extending**](https://adidas-group.gitbooks.io/api-guidelines/content/core-principles/rules-for-extending.html) and [**adidas API guidelines versioning policies**](https://adidas-group.gitbooks.io/api-guidelines/content/evolution/versioning.html)
  
  1. Use VCS pull request (PR) to propose the change to review
  
  1. After the API Design change is verified, reviewed and approved, continue with the "Develop the API" phase
  
  1. Eventually, when the updated design is ready to be deployed for production, merge the branch to the production branch
  
  1. Follow this guide from "Expose the API using Mashery" step
  