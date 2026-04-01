# 12 - Advanced Design

Advanced JSON work is not about writing more nested structures. It is about designing data that can survive growth, change, and multiple consumers.

## Principle 1: Design For Evolution

Assume your JSON will change.

Questions to ask:

- Can I add a new field later without breaking old consumers?
- If a field becomes optional, what does missing mean?
- If a field changes meaning, should it get a new name instead?

## Principle 2: Keep Types Stable

Avoid patterns like this:

- today: `"price": 19.99`
- tomorrow: `"price": "19.99 USD"`

That change breaks expectations and increases complexity everywhere downstream.

## Principle 3: Use Explicit Names

Prefer:

- `"createdAt"` over `"date"`
- `"isArchived"` over `"flag"`
- `"billingAddress"` over `"address"` when multiple address types exist

## Principle 4: Think About Null Carefully

`null` is easy to add and hard to reason about later.

Before using it, decide:

- Is this field unknown?
- Is it intentionally empty?
- Is it being cleared?
- Would omission be clearer?

## Principle 5: Separate External and Internal Shapes

External JSON contracts often need stability.
Internal application models often need convenience.

It is usually wise to translate external JSON into an internal shape rather than letting every internal layer depend directly on the wire format.

## Principle 6: Document Invariants

A schema says a field is a string. Your docs may need to say more:

- must be lowercase
- must be unique
- must match an existing entity
- must be an ISO 8601 timestamp in UTC

## Principle 7: Know When JSON Is The Wrong Tool

JSON is excellent for many boundaries, but not for every problem. Extremely high-throughput, binary-heavy, or strongly schema-driven systems sometimes use other formats internally. Even then, JSON often remains the easiest format for inspection and interoperability.

Advanced JSON design is contract design. The punctuation is the easy part. The meaning is the hard part.

Next: [13 - Glossary](./13-glossary.md)
