# Functional Programming - Explicitness

## Takeaway - Explicitness

Functional programming, in particular Denotational Semantics, attempts to make *everything* explicit.

In functional programming notation, we use function parameters to lasso every aspect of a program.

Explicitness is not unique to functional notation, for example, it is possible to draw all parameters on a diagram using arrows to join parameters together.

A computer consists of two main parts
- data
- CPU (control flow, the "soul").

Ironically, FP tends to ignore the CPU part.  Most functions deal with data, but often ignore control flow.  

Denotational Semantics is the method of using functions to describe control flow, in addition to data flow.

Most programmers find that Denotational Semantics is too difficult to reason with and understand and use.

This a *tell* that the notation is unsuited for the given purpose (e.g. describing sequencers) and is being stretched beyond its limits.  The solution to this problem is "obvious" - use a different notation - "divide and conquer".
