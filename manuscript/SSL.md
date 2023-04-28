

# S/SL

## Main Takeaways

- dataless language (this is the hidden gem in S/SL), aka *mechanisms*.
- parsing primitive operations - a DSL for parsing
- input, output, error API functions are treated the same way

## S/SL

S/SL means Syntax Semantic Language.  (See References).

S/SL is a minimal syntax for parsing.  

Parsing has been subsumed by Parser Combinators and PEG.

Yet, S/SL still contains a hidden gem.

## Support Functions - Mechanisms

S/SL mechanisms are declarations of functionality.  Mechanisms declare the existence of functionality, but do not prescribe an implementation of such functionality.

For example, in most languages, we can add two integers together
```
1 + 2
```
but, in S/SL it is only possible to declare the existence of an addition operator, e.g.
```
mechanism Int:
    ...
    oAddIntegers
    ...
```

This appears to be overly-verbose, but it divorces existence (*declaration*) from implementation (*definition*). 

The view that this syntax is overly-verbose is based on considering only human-readable syntax, and accepts the idea that Architecture must be conflated with Implementation.  See *PEG* for possible solutions to the human-readabilty problem.  

The functions in S/SL mechanism declarations are declared (like *externs* or *enums*) and support  applications written in S/SL, but the mechanism functions are *not* implemented in S/SL.

Mechanisms are implemented in the base language (I call this a Toolbox Language).

S/SL usually rides on top of some base language, like C, Pascal, etc.

See also, S/SL's types, inputs, outputs and errors.  All of these are declared but not implemented in S/SL.

## Dataless Language

In S/SL, there is no data.

There are only *handles*[^ssl1] to data.

One can declare the existence of data and can move it around, but one cannot *specify* the implementation of the data in S/SL.

[^ssl1]: Handles are similar to the concept of *enums*.  We use *handles* when communicating with operating systems, for example, we can carry around pointers to window structures, but we can't look inside window structures.

## Typeless Language

S/SL has no built-in types[^ssl2].

In S/SL, you can declare *handles* to types, but you cannot specify *how* the types are implemented[^ssl3].

[^ssl3]: For example, you cannot specify the layout of data in S/SL, i.e. records and user-defined types are not defined in S/SL itself.

Compiler technology has improved to the point that such low-level implementation details do not need to leak out into the syntax of programming languages.

## Inputs

Inputs are declared as *handles*.

## Outputs

Outputs are declared as *handles*.

## Errors

Errors are declared as *handles*.

[^ssl2]: This is not entirely true, but is a useful approximation for this essay.

## Restricted API To/From Mechanism Functions

S/SL functions can take exactly 0 or 1 parameters.

S/SL functions can return exactly 0 or 1 return values.

## Datalessness In Other PLs

It is *possible* to create data handles when using other PLs, but most PLs tend to *encourage* description of the implementations.

For example, *int*, *float*, *array*, *list*, etc. declarations are examples of data implementations.

S/SL enforces non-implementation of details.

## Typelessness in Other PLs

It is *possible* to create hierarchies of abstract types when using other PLs, but this usually tends (psychologically) towards accidental complexity.

S/SL enforces the use of type handles.

## Input in Other PLs

S/SL's simple handles enforce simple description of inputs.

## Output in Other PLs

S/SL's simple handles enforce simple description of outputs.

## Error in Other PLs

S/SL's simple handles enforce simple description of errors.

Many current PLs implement error handling using `throw`, resulting in backtraces of uninteresting details (essentially the same as mid-1900's core dumps).

Error handles could be used to invoke `throw`, or, better, could be used to provide useful debugging error messages.

## Encouraging Behavior vs Enabling Behavior

There seems to be a fine line between PLs that encourage certain paradigms vs. making those behaviors possible.

For example, it is *possible* to write CPS in assembly code, but few programmers bother to do so.

Lifting concepts to make them visible, vs. eliding other concepts, is an important aspect of PL design.

## The Hidden Gem

S/SL's use of *handles* makes the Architectural concepts of a program visible, while eliding implementation.

S/SL's simplicity makes it possible to think about higher-level concepts.

S/SL's simplicity makes it easy to implement S/SL on top of existing languages (e.g. C, Python, etc.).

S/SL's simplicity encourages layered thinking.  Details are not discarded, only pushed down to lower levels.

S/SL's simplicity encourages layering.  Layering is possible in other languages, but is too often conflated with implementation details.  It is possible to build FP and OO in assembler, but programmers usually don't do this.  The details and bookeeping required to program in assembler tend to overwhelm programmers, making it difficult to follow FP and OO principles. 
