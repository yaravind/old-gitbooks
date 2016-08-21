# Algebraic Data Types
- ADT's are only data. No behavior at all.
- 

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


## Product Types

