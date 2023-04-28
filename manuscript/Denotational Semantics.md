
# Denotational Semantics

## Main Takeaways

- making all details explicit is the main takeaway from denotational semantics
- denotational semantics deals with data *and* control-flow (both are important)

## Anti-Takeaways

Describing everything in a flat manner[^dn1] leads to complexity.

[^dn1]: Denotational Semantics, often results in a big blob of "stuff" - lots of edge-cases and exceptions - lots of nuance (simplicity is the "lack of nuance").

This "all-in-one" approach leads to accidental complexity. E.G. CPS is useful in Denotational Semantics, but is horrible for maintenance of "normal" applications, i.e. applications that do not need to define new programming languages.

The "all-in-one" approach conflates issues, such as data contruction vs. control flow contruction.  Data construction, data flow and control flow are orthogonal concepts, but are often lumped together.  Control-flow construction tends to be lumped in with data construction and is, often, overlooked.

For example, OO attempts to describe data and control flow using the same construct - objects with inheritance. Control flow construction is more easily described by delegation and composition.  The effort to combine inheritance, delegation and composition into a single language (notation) often results in accidental complexity[^dn2].

[^dn2]: Simplicity is defined as "the lack of nuance".  When too many features are combined into a single language, nuance (the opposite of simplicity) is often the result.

## Denotational Semantics

Denotational Semantics is the description of all parts of a programming language in functional notation.  Data and control flow are described as parameters to functions.

An early form of this kind of thing can be found in [Anatomy of Lisp](https://www.amazon.ca/Anatomy-Lisp-John-Allen/dp/007001115X).

[Wikipedia article for Denotational Semantics](https://en.wikipedia.org/wiki/Denotational_semantics).

[Peter Lee](https://mitpress.mit.edu/books/realistic-compiler-generation) (and, later, Uwe Pleban) created practical versions of this technology.

## Control Flow

Control flow can be described using Continuation-Passing-Style - CPS.

Control flow can, also, be described using Statecharts.

Description of control-flow as an explicit construct is not exclusive to functional programming nor to denotational semantics.

[*IMO Statecharts represent control flow better (easier to reason about) than does CPS.*]

Most General-purpose Programming Languages tend to focus on the description of data,  and tend to leave the description of control flow to "syntax".  Data and control flow are described, typically, in two different ways.

## Making Everything Explicit

Denotational Semantics creates environments explicitly, e.g. using data structures.

Denotational Semantics describes entry- and exit-points of programmng constructs as first-class entities, e.g. using a data structure.

See Data Descriptors and Condition Descriptors for early attempts at describing such concepts.

Diagrams can, also, describe data and operations explicitly.  In some cases, diagrams are more expressive than textual denotations.

Programming languages hide ("abstract") various details under-the-hood to enact certain notations / paradigms.  

Many languages hide details such as the Stack and asynchrony.

Denotational Semantics makes all of these details visible and explicit.

I feel that it is useful to be reminded of what the hidden details are and to know what the abstractions are eliding (hiding).  For example, programmers tend to forget that the Stack is abstracted and hidden from view.  Programmers, also, tend to forget that *synchrony* is a *tactic* and that the inherent concurrency of computers is most often hidden by the abstraction of synchrony.  

Not *all* abstractions are suitable for *all* purposes.  For example, servers are inherently asynchronous, but, the tactic of using synchronous abstraction interferes with the programming of such asynchronous devices, e.g. JavaScript *callbacks* were intended for synchronous description of asynchronous procedures.  Callbacks were later found to cause programming problems.

## Gotchas

The description of programming languages in functional form implies that the languages-being-described are generally sequential and synchronous.  Concurrency *can* be described in functional form, but, such descriptions tend to be uneccessarily complicated.

Since our notations and beliefs impact our thoughts, we tend to stick to designing languages that are text-based and line-oriented (and based only on non-overlapping grids of bitmaps that we call "characters").

We imagine that diagrams must be drawn *from* text instead of producing languages based on diagrammatic syntax (that may include text).  Few popular VPLs (Visual Programming Languages) exist.  Our reliance on text biases us into not imagining programming languages that straddle the gap between text and VPLs.

## See Also

Cordy's [Orthogonal Code Generation](https://books.google.ca/books?id=X0OaMQEACAAJ&dq=bibliogroup:%22University+of+Toronto+Computer+Systems+Research+Institute+Technical+Report+CSRI%22&hl=en&sa=X&ved=2ahUKEwig1Legm8bqAhWvlHIEHYzzBYEQ6AEwBHoECAEQAQs)  describes *condition descriptors* which are, basically, records with two fields (continuations) which describe the *true* and *false* branches of branching code.  Condition descriptors can be combined with other condition descriptors, in a manner similar to [De Morgan's Laws](https://en.wikipedia.org/wiki/De*Morgan's*laws), to form branching code[^dnbc]

[^dnbc]: Branching code is code that does not cause all branches/arguments to be evaluated, unless necessary.

[StateCharts](https://guitarvydas.github.io/2020/12/09/StateCharts.html)
[StateCharts Again](https://guitarvydas.github.io/2021/02/25/statecharts-(again).html)
[StateCharts - Harel's Paper](https://www.inf.ed.ac.uk/teaching/courses/seoc/2005_2006/resources/statecharts.pdf))

 





