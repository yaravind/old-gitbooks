Functional Programming Notes
=======

This is a collection of my notes and references to articles and books on functional programming. Examples and links are specific to Scala most of the time.

Why FP matters?
--------
When writing programs in a modular way, we divide a problem into sub-problems, solve them separately, and glue them together to form a solution. The ways we divide the problem directly depends upon the ways we can glue them together. Therefore, to increase one's ability to modularize a problem conceptually, one must provide new kinds of glues in the programming language. FP languages provide two new, very important kind of glue: **Higher-order functions** and **Lazy evaluation**.

**Higher-order functions** enable simple functions to be glued together to make more complex ones. Define a general higher-order function (`foldr`) and some particular specializing functions (`sum` etc.). 

Examples

- sum = foldr (+) 0
- product = foldr (*) 1
- anytrue = foldr or False
- alltrue = foldr and True
- length = foldr count 0 // where count a n = n + 1
- map f = foldr (Cons .f) Nil
- summatrix = sum . map sum

**Lazy evaluation** makes it practical to modularize a program as a **generator** that constructs a large number of possible answers, and a **selector** that chooses the appropriate one. Without lazy evaluation this would not always be practical (or even possible, in the case of infinite generators).

Reference
- https://www.cs.kent.ac.uk/people/staff/dat/miranda/whyfp90.pdf
- [foldl.com](http://foldl.com/) and [foldr.com](http://foldr.com/)
