

# Relational Programming

## Main Takeaways

- triples
- exhaustive search
- separation of concerns: (1) syntax, separated from (2) engine
- separation of concerns
- Barliman

## Anti-Takeaways from Relational Programming

- functors with arity different from 2

## Triples

Triples are a grouping of `{Relation x Subject x Object}`.

In syntax-full languages, like Python, triples might be represented as:

`rel(s,o)`

In expression languages, like Lisp, triple might be represented as:

`(rel s o)`

In assembler, triple are represented as:

```
MOV R0,R1
```

### Curried Functions

Functionl thinking has shown that we can represent functions as functions of a single parameter, e.g.
`
(lambda (x) ...)
`

It *appears* that Curried functions are doubles, not triples.

If fact, Curried functions are triples-in-disguise.  The *relation* and the *subject* are grouped together, waiting[^rp1] for an *object* to satisfy the triple relationship.

[^rp1]: Satisfying a Curried function with an *object* is called *Apply*.

## Exhaustive Search

(see Pattern Matching)

## Separation of Concerns
- Relational Programming syntax is declarative
- In Relational Programming, the syntax states what is "true"[^rp2], possibly in terms of other relations, but does not state *how* to implement the operations (to evaluate the other relations).

[^rp2]: A Tautology


## Barliman

[Barliman presentation](https://www.youtube.com/watch?v=er*lLvkklsk)

Barliman is an example of what happens when the mind is freed of concerns for implementation and optimization.

Barliman is like TDD on steroids.

## See Also

[Factbases (aka Triples)](https://guitarvydas.github.io/2021/01/17/Factbases.html)
[Factbases 101](https://guitarvydas.github.io/2021/04/26/Factbases-101.html)
[Triples 2](https://guitarvydas.github.io/2021/03/16/Triples.html)
[Triples in PROLOG](https://guitarvydas.github.io/2021/11/06/Triples-in-PROLOG.html)
[PROLOG For Programmers](https://guitarvydas.github.io/2021/04/11/Playlists.html)
[miniKanren](http://minikanren.org)

  







