# adidas Asynchronous API guidelines

## AsyncAPI guidelines for Kafka

### Contact information

AsyncAPI specs **MUST** include at least one main contact under the info.contact section. 

The spec only allows to include one contact there, but it **MAY** also include additional contacts using extension fields. In case this is done, it **MUST** use the extension field *x-additional-responsibles*.

For example:

```yaml
...
info:
  ...
  contact:
    name: "Main point of contact"
    email: "team_dl@adidas.com"
  x-additional-responsibles:
    - person2@adidas.com
    - person3@adidas.com
    - person4@adidas.com
```