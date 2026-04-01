# 00 - Start Here

If JSON feels mysterious right now, that is completely normal. The fastest way to remove the mystery is to hold one clear idea in your head:

> JSON is plain text used to describe data in a strict, predictable way.

That sentence is enough to begin.

## What JSON Is Not

- It is not a programming language.
- It is not something you "run" like an app.
- It is not JavaScript code, even though it looks similar.

## The Beginner Mental Model

Imagine you have a box with labeled slots:

- `name` -> `"Asha"`
- `age` -> `19`
- `isStudent` -> `true`

JSON is just a text-based way to write that box down so computers can exchange it without guessing.

## What You Need To Learn First

Before anything advanced, you only need to understand:

1. Objects: collections of named values
2. Arrays: ordered lists of values
3. Primitive values: strings, numbers, booleans, and `null`
4. Valid syntax: quotes, commas, braces, and brackets in the right places

## How To Use This Repository

Follow this order if you are completely new:

1. Read [What Is JSON](./01-what-is-json.md)
2. Read [Core Syntax](./02-core-syntax.md)
3. Examine this basic JSON profile:
   ```json
   {
     "name": "Asha",
     "age": 19,
     "isStudent": true
   }
   ```
4. Read [Valid vs Invalid JSON](./04-valid-vs-invalid.md)
5. **Knowledge Check:** Can you spot the error in `{ name: "Asha" }`? (Answer: Keys must have double quotes!)

## The Right Way To Practice

Do not try to memorize random snippets. Instead:

- Look at a JSON file.
- Say what the shape means in plain English.
- Notice whether each piece is an object, array, or primitive value.
- Rewrite a tiny version yourself.

That habit will make the advanced lessons much easier later.

## The Big Promise

By the end of this repository, you should be able to:

- Read JSON quickly
- Write valid JSON confidently
- Design cleaner data shapes
- Validate and evolve JSON contracts
- Recognize production risks before they bite you

Next: [01 - What Is JSON](./01-what-is-json.md)
