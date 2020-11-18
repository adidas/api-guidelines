# Complete API Development

> NOTE: The content of this file is outdated, refering to previous technologies used at adidas. It is kept for reference until its refresh

1. **Design the API**
   1. Analyze business requirements
   2. Identify affordances

      > e.g.: Create user, Submit order, Search for an article

   3. Identify resources

      > e.g.: User, Order, Article

   4. Identify relations

      > e.g.: User has many Orders via order relation, all of the required affordances should be mapped to relations.

   5. Formalize the design in the [Open API Specification](http://swagger.io/specification/) \(OAS, formerly known as "Swagger"\) format
   6. Follow the [adidas API guidelines](https://adidas.gitbook.io/api-guidelines/introduction/readme)
   7. Put the OAS file into (Swaggerhub adidas group)
   8. Make sure the OAS file passes all adidas API style guide checks using spectral
   9. Verify the design using Swaggerhub Documentation and Swaggerhub Mock Service
   10. Review the API Design
   11. Put the OAS file in a version control system \(VCS\) repository
   12. Set up a CD pipeline to push OAS file from VCS to Swaggerhub using our Jenkins library, whenever the file is changed
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

   6. Set up a [CI/CD pipeline](https://adidas-group.gitbooks.io/api-guidelines/content/guides/api-testing-ci-environment.html) to execute the Dredd tests automatically

3. **Deploy the API**
   1. Deploy the service
   2. Update the OAS file to add the deployment HOST

      > ```text
      > host: adidas.api.mashery.com
      > basePath: /demo-approval-api
      > ```

   3. Verify the deployment with Dredd

      > Use Dredd pointed towards the deployment host, be careful NOT to run it against the production OR using real production credentials.

   4. Monitor the API usage "From performance and technical standpoint."
4. **Expose the API using Kong**

5. **Use the API**

   > This step can be done at the same time as "Develop the API" thank Apiary hosted Mock, Inspector, and Documentation.

   1. Read API documentation at Swaggerhub
   2. Use API mock service provided by Swaggerhub
   3. Obtain your API keys
   4. Use production deployment

6. **Analyze the API**
   1. Analyze the technical performance metrics - using Grafana
   2. Check the logs in Kibana
   3. Collect the feedback from users
7. **Update API Design**

   > Based on the analysis, new or changing business requirements

   1. Create a new branch in the VCS repository with OAS file
   2. Create a new project \(alternative\) in Swaggerhub
   3. Make sure the CI/CD pipeline is updated.
   4. Modify the design \(OAS file\) accordingly, follow the "Design API" step
   5. Follow the [**rules for extending**](https://adidas-group.gitbooks.io/api-guidelines/content/core-principles/rules-for-extending.html) and [**adidas API guidelines versioning policies**](https://adidas-group.gitbooks.io/api-guidelines/content/evolution/versioning.html)
   6. Use VCS pull request \(PR\) to propose the change to review
   7. After the API Design change is verified, reviewed and approved, continue with the "Develop the API" phase
   8. Eventually, when the updated design is ready to be deployed for production, merge the branch into the production branch
   9. Follow this guide from "Expose the API using Kong" step

