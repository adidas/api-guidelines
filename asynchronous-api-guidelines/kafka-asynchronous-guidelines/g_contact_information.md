# Contact Information

AsyncAPI specs **MUST** include at least one main contact under the info.contact section.

Aside from _name_ field, which describes the contact information, it supports two fields for the contact detail, _email_ and _url_. It **MUST** contain at least one of them. For _url_, it is suggested to specify an endpoint where the contact detail is clearly reflected.

The spec only allows to include one contact there, but it **MAY** also include additional contacts using extension fields. In case this is done, it **MUST** use the extension field _x-additional-responsibles_.

For example:

```yaml
...
info:
  ...
  contact:
    name: "Main point of contact"
    email: "team_dl@adidas.com"
    url: http://www.adidas.com/contact/team_dl
  x-additional-responsibles:
    - person2@adidas.com
    - person3@adidas.com
    - person4@adidas.com
```
