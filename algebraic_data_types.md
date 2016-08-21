# Algebraic Data Types
- ADT's are only data. No behavior at all.
- 

## Enumerated Types

- All the possible values can be enumerated as there are only finite set of values. E.g. Seasons, Switches
- Case classes and objects are used to define these
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

## Sum Types

## Product Types

