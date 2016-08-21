# Algebraic Data Types
- ADT's are only data. No behavior at all.
- In Scala, when we hear ADT, it means Sum Type.
- ADT's doesn't feature sub-type polymorphism, but only *combination/composition* of data types.

## Enumerated Types

- All the possible values are enumerated as there are finite set of values. E.g. Seasons, Switches
- `case` *classes* and *objects* are used to define enumerated type
- When defining an ADT, we need to
  - First define the type
  - Second define the domain of the type i.e. all possible values of that type. These valuses are called *value constructors*.
- Example

```scala
//Intoruduce the type
sealed abstract class Season

//Define value constructors
case object Summer extends Season
case object Winter extends Season
case object Fall extends Season
case object Spring extends Season
```
- Pattern matching simplifies the way we work with enumerated types
- It is not always possible to enumerate all possible values of a type, for e.g. `Color`. This is where the sum and product types are helpful.

## Sum Types

- **This or That**
- All the values of a sum type are clearly expressed as a sum of all of its value constructors.
- Sum types provide individual value constructors for each and every value of that type.
- In Scala, Sum Types are encoded by subclassing
-  Examples: Season, Boolean

## Product Types

- **This and That**
- Sometime we can't enumerate all values of a particular type. For e.g. it is not worth to enumerate all possible colors.
- Example

```scala
sealed case class RGBColor(red:Int, blue:Int, green:Int)
```

## "Sum of Product" Types

- Combination of sum and product types
- Mostly have nested definitions

## Recursive Types

- TBD: http://tpolecat.github.io/presentations/cofree/slides

## Standard Library

| Intuition | Type | Value Constructors |
| -- | -- | -- |
| Computations that may fail to return a value | `Option` | `None`, `Some` |
| Computations that may return this or that | `Either` | `Left`, `Right` |
| Computations that may fail with an Exception | `Try` | `Success`, `Failure` |
| Computations that may return many answers | `List` | `Nil`, `::` |


## References

- http://tpolecat.github.io/presentations/algebraic_types.html
- https://gleichmann.wordpress.com/2011/01/30/functional-scala-algebraic-datatypes-enumerated-types/
- https://gleichmann.wordpress.com/2011/02/05/functional-scala-algebraic-datatypes-sum-and-product-types/
- https://gleichmann.wordpress.com/2011/02/08/functional-scala-algebraic-datatypes-sum-of-products-types/