# Conditional Types!

### Type queries!

- `keyof`
  - Used to get a union of all keys of an object type
  - To get all `string` keys, use intersection type, like so:
    - `type DatePropertyNames = keyof Date`
    - `type DateStringPropertyNames = keyof DatePropNames & string`
- `typeof`
  - Used to extract a type from a value, like so:

```ts
const band = {
  singer: 'Mick',
  guitarist: 'Keith',
  drummer: 'Charlie',
}
// this:
type Band = typeof band
// is equivalent to:
type Band = {
  singer: string,
  guitarist: string,
  drummer: string,
}
```

### Conditional Types:

Use ternary syntax, very similar the one used for values
  
```ts
class Grill {
  ...grillThings
}

class Oven {
  ...ovenThings,
}

type CookingDevice<T> = T extends "grill"
  ? Grill
  : Oven

type CookingDevice<"grill"> // Evaluates to `Grill` type
type CookingDevice<"oven"> // Evaluates to `Oven` type
```