# Coding by Composition

## Associative Property

When compositing functions, by math, the composition must satisfy associative property, meaning it doesn't matter how you group two of them. So, should we choose to uppercase the string, we can write:

```
compose(toUpperCase, compose(head, reverse));

// or
compose(compose(toUpperCase, head), reverse);
```