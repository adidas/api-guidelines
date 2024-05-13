# Contact Information

AsyncAPI specs **MUST** include at least one main contact under the info.contact section.

The spec only allows to include one contact there, but it **MAY** also include additional contacts using extension fields. In case this is done, it **MUST** use the extension field _x-additional-responsibles_.

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
