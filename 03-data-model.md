# 03 - Data Model

Learning JSON syntax is only the beginning. The harder and more valuable skill is shaping data well.

## Shape Is Meaning

Consider these two examples:

```json
{
  "users": [
    {
      "id": "u_001",
      "name": "Asha"
    }
  ]
}
```

```json
[
  {
    "id": "u_001",
    "name": "Asha"
  }
]
```

Both are valid. They do not mean the same thing.

- The first says the top-level object may hold several named sections, one of which is `users`.
- The second says the entire document itself is just a list of users.

Choosing a shape is a design decision.

## When To Use An Object

Use an object when:

- fields have names
- you need direct access by key
- the data represents one entity or one named container

Example:

```json
{
  "theme": "dark",
  "language": "en",
  "notifications": true
}
```

## When To Use An Array

Use an array when:

- order matters
- you have a sequence of similar items
- the item count can grow or shrink naturally

Example:

```json
{
  "tags": ["json", "api", "schema"]
}
```

## Design Principles That Age Well

- Keep one key responsible for one meaning.
- Keep value types stable. Do not make `"price"` a number in one place and a string in another.
- Use plural names for arrays when it helps clarity, such as `"users"` or `"tags"`.
- Use objects for grouped meaning, not just because nesting looks advanced.
- Prefer consistency over cleverness.

## A Simple Smell Test

Ask these questions:

1. What does this JSON represent?
2. What is the top-level thing?
3. Which parts are single values, and which parts are collections?
4. If a new field is added later, will the shape still make sense?

## Avoid Shape Chaos

This is valid JSON but poor design:

```json
{
  "user": "Asha",
  "tags": "json,api,frontend",
  "settings": ["dark", true, 14]
}
```

Why poor:

- `user` should probably be an object if it grows later.
- `tags` should probably be an array, not a comma-separated string.
- `settings` hides meaning because each array position means something different.

Good JSON is not only valid. Good JSON is readable, predictable, and easy to evolve.

Next: [04 - Valid vs Invalid JSON](./04-valid-vs-invalid.md)
