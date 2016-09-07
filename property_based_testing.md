# Property Based Testing
Generate -> Run -> Shrink

## Generate
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

## Run
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
