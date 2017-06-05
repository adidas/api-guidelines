# The Complete API Development Guide


1. **Design the API**
  1. Analyze business requirements
  
  1. Identify affordances
    
      > e.g.: Create user, Submit order, Search for an article
      
  1. Identify resources
  
      > e.g.: User, Order, Article
      
  1. Identify relations
    
     > e.g.: User has many Orders via order relation, all of the required affordances should be mapped to relations.
     
  1. Formalize the design in the Open API Specification (OAS, formerly known as "Swagger") format
  
  1. Follow the adidas API guidelines
  
  1. Put the OAS file into Apiary adidas group
  
  1. Verify the design using Apiary Documentation and Apiary Mock Service
  
  1. Review the API Design
  
  1. Put the OAS file in a version control system (VCS) repository
  
  1. Set up a CD pipeline to push OAS file from VCS to Apiary, whenever the file is changed

1. **Develop the API**

  1. Check out the VCS repository with the OAS file 
  
  1. Set up the Dredd testing tool locally
  
  1. Configure the Dredd for your project
    
      ```
      $ dredd init
      ```
    
  1. Run the Dredd test locally
  
      > Against locally running API implementation, Every test should fail.
      
  1. Implement the API
  
      > Keep running the Dredd locally to see the progress.
      
  1. Set up a CI/CD pipeline to run the Dredd tests automatically
  
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

  1. API
  
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
    
  - API Documentation
    - Create new adidas API developer's portal page in the Mashery
      "Manage > Content > Documentation > APIs"
    - Embed Apiary documentation on that Page
    - Revisit the API documentation access policy / authorization
- Use the API
  "This can be done at the same time as "Develop the API" thank to Apiary hosted Mock, Inspector and Documentation"
  - Read API documentation at Apiary
  - Use API mock service provided by Apiary
  - Use API call inspector provided by Apiary
  - When available use API implementation via Apiary proxy
    "To debug the calls"
  - Use production deployment
- Analyze the API
  - Analyze the use of production API
    "Using Mashery"
  - Analyze the technical performance metrics 
  - Collect users feedback
- Update API Design
  "Based on the analysis and changed (new) business requirements"
  - Create a new branch in the VCS repository with OAS file
  - Create a new project (alternative) in Apiary 
  - Make sure the CI/CD pipeline is still
    - Set to push the OAS file to Apiary but make sure to modify the Apiary project name
    - Set to run Dredd test in the CI/CD
  - Modify the design (OAS file) accordingly, follow the "Design API" phase
  - Follow the rules for extending and adidas API guidelines versioning policies
  - Use VCS pull request (PR) to propose the change to review
  - After the API Design change is verified, reviewed and approved, continue with the "Develop the API" phase
  - Eventually, when the updated design is ready to be deployed for production, merge the branch to the production branch
  - Follow the guide from "Expose the API using Mashery" 