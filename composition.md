# Coding by Composition

Composition will be our tool for constructing programs and, as luck would have it, is backed by a powerful theory that ensures things will work out for us. Let's examine this theory.

## Associative Property

When compositing functions, by math, the composition must satisfy associative property, meaning it doesn't matter how you group two of them. So, should we choose to uppercase the string, we can write:

```
compose(toUpperCase, compose(head, reverse));

// or
compose(compose(toUpperCase, head), reverse);
```

## Pointfree coding

http://drboolean.gitbooks.io/mostly-adequate-guide/content/ch5.html

## Debugging

http://drboolean.gitbooks.io/mostly-adequate-guide/content/ch5.html