

# Pattern Matching

## Main Takeaway

- Exhaustive Search

## Exhaustive Search

Many programming tasks consist of searching through information.

The ultimate search is an exhaustive search.

Non-exhaustive searches often suffer from premature optimization.  Non-exhaustive searches are often hand-coded as *loops* which miss certain edge-conditions.  In some cases, ignoring certain edge-conditions can be considered an optimization, in other cases ignoring certain edge-conditions can be considered as an oversight, which leads to future epicycles and accidental complexity.

PROLOG showed that it is possible to make exhaustive search the default mode of operation and to add operators (e.g. *cut*) to optimize searches when necessary.

Further analysis showed that *cut* should not be a default operation, since it causes twisting of the underlying semantics and leads to accidental complexity.  This is a *tell* that *cut* should be used for optimization only and that it should be used with care.

## See Also

- [PEG](https://bford.info/packrat/)
- [PROLOG](https://www.swi-prolog.org)
- [miniKanren](http://minikanren.org)
- [Ohm](https://ohmlang.github.io)
- [Ohm-JS](https://github.com/harc/ohm)
- REGEXP is an example of a search DSL that hides the underlying matching-engine
- Parsing











