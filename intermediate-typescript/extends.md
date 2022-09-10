# Typescript's `extends` keyword

Extends is one of the tricker pieces of TypeScript syntax.

The sentence that I find snaps things best into place for me is:

```
The `extends` keyword means 'meets or exceeds the constraints of'.
```

Here are a couple of example thought-frames that help keep my understanding snapped in:

A restaurant model:
```ts
type Restaurant = { 
  ...allRestaurantThings // i.e. 'menu', 
}
type Dominos extends Restaurant = {
  ...allRestaurantThings,
  ...allDominosThings
}
type LocalDominos extends Dominos = { 
  ...allRestaurantThings,
  ...allDominosThings,
  ...localDominosOnlyThings 
}
```

A movie model:
```ts
type Movie = { 
  ...allMoveThings, // e.g. 'director', 'budget'
}
type ActionMovie extends Movie = {
  ...allMovieThings,
  ...actionMoveThings // e.g. 'stuntDirector', 'explosivesSpecialist'
}
type BatmanMovie extends ActionMovie = {
  ...allMovieThings,
  ...actionMovieThings,
  ...batmanOnlyThings // e.g. 'hasPenguin', 'alfredActor', etc.
}
```

Any type `A` that has all the characteristics and restraints of a type `B` can be said to `extend` that type.