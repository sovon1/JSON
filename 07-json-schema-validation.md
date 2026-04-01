# 07 - JSON Schema and Validation

Saying "this JSON should look like X" is not enough once multiple people or systems depend on it. You need a contract. JSON Schema is one of the most common ways to define that contract.

## What A Schema Does

A schema describes what JSON is allowed to look like.

It can express rules such as:

- this field is required
- this field must be a string
- this number must be at least 0
- this field can only be one of several values
- no extra fields are allowed

## Why Validation Matters

Without validation:

- bad data enters the system silently
- clients and servers disagree about shape
- bugs appear far away from the real cause

With validation:

- invalid input is rejected early
- contracts become clearer
- tooling gets stronger

## Common Schema Keywords

- `type`
- `properties`
- `required`
- `items`
- `enum`
- `minimum`
- `maximum`
- `additionalProperties`

## Tiny Example

```json
{
  "type": "object",
  "properties": {
    "name": { "type": "string" },
    "price": { "type": "number", "minimum": 0 }
  },
  "required": ["name", "price"],
  "additionalProperties": false
}
```

This says:

- the root must be an object
- `name` must exist and be a string
- `price` must exist and be a non-negative number
- extra fields are not allowed

## Practical Advice

- Use schemas for boundaries: API inputs, events, configs, and external files.
- Decide whether unknown fields should be allowed.
- Treat validation errors as product feedback, not just technical failures.

## Study A Real Example

Consider this realistic schema for a product:

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "Product",
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "format": "uuid"
    },
    "name": {
      "type": "string",
      "minLength": 3
    },
    "category": {
      "type": "string",
      "enum": ["electronics", "clothing", "home"]
    },
    "tags": {
      "type": "array",
      "items": { "type": "string" },
      "uniqueItems": true
    }
  },
  "required": ["id", "name", "category"],
  "additionalProperties": false
}
```
Notice how required fields, enums, and nested arrays work together to enforce a strict contract.

## Schema Is Not The Whole Story

A schema can prove structure, but not business meaning. A valid schema might still permit values that make no sense for your domain. Validation is necessary, not sufficient.

Next: [08 - Transform, Merge, and Patch](./08-transform-merge-patch.md)
