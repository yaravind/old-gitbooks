# Property Based Testing
Generate -> Run -> Shrink

## Generators
- Can generate **any** value for a type or a **subset** of values
- Are a Monad so we can sequence/chain them to produce new ones
- Composable: `map`, `flatMap`, `filter`, `suchThat`
  - Using `suchThat` means ScalaCheck treats filtered values as *discarded*
- Are edge-case biased
- ScalaCheck has generators for
  - Primitives
  - `Throwable`, `Date`
  - `Option`, `Either`, `Tuple1` to `Tuple9`, `Function1` to `Function5`
  - Collections: `Array`, `List`, `ArrayList`, `Map`, `Stream`, `Set`
  - Helpers: `alphaChar`, `alphaNumChar`, `alphaStr`, `identifier` etc.
  - choose, oneOf, someOf
- `for` comprehension can be used to generate custom types

