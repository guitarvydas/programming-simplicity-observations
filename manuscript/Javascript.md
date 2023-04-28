# Javascript

## Main Takeaways

- Javascript popularized / normalized the concept of programming GUIs
- Javascript popularized a fundamental paradigm - prototypes (instead of classes)

## Anti-Takeaways from Javascript

- not counting function parameters
- callbacks

## Prototypes

Prototypes first, formally appeared in Self.

Prototypes are the dynamic version of classes.

Classes are compile-time checkable, whereas prototypes can be only be fully checked at runtime.

It is important to understand the full underlying  paradigm first.  Classes are an optimization of prototypes.  Classes allow checking to be done at compile time.  Sometimes, inventing the compile-time version of something becomes an exercise in premature optimization.  Common Lisp improved the concept of classes by undoing some of the premature optimizations found in earlier class-based languages.  

JavaScript was invented after Common Lisp was invented. JS first implemented prototypal inheritance.  Classes were implemented in JavaScript using the pre-exising protype system.  Going from a prototype-based inheritance system to a class-based system was possible, whereas going in the other direction would require fundamental redefinition of the language.

## Counting Parameters

It is easy - and useful - for a language to count and check parameters to functions.

This check falls into the same class of error checks, as syntax checking for simple things like `end if`.

Counting parameters is easy to do and is "one of those things" that detects a lot of blunders (bugs) at compile time.

JS does not perform this kind of simple checking resulting in an increase in "puzzling" bugs and resulting in the popularity of TypeScript and other languages.

Simple error checks are desired in human-readable languages, but are not required in machine-readable languages (like assembler).

## HTML + JavaScript - GUI Programming

HTML was intended to be a declarative syntax for describing the appearance of GUIs (the browser).

This was found to be insufficient.  JavaScript was invented to augment HTML.  Javascript became very popular.

Many libraries, in many languages, transpile programs into JavaScript.

HTML+JavaScript has become the defacto method for programming GUIs.

## See Also

[Self](https://en.wikipedia.org/wiki/Self_(programming_language))