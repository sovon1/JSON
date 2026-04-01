# 11 - Real-World Patterns

JSON becomes much easier to reason about when you recognize the recurring shapes used across products and platforms.

## Pattern 1: Configuration

Configs are usually objects with stable keys.

Example uses:

- themes
- build settings
- deployment toggles
- app preferences

```json
{
  "theme": "dark",
  "colors": {
    "primary": "#007bff",
    "background": "#121212"
  },
  "showSidebar": true
}
```

## Pattern 2: API Documents

These often use:

- `data`
- `meta`
- `error`
- `links`

```json
{
  "data": {
    "id": "1",
    "type": "article",
    "title": "JSON Patterns"
  },
  "meta": {
    "processingTimeMs": 42
  }
}
```

## Pattern 3: Feature Flags

Flags are often boolean, but mature systems usually need metadata too:

- owner
- rollout percentage
- environments
- expiration date

```json
{
  "newDashboard": {
    "enabled": true,
    "rolloutPercentage": 25,
    "owner": "team-frontend",
    "environments": ["production", "staging"]
  }
}
```

## Pattern 4: Design Tokens

Frontend systems often store colors, spacing, typography, and motion tokens in JSON-like shapes.

```json
{
  "spacing": {
    "small": "4px",
    "medium": "8px",
    "large": "16px"
  },
  "typography": {
    "fontFamily": "Inter, sans-serif"
  }
}
```

## Pattern 5: Event Logs

Event payloads usually need:

- event name
- timestamp
- actor or subject identifiers
- a payload object

```jsonl
{"timestamp": "2023-11-01T08:00:00Z", "event": "login", "userId": "usr_1"}
{"timestamp": "2023-11-01T08:05:00Z", "event": "click", "target": "buy_btn"}
```

## Pattern 6: Validation Contracts

Schemas and contract files often describe other JSON files, not end-user data itself.

```json
{
  "type": "object",
  "properties": {
    "sku": { "type": "string" },
    "price": { "type": "number", "minimum": 0 }
  },
  "required": ["sku", "price"]
}
```

Once you notice these patterns, JSON stops looking like random punctuation and starts looking like a set of design tools.

Next: [12 - Advanced Design](./12-advanced-design.md)
