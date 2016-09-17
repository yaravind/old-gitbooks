
# Functions

* When we say functions are "first class", we mean they are just like everyone else...so normal classcoach?. We can treat functions like any other data type and there is nothing particularly special about them - store them in arrays, pass them around, assign them to variables, what have you.

## Higher Order Functions

Enable simple functions to be glued together to make more complex ones. Define a general higher-order function (`foldr`) and some particular specializing functions (`sum` etc.). 

Examples

- ```sum = foldr (+) 0```
- ```product = foldr (*) 1```
- ```anytrue = foldr or False```
- ```alltrue = foldr and True```
- ```length = foldr count 0 // where count a n = n + 1```
- ```map f = foldr (Cons .f) Nil```
- ```summatrix = sum . map sum```

## Pure Functions

[From Mostly Adequate Guide to FP](http://drboolean.gitbooks.io/mostly-adequate-guide/content/ch3.html)

* A pure function is a function that, given the same input, will always return the same output and does not have any observable side effect. 
* Depending on external state increases the cognitive load by introducing an external environment. Erlang creator, Joe Armstrong: "The problem with object-oriented languages is they’ve got all this implicit environment that they carry around with them. You wanted a banana but what you got was a gorilla holding the banana...and the entire jungle".
* The philosophy of functional programming postulates that side effects are a primary cause of incorrect behavior. It is not that we're forbidden to use them, rather we want to contain them and run them in a controlled way. We'll learn how to do this when we get to functors and monads in later chapters, but for now, let's try to keep these insidious functions separate from our pure ones.
* You can transform some impure functions into pure ones by delaying evaluation


### Memoization

* Pure functions can always be cached by input. This is typically done using a technique called memoization.

### Referential Transparency

* A spot of code is referentially transparent when it can be substituted for its evaluated value without changing the behavior of the program.

### Parallel Code

* Here's the coup de grace, we can run any pure function in parallel since it does not need access to shared memory and it cannot, by definition, have a race condition due to some side effect.
* Because we are not encoding order of evaluation (unlike in imperative coding), declarative coding lends itself to parallel computing. This coupled with pure functions is why FP is a good option for the parallel future - we don't really need to do anything special to achieve parallel/concurrent systems.

## Challenges

* We have to juggle data by passing arguments all over the place
* We're forbidden to use state, not to mention effects.

How does one go about writing these masochistic programs? **Currying is the answer.**



