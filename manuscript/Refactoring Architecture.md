

# Refactoring - Architecture

## Main Takeaway
- refactoring of architecture

## Anti-Takeaway

- refactoring code

## Refactoring

The ultimate goal is to refactor *architecture*.

Refactoring *code* is merely a low-level subset of refactoring *architecture*.

## One Line Of Code

The ultimate goal is to write a full application in one line of code[^apl].

The goal of Software Architecture is to enable lots of thinking with very little coding.

## Refactoring is a Tell 

The need to refactor is a *tell* that something is wrong.

Refactoring usually means that the paradigm being used does not suit the problem-at-hand. 

## Locality

*Locality* is the issue of attempting to "keep like things together"[^ra1].

[^ra1]: Aside.  It is not possible to keep *all* like things together along many dimensions.  The best that can be done is to pick-and-choose the best notation for any one sub-problem in one dimension, then have the machine join sub-notations and manipulate them producing a complete program.  Mathematics works like this, also, except that - until recently - manipulations were done manually without machines. Mathematical notation was designed to allow manipulation using pen-and-paper. 

*Locality* was used as a solution to the "global variable" problem.  The issue was "solved" be creating local scopes for variables.  This kept all of the variables in the programmers' *view* (an eye-full, an editing window, a computer screen).  Global variables were not much of a problem in early BASIC programs, because the programs were typically short and all of the details were visible at-a-glance.

*Locality* was used in *structured programming*.  Code was constrained to use only *structured* concepts.  This alleviated the problem of wide-ranging GOTOs and kept most logic visible at-a-glance.

*Locality* is implicitly used in forming subroutines (functions).  Creation of subroutines eliminated most long runs of code - keeping all logic visible-at-a-glance.

OOP takes the idea of locality to a higher level (keeping all operations and data together.) 

*Refactoring* is a *tell* that *locality* has been violated.



[^apl]: I came close to describing a complete solution in one line of code in APL, but that was one very complicated line of code.  Simplicity is more important than complexity.











