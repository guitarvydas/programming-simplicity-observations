

# Functional Programming - First Class Functions

## Takeaway - First Class Functions

## GOTO

First Class Functions are as powerful as GOTOs.

CPS - Continuation Passing Style - is like GOTOs on steroids.

GOTOs first appeared in Assembly language.

CPS was borne out of /CC functions in Scheme and functional thinking (i.e. an attempt to force-fit control flow into the functional paradigm).

## Utility

First Class functions & CPS are useful in Denotational Semantics (to express control-flow).

First class functions and CPS should *not* be used in lieue of more structured expressions of control flow.  

What are these more structured versions? The paper [GOTO Statement Considered Harmful](https://homepages.cwi.nl/~storm/teaching/reader/Dijkstra68.pdf) might provide clues.

FP usage of first class functions is Structured only because of the severe restrictions imposed by FP.  

FP uses a one-in, one-out[^exceptions] model of computing (aka "synchronous calculators").

[^exceptions]: Exceptions are warts - bags added onto the side of one-in/one-out syntax. Exception syntax is an attempt to push functional notation beyond its limits, and, to make stack-based operations "visible" (whereas, the original intent of functional notation is to hide the stack).

## Anonymous Functions

First class functions are data objects that contain functions.

First class functions have no names[^fpfcf1] and can be assigned (held in) variables.

[^fpfcf1]: First-class function are *anonymous*.

## Lambdas

Lambdas - first appeared in Lisp (approx. 1956) as a programming construct.

Lambdas are "anonymous functions".

## C's First-Class Functions

C has first-class functions, emodied as calls such as
```
(*f)(...);
```

## First-Class Functions in Assembler

Assembler provides first-class functions. 

For example, the address of a function can be held in a register, then called.

## Function Syntax 1D vs. 2D

Function Syntax was invented for *mathematics*.

*Mathematics* notation was invented for pencil-and-paper use (approximately 1D).

Computers allow us to use 2D, 3D, etc., for notations.


