# Code Infrastructure

## Declaration Merging

Typescript can stack values, types, and classes and assign the same reference

How do I tell which is which?

Values can be to the right of the `=` operator, like so:

```ts
const Sandwich = {
  bread: 'wheat',
  topping: 'baloney'
}
const item = Sandwich //ok
const item: Sandwich = ... // NOT ok!
```

Types can be to the left of the `=` operator, like so:
```ts
type Sandwich = {
  bread: string,
  topping: string,
}
const item = Sandwich // NOT ok!
const item: Sandwich = ... // ok!
```

This collection of various entities (types) under one reference allowed for typing of legacy modules (like JQuery), and the third usage (namespace) is uncommon in modern JS -- in fact, it should generally be avoided.

# Modules and CJS interop

- `esModuleInterop` and `allowSyntheticDefaultImports` can be thought of as 'viral options'
- They can make things markedly easier, but at a cost
  - Much like type assertions, they bleed upwards through code
  - Causes anyone consuming code typed this way to use the same options and deal with the consequences
- Another solution:
  - Use non-ECMAScript import
  - e.g. `import createThing = require('./library')`
- Importing non-TS things:
  - e.g. `import img from './file.png`
  - You can create a `global.d.ts` file
    - Include a `declare module '*.png' { ... }` object with base defaults