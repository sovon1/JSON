# 08 - Transform, Merge, and Patch

Most real systems do not just store JSON. They reshape it.

## Common Transformation Jobs

- rename fields
- remove internal-only fields
- flatten nested data
- group records
- normalize different producer formats into one contract

## A Useful Pipeline

1. Parse incoming JSON
2. Validate it
3. Normalize it into your internal shape
4. Apply business logic
5. Serialize the result

## Merge Patch vs JSON Patch

These two are often confused.

### JSON Merge Patch

Merge patch describes the desired changes by example.

Patch:

```json
{
  "status": "published",
  "description": null
}
```

Typical meaning:

- set `status` to `"published"`
- remove `description`

This style is simple when you want partial updates to an object.

### JSON Patch

JSON Patch is operation-based. It uses an array of actions such as `add`, `remove`, and `replace`.

Example:

```json
[
  { "op": "replace", "path": "/status", "value": "published" }
]
```

This is more explicit and works well when precise mutation steps matter.

## Design Advice

- Use merge patch for straightforward object updates.
- Use JSON Patch when you need precise, auditable operations.
- Document patch semantics clearly, especially what `null` means.

## Shape Stability Matters

Transformations become painful when upstream JSON changes type or naming unexpectedly. Good contracts reduce transformation complexity.

Consider this base document:

```json
{
  "title": "Goodbye!",
  "author": {
    "givenName": "John",
    "familyName": "Doe"
  },
  "tags": ["example", "sample"],
  "content": "This will be unchanged"
}
```

And this merge patch:

```json
{
  "title": "Hello!",
  "phoneNumber": "+01-123-456-7890",
  "author": {
    "familyName": null
  },
  "tags": ["example"]
}
```

When applied, the `title` changes, `phoneNumber` is added, `author.familyName` is removed, and the `tags` array is entirely replaced.

Next: [09 - Large JSON and JSONL](./09-large-json-and-jsonl.md)
