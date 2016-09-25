# Property Based Testing
- Unit tests: Reason by example
- PBT: Reason by proof
- Generate -> Run -> Shrink

**Intuition**

1. Specify the behavior of a unit of code as a `Prop`
2. ScalaCheck generates test data to falsify the property until it is exhausted
3. If the property holds true for all such generated test data, then the `Prop` is assumed to pass the test

**Flow**

1. Create an instance of `org.scalacheck.Prop` say `p`
2. Test it by calling `check` function on it `p.check`

## Create
- Universally qunatified Prop can be created using `Prop.forAll`
- `forAll` takes function as the parameter
- The function takes any type as input parameter and returnes either a `Boolean` or another `Prop`
- **Combine** `Prop` using `all, &&, ||, atLeastOne, ==`
- Group related props by
  - Extending from `Properties`
  - Using `include`

## Generate
- `org.scalacheck.Gen`
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
  - Higher-order: `choose`, `oneOf`, `someOf`, `listOf1`
  - Distributions: Random, `Prop.frequency`
- `for` comprehension can be used to generate custom types
- `Arbitrary` is a canonical way of generating data for a specific type. There can be only one canonical generator for type in a given scope. See [this video](https://www.infoq.com/presentations/scalacheck-magic) from 41th to 44th min.
- `arbitrary` is a way to convert an `Arbitrary` into a Gen. See [this video](https://www.infoq.com/presentations/scalacheck-magic) from 43.30 to 44.10 min.

## Run
- 
- ScalaTest
- Specs2
- [ScalaMeter](https://scalameter.github.io/)
- [Simulant](https://github.com/Datomic/simulant/wiki)

## Shrink

```
scala> implicitly[Shrink[String]].shrink("asdf")
Stream[String] = Stream(as,?)
scala> implicitly[Shrink[String]].shrink("asdf").force
Stream[String] = Stream(as,df,adf,asd,sdf,asf)
scala> implicitly[Shrink[String]].shrink("as").force
Stream[String] = Stream(a,s) 
scala> implicitly[Shrink[String]].shrink("a").force
Stream[String] = Stream("") 
scala> implicitly[Shrink[String]].shrink("").force
Stream[String] = Stream()  
```

## Test Distribution
- Use `collect` and `classify` to examine the distribution of the generated test data
- We can nest both of them to get multi-level grouping

## Patterns
- Symmetry: There and back again ([Click for e.g.](http://blog.charleso.org/property-testing-preso/#71))
- Multiple paths:
- Induction
- Invariants ([Click for e.g.](http://blog.charleso.org/property-testing-preso/#73))
  - Idempotence
  - Consistency

## References
- [ScalaCheck Cookbook](https://github.com/oscarrenalias/scalacheck-cookbook/blob/master/markdown/TOC.md)
- [ScalaCheck Magic](https://www.infoq.com/presentations/scalacheck-magic)
- [Getting the most out of ScalaCheck](https://engineering.sharethrough.com/blog/2016/07/29/a-retrospective-on-scalacheck/)
- [Categories of Properties](https://fsharpforfunandprofit.com/posts/property-based-testing-2/)
- [Patterns](http://blog.charleso.org/property-testing-preso/#1)

##New Generators Project

- Names
  - [UK female dataset](https://www.ons.gov.uk/peoplepopulationandcommunity/birthsdeathsandmarriages/livebirths/datasets/babynamesenglandandwalesbabynamesstatisticsgirls) (Rank, Name Count)
  - UK male dataset