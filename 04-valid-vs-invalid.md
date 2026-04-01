# 04 - Valid vs Invalid JSON

Many beginners think "I understand the idea, so my JSON should work." In practice, most early mistakes are syntax mistakes.

## Standard JSON Is Strict

A parser accepts JSON based on the format rules, not on what you meant.

## Common Invalid Patterns

### 1. Unquoted keys

Invalid:

```txt
{ name: "Asha" }
```

Valid:

```json
{ "name": "Asha" }
```

### 2. Single quotes

Invalid:

```txt
{ "name": 'Asha' }
```

Valid:

```json
{ "name": "Asha" }
```

### 3. Trailing commas

Invalid:

```txt
{
  "name": "Asha",
}
```

Valid:

```json
{
  "name": "Asha"
}
```

### 4. Comments

Invalid:

```txt
{
  "theme": "dark" // preferred theme
}
```

Standard JSON has no comments.

### 5. JavaScript-only values

Invalid in standard JSON:

```txt
{
  "score": Infinity,
  "value": undefined
}
```

## Duplicate Keys

This area is tricky. Some parsers accept duplicate keys, but behavior can differ and later values may silently overwrite earlier ones.

Example:

```json
{
  "role": "student",
  "role": "admin"
}
```

Treat duplicate keys as a bug, even if a parser lets them through.

## How To Debug Broken JSON

1. Check the first error location from your parser or editor.
2. Confirm braces and brackets are balanced.
3. Check every key and string for double quotes.
4. Remove trailing commas.
5. Remove comments.

## Broken Files To Inspect

Open these on purpose (or create a file and paste them in):

**`broken-commas.txt`**
```json
{
  "item": "laptop"
  "price": 999
}
```

**`comments-not-allowed.txt`**
```json
{
  "item": "laptop", // The main product
  "price": 999
}
```

**`unquoted-keys.txt`**
```json
{
  item: "laptop",
  price: 999
}
```

That habit is valuable because real work often involves repairing malformed JSON produced by humans or tools.

Next: [05 - Working with JSON](./05-working-with-json.md)
