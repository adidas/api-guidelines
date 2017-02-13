# API First

Everyone **MUST** follow the **API first** principle.

**API first** principle is extension of **Contract first** architecture principle.
Therefore development of an API **MUST** always start with **API design** without any upfront coding activities.
An API design **MUST** be formalized in a form of an **API description** using [Open API Specification](./openapi-specification.md) and stored in adidas [API design platform](./apiary.md) and agreed by all stakeholders.

Clearly describing what API is supposed to do before coding it, helps to facilitate discussion between stakeholders and allows to receive feedback in early stage of the API development process. 
It also helps to establish governance on API's to check that certain quality is met and API guidelines are being followed.

**API description is master of truth, not the API implementation.**
API implementation **MUST** always be compliant to respective API description which represent the  [Contract](./contract.md) between API and it's consumer.

> NOTE: 
* It's not acceptable that API is developed first and later on described in some proprietary format.
* It's not acceptable that API implementation doesn't implement it's description.




      
 