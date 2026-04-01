# 05 - Working with JSON

Once you understand syntax, the next skill is moving JSON in and out of real programs.

## The Core Operations

- Parse: convert JSON text into runtime data
- Stringify or serialize: convert runtime data into JSON text
- Pretty-print: format JSON so humans can read it easily

## JavaScript Example

```js
const text = '{"name":"Asha","active":true}';
const data = JSON.parse(text);

console.log(data.name); // Asha

const output = JSON.stringify(data, null, 2);
console.log(output);
```

What the third argument to `JSON.stringify` does:

- `null` means "do not customize the replacer"
- `2` means "indent nested levels by 2 spaces"

## Python Example

```python
import json

text = '{"name":"Asha","active":true}'
data = json.loads(text)

print(data["name"])

output = json.dumps(data, indent=2)
print(output)
```

## Reading JSON From Files

At rest, JSON usually lives in `.json` files. In code, you typically:

1. read the file as text
2. parse it
3. use the resulting data structure

## Writing JSON To Files

When writing JSON, it helps to:

- pretty-print it for readability when humans edit it
- keep field names stable
- avoid accidental type changes

## Numbers Need Care

Large numbers can be tricky across languages and databases. Some runtimes lose integer precision beyond certain limits. If exact precision matters, use a clear strategy and document it.

## Dates Are Usually Strings

JSON has no built-in date type, so dates are commonly stored as ISO 8601 strings:

```json
{
  "createdAt": "2026-03-28T03:30:00Z"
}
```

## One Reliable Workflow

Parse -> validate -> normalize -> use -> serialize

That sequence reduces bugs. Parse gives structure. Validation checks rules. Normalization makes the data shape predictable before the rest of your application depends on it.

Next: [06 - JSON and APIs](./06-json-and-apis.md)
