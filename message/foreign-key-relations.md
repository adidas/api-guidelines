# Foreign Key Relations

## Link or Embed Foreign Key Relation
When a resource representation includes relation with another (foreign) resource the relation **MUST** be expressed as a link relation or embed the related resource.

#### Example 
Use e.g.:

```json
{
  "_links": {
    "author": { "href": "/users/john" }
    ...
  }
  ...
}
```

or e.g.:

```json
{
  ...
  "_embedded": {
    "author": {
      "_links": { "self": "/users/john" },
      "name": "John Appleseed",
      "email": "john@apple.com"
    }
  }
}
```

instead e.g.:

```json
{
  ...
  "author_href": "/users/john"
}
```

## Nest Foreign Key Relation
If a foreign object has another identifier but URI or the foreign object isn't a resource the object **MUST** be nested.

#### Example
Use e.g.:

```json
{
  "author": {
    "id": "1234",
    "name": "John Appleseed",
    "email": "john@apple.com"    
  }
}
```

instead e.g.:

```json
{
  "author_id": "1234"
}
```

