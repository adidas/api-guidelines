# Search Requests
A search (filter) operation on a collection resource **SHOULD** be defined as safe, idempotent and cacheable, therefore using the [GET HTTP request method](https://adidas-group.gitbooks.io/api-guidelines/content/protocol/use-appropriate-methods.html). 

Every search parameter **SHOULD** be provided in the form of a query parameter. In the case of search parameters being mutually exclusive or require the presence of another parameter, the explanation **MUST** be part of operation's description.


#### Example
A collection of orders can be filtered by either article id it includes or by article manufacturer id. The two parameters are mutually exclusive and cannot be used together. The API description for such a design should look as follows:

```yaml
paths:
  /orders:
    x-summary: Collection of Orders

    get:
      summary: Retrieve or Search in the Collection of Orders
      description: | 
        
        This operation allows to retrieve a filtered list of orders based on multiple criteria:
        
        1. **Filter Orders by Article Id**
        2. **Filter Orders by Manufacturer Id**
        
      parameters:
        - name: article_id
          in: query
          description: | 
            Article Id. Denotes the id of an article that must be in the order.
            
            **Mutually exclusive** with `manufacturer_id`.

          required: false
          type: string
          x-example: article_id_1
          
        - name: manufacturer_id
          in: query
          description: |
            Manufacturer Id. Denotes an id of a manufacturer of an article that must be in the order.

            **Mutually exclusive** with `article_id`.
            
          required: false
          type: string
          x-example: manufacturer_id_1     
```

## Alternative Design
When it would be beneficial (e.g. one of the filter queries is more common than another one) a separate resource for the particular query **SHOULD** be provided. In such a case, the pivotal search parameter **MAY** be in the form of a path variable.

#### Example
Building on top of the example mentioned above, we will provide the filtering of orders by article id as a separate resource. 

```yaml
paths:
  /articles/{article_id}/orders:
    x-summary: Collection of Orders for given Article 

    get:
      summary: Retrieve the collection of Orders that contain given article.
```
