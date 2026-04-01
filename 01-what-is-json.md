# 01 - What Is JSON

JSON stands for JavaScript Object Notation. The name comes from JavaScript, but JSON is used almost everywhere: browsers, servers, mobile apps, CLIs, configuration files, search engines, pipelines, and logs.

## Plain-English Definition

JSON is a text format for representing structured data.

Structured data means information that has a clear shape. For example:

```json
{
  "name": "Asha",
  "age": 19,
  "skills": ["HTML", "CSS", "JavaScript"]
}
```

This is not "just text" in the messy sense. It is text with rules:

- keys and string values use double quotes
- objects use `{ }`
- arrays use `[ ]`
- values are separated by commas

## Why JSON Matters

JSON is the meeting point between systems.

Examples:

- A frontend sends form data to a backend as JSON.
- A backend returns API responses as JSON.
- A deployment tool stores settings in JSON.
- An application emits logs or events in JSON.

Once you notice it, JSON is everywhere.

## What Makes JSON Popular

- Human-readable
- Easy for machines to parse
- Language-independent
- Good enough for many kinds of structured data

## What JSON Cannot Express Well

JSON is deliberately small. It does not have:

- comments
- functions
- dates as a built-in type
- `undefined`
- `NaN` or `Infinity` in standard JSON

If you need those ideas, you usually represent them another way, like:

- dates as ISO 8601 strings
- missing values as omitted fields or `null`
- special states as enums such as `"pending"` or `"failed"`

## JSON Text vs Runtime Objects

This distinction is important:

- JSON text is the string form stored in files or sent over the network.
- Runtime objects are what your programming language creates after parsing that text.

That is why people say things like "parse JSON" and "stringify JSON." They are converting between text and in-memory data.

## Common Places You Will See JSON

- API request and response bodies
- `package-lock.json` and similar tool files
- design tokens
- search documents
- feature flags
- webhook events
- configuration files

Next: [02 - Core Syntax](./02-core-syntax.md)
