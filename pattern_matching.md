# Pattern Matching
- Guard conditions can be used to avoid nested pattern-matching
- [Pattern matching or OOP polymorphism?](https://youtu.be/S60PiAw-Tg4?list=PLO9y7hOkmmSEmDcxBXvIDp-1b5EIC5Ed5&t=867)
  - Use polymorphism when 
    - new sub-types are expected to be added in future. This way, the implementation of the method is localized to the new type
  - Use pattern matching when
    - new methods are expected to be added to existing types. This way, we no need to touch multiple classes
    - the behavior is spanning multiple types
- apply, applySeq

