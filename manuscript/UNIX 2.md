

# UNIX® 2

## Takeaway - Restricted Interface

- restricted interfaces
- low-level types for interfaces

## Restricted Interfaces

UNIX commands have

- 1 input (stdin)
- 2 outputs (stdout, stderr).

UNIX shows how much can be done with simple interfaces.

## Low-Level Types

Typing, in pipelines, is done in layers, not in an *all-in-one* basis.

UNIX commands use a very simple, low-level type for communication between components - a line of text terminated by a newline.

This simplicity allows components to be plugged together.[^u21]

[^u21]: I argue, elsewhere, that this is not simple enough.

Note that more elaborate types *can* be used, but the fundamental (atomic) type for *plugging* components together remains constant (a line of text).

More elaborate types can be enforced by components in UNIX® pipelines.

(See also, LEGO Takeaways).

UNIX® interfaces are all connected using *lines of characters terminated by a newline*.  Even this low-level "type" is too restrictive.  Parsers usually pattern-match across lines and can be used to lift the line-oriented restriction.

## Type Pipelines

More elaborate types can be checked in layers in a type pipeline.  Each successive component in a pipeline either 

1. passes data down the pipe (after checking it)
2. signals an error, e.g. by withholding (1) and sending an error object (/ message) on a side-channel.

This structure inherently needs multiple outputs e.g. at least stdout and stderr (I favor having more than 2 outputs) which is not well-served by functional notation (which is fundamentally a 1-in-1-out notation[^u211])

[^u211]: Over time, the limits of functional notation have been addressed by playing whack-a-mole - adding syntactic bags onto the side of the otherwise-pure syntax, e.g. exceptions.

## FBP

FBP means [Flow-Based Programming](https://en.wikipedia.org/wiki/Flow-based_programming).

UNIX commands are a subset of FBP[^u22].

[^u22]: I favor Event-Driven Component Based Programming, which is more similar to EE and LEGO.  FBP focuses on the flows of data while event-driven component-based programming focuses on the components themselves.

## Edge-Cases

Q: What kinds of operations cannot be handled with the above?

Q: Should we create PLs[^u23] that are the Union of all edge-cases, or, should we create many SCNs[^u24] instead?  

Q: Does PEG offer advantages over REGEX for creating commands (e.g. grep vs. fictional peggrep ; awk vs. fictional pegawk ; python vs. fictional pegpy ; lisp vs. peglisp)?  Is this an edge-case or something common to many apps?

Q: Should PLs be hierarchical, not flat?  Should variables be hierarchical?  [Example: "y = mx + b" vs. "y = (slope * x) + intersect".  Is the difference (e.g. using "m" instead of "slope") a language decision or a IDE feature?  Is this kind of maleability the goal of Projectional Editing?].  Functional thinking teaches us that variable names are frivolous (the extreme case being De Bruijn indices).  If names are frivolous, why do we support them?  Is this a language decision or an IDE decision?

[^u23]: PL means Programming Language.
[^u24]: SCN means Solution Centric Notation (essentially a light-weight DSL).

