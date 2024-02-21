# Naming conventions

## Naming Conventions

### General Naming Rules

* Use American English
* Don't use acronyms
* Use `camelCase` unless stated otherwise
* Reconcile terms with adidas CDM

Every identifier **MUST** be in American English and written in `lowercase`. An identifier **SHOULD NOT** contain acronyms. CamelCase (`camelCase`) **MUST** be used to delimit combined words.

## Subject Naming Strategies

In order to make simple you **SHOULD** use _TopicNameStrategy_. The topic only support one kind of event.&#x20;

| **TopicNameStrategy** | <p>myNameTopic-Key</p><p><br>myNameTopic-Value</p> |
| --------------------- | -------------------------------------------------- |

**MAY** use _RecordNameStrategy_ or _TopicRecordNameStrategy_. The topics could support different kind of events. If you use any of this strategies you **MUST** make key/value explicit in the subject name.

| **RecordNameStrategy**      | <p>namespace.myKeyRecordName</p><p><br>namespace.myValueRecordName</p>                         |
| --------------------------- | ---------------------------------------------------------------------------------------------- |
| **TopicRecordNameStrategy** | <p>myNameTopic-namespace.myKeyRecordName</p><p><br>myNameTopic-namespace.myValueRecordName</p> |

Example of naming:

| Strategy                    | Example                                                                        |
| --------------------------- | ------------------------------------------------------------------------------ |
| **TopicNameStrategy**       | <p>orders-key</p><p><br>orders-value</p>                                       |
| **RecordNameStrategy**      | <p>com.adidas.fdp.orderKey</p><p><br>com.adidas.fpp.orderValue</p>             |
| **TopicRecordNameStrategy** | <p>store-com.adidas.fdp.orderKey</p><p><br>store-com.adidas.fdp.orderValue</p> |
