# Lessons Learned

Compiling the following code

```scala
def fetch[T](jobId: String, contentType: ContentType)(implicit context: SparkContext, config: JobConfig) {
    val items: RDD[String] = context.textFile(config.readInputPath(contentType))
    null
  }
```
Will give the following warning

```
[WARNING] warning: a pure expression does nothing in statement position; you may be omitting necessary parentheses
[WARNING]     null
[WARNING]     ^
```
Value discarding: Making the return type as Unit means that, any value returned from the function is automatically discarded and a Unit is returned (Similar to void in Java)

```scala
def fetch[T](jobId: String, contentType: ContentType)(implicit context: SparkContext, config: JobConfig): Unit = {
    val items: RDD[String] = context.textFile(config.readInputPath(contentType))
  }
```

Reference
- [Value discarding section](https://dzone.com/articles/useful-scala-compiler-options-for-better-scala-dev)
- - [http://stackoverflow.com/questions/18368346/quite-confused-about-this-code-snippet-return-types-with-without](http://stackoverflow.com/questions/18368346/quite-confused-about-this-code-snippet-return-types-with-without)
- [http://stackoverflow.com/questions/23206201/scala-expression-evaluation](http://stackoverflow.com/questions/23206201/scala-expression-evaluation)

---



