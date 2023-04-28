# Compiler Technology (1)

## Takeaway - Parsing

Parsing is better than REGEX.

Ohm-JS is better than *parser combinators*.

## Parsing

Parsing technology (PEG, YACC, etc.) can (easily) match across lines.

Parser specifications can include parsing subroutines.

Parser specifications usually span multiple lines.

The unit of matching in parsers is a block of structured text (possibly spanning many lines).

## REGEX

REGEX is a DSL for matching patterns *within* lines.

The unit of matching in REGEX is a *line*.

REGEX does not supply subroutines at the DSL level.

REGEX specifications are usually a single line in length (or less).

## Flexibility

Parsers are more flexible than REGEX, but parsers usually require multiple-line specifications whereas REGEX uses single-line specifications.

## PEG (Ohm-JS)

PEG is a relatively recent addition to parsing technologies.

PEG libraries are available for many languages.

IMO, Ohm-JS is the best variant of PEG, since Ohm obeys the principle of *separation of concerns*.  In Ohm, grammars and action code (aka semantics) are kept separated from one another.

## Command Line Tool (to augment GREP)

GREP is a early tool that uses REGEX technology.  It is found in UNIX® and Linux systems.

IMO, there should be a GREP-like tool that uses PEG technology instead of REGEX technology.

I've build a POC[^poc] of such a tool and call it `prep`.

[^poc]: Proof of Concept

## PREP

`Prep` is a tool that performs parsing *find-and-replace*:

`prep begin-regex end-regex pattern-specification string-rewrite-specification <input-file`

See the References section for a prototype for *prep, based on Ohm-JS.

## Parsing Combinators

Parsing Combinators force-fit parsing onto GPLs.

Good parser generators are better than combinators, because parser generators perform only one task (well) instead of being force-fitted into GPLs.

## State Machines or Recursive Descent

REGEX is usually compiled into a state machine.

Parsers are compiled into state machines or sets of mutually recursive routines (recursive descent).

S/SL is an early technology that compiles parsers to top-down (recursive descent) routines.

YACC is an early technology that compiles to bottom-up state machines.

YACC (LR(k)) parsers specify languages.

TDPL[^tdpl] parsers, like PEG, specify parsers.

[^tdpl]: TDPL mean Top-Down Parsing Language.

Language specification tools are harder to use, IMO, than parser building tools.

## See Also

REGEX and YACC (LR(k)) technologies are described in the [Dragon Book](https://en.wikipedia.org/wiki/Compilers:*Principles,*Techniques,*and*Tools).

Ohm (and Ohm-JS) are described in [Ohm](https://ohmlang.github.io).

PEG is described in [Bryan Ford's PEG paper](https://bford.info/pub/lang/peg/).  Further information about [PEG and packrat Parsing](https://bford.info/packrat/).

[S/SL Report](https://archive.org/details/technicalreportc118univ) and [S/SL Source Code](https://research.cs.queensu.ca/home/cordy/pub/downloads/ssl/)

[Prep](https://github.com/guitarvydas/prep/blob/master/README.md)


