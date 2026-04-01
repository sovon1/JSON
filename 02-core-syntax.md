# 02 - Core Syntax

JSON looks simple because it is small. That is a strength. The entire format is built from a few building blocks.

## The Six Value Types

JSON values can be:

1. Object
2. Array
3. String
4. Number
5. Boolean
6. `null`

## Objects

An object is a collection of key-value pairs.

```json
{
  "name": "Asha",
  "age": 19,
  "active": true
}
```

Rules:

- Objects start with `{` and end with `}`.
- Keys must be strings.
- Each key is followed by `:`.
- Pairs are separated by commas.

## Arrays

An array is an ordered list of values.

```json
[
  "HTML",
  "CSS",
  "JavaScript"
]
```

Arrays can contain mixed types, but mixing types carelessly often creates confusing data models.

## Strings

Strings are text values wrapped in double quotes.

```json
"hello"
```

Important:

- JSON uses double quotes for strings.
- Single quotes are not valid in standard JSON.

## Numbers

JSON numbers do not use quotes.

```json
42
3.14
-7
```

Avoid storing numeric data as strings unless there is a reason, such as preserving formatting for phone numbers or IDs.

## Booleans

Booleans represent true or false.

```json
true
false
```

They are not strings. `"true"` is text. `true` is a boolean.

## Null

`null` means an explicit empty or absent value.

```json
{
  "middleName": null
}
```

This is different from a missing field. Whether to use `null` or omit the key is a design decision.

## Nested Structures

JSON becomes powerful when you combine objects and arrays.

```json
{
  "user": {
    "name": "Asha",
    "roles": ["student", "builder"]
  }
}
```

## Whitespace

Spaces and line breaks are allowed between tokens. They help humans read JSON, but they do not change meaning.

## One Tiny Rule Set, Many Systems

Nearly every JSON file you will ever read is made from the same few pieces. If you learn them well, the rest of the repository becomes easier.

Next: [03 - Data Model](./03-data-model.md)
