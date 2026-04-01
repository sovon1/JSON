# 06 - JSON and APIs

APIs are where many developers first become serious about JSON.

## Why APIs Love JSON

- It is text-based and easy to transmit over HTTP.
- It maps naturally to objects and arrays in many languages.
- It is readable enough for debugging.

## A Simple API Response

```json
{
  "data": [
    {
      "id": "usr_001",
      "name": "Asha",
      "email": "asha@example.com"
    }
  ],
  "meta": {
    "page": 1,
    "pageSize": 20,
    "total": 1
  }
}
```

This shape works well because:

- `data` holds the main records
- `meta` holds metadata about the response

## API Payload Design Principles

- Be consistent with naming.
- Keep field types stable.
- Use nested objects when they represent real sub-structures.
- Keep error responses predictable.
- Do not overload one field with multiple meanings.

## A Good Error Shape

```json
{
  "error": {
    "code": "USER_NOT_FOUND",
    "message": "No user exists with that id."
  }
}
```

Predictable error shapes make client code and observability much easier.

## Pagination

Large collections should not always be returned all at once. JSON responses often include:

- current page
- page size
- total count
- next cursor or token

## Optional vs Required Fields

If a field is required for correct behavior, document it and validate it. If a field is optional, define what happens when it is missing.

## Versioning Starts With Design

Good JSON API design makes versioning easier later:

- avoid vague names
- avoid mixing unrelated concepts into one field
- avoid sending surprise types

Here is a comprehensive example of an API response structure:

```json
{
  "data": [
    {
      "id": "usr_001",
      "name": "Asha",
      "email": "asha@example.com",
      "roles": ["admin", "user"]
    }
  ],
  "meta": {
    "page": 1,
    "pageSize": 20,
    "total": 1,
    "nextCursor": null
  },
  "links": {
    "self": "https://api.example.com/users?page=1",
    "next": null
  }
}
```
Inspect this structure carefully to see how `data`, `meta`, and `links` work together to provide a complete context for the client.

Next: [07 - JSON Schema and Validation](./07-json-schema-validation.md)
