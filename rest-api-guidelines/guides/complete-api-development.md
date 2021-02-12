# Complete API Development

1-Design --> 2-Develop --> 3-Deploy --> 4-API Gateway --> 5-Use --> 6-Analyze --> 7-Update

1. **Design the API**
   1. Analyze business requirements
   2. Identify affordances

      > e.g.: Create user, Submit order, Search for an article

   3. Identify resources

      > e.g.: User, Order, Article

   4. Identify relations

      > e.g.: User has many Orders via order relation, all of the required affordances should be mapped to relations.

   5. Formalize the design in the [Open API Specification](http://swagger.io/specification/) \(OAS, formerly known as "Swagger"\) version 2.x or 3.0.x format.

      > Use **[SwaggerHub](https://design.api.3stripes.io/)** for the whole design process to the publication of the API specification.

   6. Follow the [adidas API guidelines](https://adidas.gitbook.io/api-guidelines/introduction/readme)
   7. Publish the OAS file in SwaggerHub [under a specific project](https://design.api.3stripes.io/help/organizations/index) in the adidas organization. 
   8. Verify the OAS file you have written passes the Spectral test.
   9. Make sure the OAS file passes all adidas SwaggerHub style guide checks. A red banned will be showed at the bottom of the editor if something is wrong with the OAS content.
   10. Review the API Design
   11. Put the OAS file in a version control system \(VCS\) repository
   12. Set up a CD pipeline to push OAS file from VCS to SwaggerHub, whenever the file is changed

2. **Develop the API**
   1. Check out the VCS repository with the OAS file
   2. Set up the [Dredd API testing tool](https://github.com/apiaryio/dredd) locally
   3. Configure the Dredd for your project
      ```text
       $ dredd init
      ```
   4. Run the Dredd test locally

      > Against locally running API implementation, Every test should fail.

   5. Implement the API

      > Keep running the Dredd locally to see the progress.

   6. Set up a [CI/CD pipeline](https://adidas.gitbook.io/api-guidelines/rest-api-guidelines/guides/api-testing-ci-environment) to execute the Dredd tests automatically.

      > NOTE: Both TeamCity and Jenkins environments are available, contact adidas API Evangelist for details.

3. **Deploy the API**
   1. Deploy the service
   2. Update the OAS file to add the deployment host (OAS v2.x) or the deployment servers (OAS v3.0.x). For instance:

      OAS Version 2.x
      ```text
      host: adidas.api.myapp.com
      basePath: /demo-approval-api
      ```

      OAS Version 3.0.x
      ```yaml
      servers:
         - url: https://adidas.api.myapp.com/
           description: Production cluster
         - url: http://stg.adidas.api.myapp.com/
           description: Staging cluster
         - url: http://dev.adidas.api.myapp.com/
           description: Development cluster
      ```

   3. Verify the deployment with Dredd

      > Use Dredd pointed towards the deployment host, be careful NOT to run it against the production OR using real production credentials.

   4. Monitor the API usage "From performance and technical standpoint."
4. **Expose the API using Kong**
   > Ensure you have all the operational context information:
      - Type of application
      - Servers
      - Detailed ownership information (Organiational unit, API Owner, Support contact, etc)

   > Ensure you have all the Non-Functional Requirements for your API like:
      - Caching strategy detailed for each endpoint
      - Rate Limits information
      - Scope (internal to adidas or public)
      - List of consumers and ACLs
      - Authentication & Authorization

   Please read the [API On-Boarding Kong](https://tools.adidas-group.com/confluence/pages/viewpage.action?spaceKey=API2&title=Demand+-+API+Onboarding+in+Kong) to include your API in the adidas API Gateway if it is not done yet.
   
   Once all the information is ready create an [on-boarding request in JIRA](https://tools.adidas-group.com/jira/Secure/CreateIssueDetails!Init.jspa?issuetype=3&pid=28605&issueTemplateId=3701&summary=null&priority=2&labels=Kong-Onboarding).

   > Read the [API Team Service Catalog](https://tools.adidas-group.com/confluence/pages/viewpage.action?spaceKey=API2&title=Service+catalog) to get more information.

5. **Use the API**

   > This step can be done at the same time as "Develop the API" using [SwaggerHub auto-mock service](https://design.api.3stripes.io/help/integrations/api-auto-mocking) and the continuous inspection of the OAS file.

   1. Read API documentation at SwaggerHub
   2. Use an API implementation stub provided by SwaggerHub. 

      > This is a good starting point for implementing the API, you can run and test it locally, implement the business logic for the API, and then deploy it to your server.
   
   3. Obtain your API key and other information to apply the authentication/authorization mode in your API

      > The key is part of the adidas API Gateway on-boarding process and can be requested from your dashboard in the adidas API developer's portal.

   4. Use production deployment

6. **Analyze the API**
   1. Examine the use of production API Using Kong
   2. Analyze the technical performance metrics
   3. Collect the feedback from users

7. **Update API Design**

   > Based on the analysis, new or changing business requirements

   1. Create a new branch in the VCS repository with OAS file
   2. Create a new project \(alternative\) in SwaggerHub
   3. Make sure the CI/CD pipeline is:
      1. Set to push the OAS file to SwaggerHub but make sure to modify the SwaggerHub project name under the adidas organization
      2. Set to run Dredd test in the CI/CD
   4. Modify the design \(OAS file\) accordingly, follow the "Design API" step
   5. Follow the adidas API Guidelines for [**changes and versioning**](https://adidas.gitbook.io/api-guidelines/rest-api-guidelines/evolution/versioning)
   6. Use VCS pull request \(PR\) to propose the change to review
   7. After the API Design change is verified, reviewed and approved, continue with the "Develop the API" phase
   8. Eventually, when the updated design is ready to be deployed for production, merge the branch into the production branch
   9. Follow this guide from "Expose the API using Kong" step

