# 10 - Security and Reliability

Once JSON crosses system boundaries, you should stop treating it as friendly by default.

## Assume Input Is Untrusted

Any external JSON can be:

- malformed
- unexpectedly large
- deeply nested
- missing required fields
- carrying unknown fields
- semantically wrong even if syntactically valid

## Reliability Risks

### Type drift

The same field changes from number to string or from object to array.

### Duplicate keys

Different parsers may handle them differently.

### Precision loss

Large numbers may not survive every language or storage system exactly.

### Null confusion

Does `null` mean "empty," "unknown," "clear this field," or "not applicable"?

### Unknown fields

Will consumers ignore them, reject them, or accidentally leak them onward?

## Security Risks

- secrets accidentally logged in JSON
- over-trusting client-supplied fields
- deserializing without validation
- allowing giant payloads to consume resources
- using JSON from external sources to drive dangerous behavior directly

## Guardrails That Help

- validate at boundaries
- cap payload size
- cap nesting depth when relevant
- document nullability clearly
- normalize before core business logic
- log safely and redact secrets

## Reliability Is Mostly About Boring Discipline

Most JSON disasters are not caused by exotic edge cases. They come from missing rules, weak validation, vague contracts, and silent assumptions.

Consider this feature flags configuration:

```json
{
  "enableNewCheckout": true,
  "maxRetries": 3,
  "betaUsersOnly": false
}
```

Ask yourself what would happen if the type of `maxRetries` unexpectedly changed from a number to a string (`"3"`), or if `enableNewCheckout` became `null`. Without validation, your application might crash or behave unpredictably.

Next: [11 - Real-World Patterns](./11-real-world-patterns.md)
