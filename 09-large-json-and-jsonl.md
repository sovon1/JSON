# 09 - Large JSON and JSONL

JSON feels easy when the document is small. The moment the file becomes huge, the strategy changes.

## Whole-Document JSON

A normal `.json` file is usually one complete JSON value, often an object or an array.

That works well for:

- configs
- API responses
- compact documents

It becomes awkward for:

- append-only logs
- large datasets
- long-running event streams

## JSONL and NDJSON

JSON Lines, often written as `.jsonl`, stores one JSON object per line.

Example:

```json
{"event":"page_view","userId":"usr_001"}
{"event":"add_to_cart","userId":"usr_001"}
{"event":"purchase","userId":"usr_001"}
```

Benefits:

- easy to append
- easier to stream
- can process line by line
- better for logs and pipelines

## Streaming Matters

Loading a giant JSON array fully into memory can be expensive. Streaming lets you process data incrementally instead of all at once.

## Practical Scale Tips

- compress large payloads during transport
- paginate API responses
- avoid deeply nested, repetitive shapes
- keep only the fields you need
- use JSONL for append-heavy pipelines

## Human Readability vs Machine Efficiency

JSON is readable, but not the most compact format. For some high-scale or binary-heavy systems, teams eventually adopt alternatives. Even then, JSON often remains the human-facing boundary format.

Here is a realistic `event-stream.jsonl` example:

```jsonl
{"id":"ev_1","type":"user_signup","timestamp":"2023-10-01T10:00:00Z","data":{"userId":"usr_123"}}
{"id":"ev_2","type":"page_view","timestamp":"2023-10-01T10:05:00Z","data":{"userId":"usr_123","path":"/pricing"}}
{"id":"ev_3","type":"subscription_created","timestamp":"2023-10-01T10:10:00Z","data":{"userId":"usr_123","plan":"pro"}}
```

Notice how each line is an independent, valid JSON object, making it trivial to append to the end of the file without rewriting the whole structure.

Next: [10 - Security and Reliability](./10-security-reliability.md)
