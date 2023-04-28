# Structured Programming

## Main Takeaway

- Nesting (aka Scoping).

## Nesting / Scoping

Scoping is nesting.

Structured Programming suggested ways to scope *control flow* using constructs such as `while` and `if then else`.

Control flow spaghetti was discarded in lieue of structured control-flow concepts such as `while loops`.

[N.B. The problem of Global Variables was, also, solved by using nesting (scoping), although this was not fundamentally a control-flow problem]

## Q: What Could Be Further Nested In Today's PLs?

- functions
- types
- CPS
- environments
- ...

## Package Managers

Packaging, package managers, are attempts at providing nesting for symbols.

The fact that there is more than one kind of package manager implies that the concept has not been normalized, yet.

## Docker

Docker is an attempt at providing nesting and isolation.

## Environment Variables

Environment variables are global variables.  

## Environments

The name, *environment*, is used in Denotational Semantics and language building.

In such cases, *environment* means an object that contains all of the "stuff" needed for a routine to execute.

Language builders need to deal with *environment* objects explicitly but tend to elide such details in the final UX (the language).

For example, in a typical compiler that transforms HLL to machine code, the *environment* contains details such as the parameters, the return address, etc.

In Denotational Semantics, *everything* is made explicit. Such details are passed as arguments to functions in denotational descriptions. Denotational Semantics is an attempt to abstract low-level details (such as labels and branches) using functional notation (such as CPS, which boils down to GOTOs).

## The Takeaway

The main takeaway from *structured programming* is that *control flow* can be nested and can lead to more readable code.

Note that "more readable" means "no surprises" and that the human reader can comprehend all dependencies easily.

Note that *structured programming* is not as necessary if the human reader can comprehend all dependencies in the code without further refactoring.  This is the case when the code is short (about 5-ish lines in length) and when all of the code fits in one eye-full, e.g. on one screen or in one window.  Early programs did not need structuring and refactoring, since the programs were short and understandable.  *Structured Programming* became an issue when programs grew in size.



