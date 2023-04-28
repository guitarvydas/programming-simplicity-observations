# Writing Less Code

## Main Takeaway

- Less code leaves more time for thinking (aka Architecting)

## Anti-Takeaways from Writing Less Code

- Striving to write less code can result in write-only code.

## More Time for Thinking

A goal of architecting languages is to write very little code and to spend most of the time thinking about and solving the problem-at-hand.

## Flexibility

Ideally, a system can be architected with so few lines of code that the designer/programmer has no compunction about throwing all of the code away and starting afresh when new architectural discoveries are made about the problem space[^wlc2].

[^wlc2]: The belief that code will never be thrown away - that code is precious - is an insidious form of Waterfall thinking.

The code written must be so flexible as to allow rearranging of the architecture with little effort.  

Most GPLs discourage this kind of flexibility while encouraging expression of details (which leads to inflexibility[^wlc1]).

## Write-only Code

### APL

The shortest - in lines of code - significant program that I wrote was in APL.

That version of APL had a single purpose - manipulating matrices - but the code was forced to deal with design issues beyond manipulation of matrices e.g. string manipulation (strings are not matrices).

I wrote 2 lines of APL code and wrote about 80 lines of English comments.

I felt that the code was write-only and that English comments were needed to make the code and architecture readable by other programmers.

### Terseness

There is a saw-off point where the code becomes so terse as to be write-only in nature.

In the APL code I wrote, every character, in the lines of code, performed significantly large operations.

The final design was less understandable because matrix operations were used to manipulate non-matrix entities.

[^wlc1]: For example, flexibility requires that *no* functions be called directly by name - all functions should be called through indirection. DLLs provide a degree of indirection, but DLLs discourage full flexibility by retaining function names.

### How to Write Less Code

- Lisp is one way to write *less* code.
- Diagrams are a way to write *less* code while maintaining clarity of design.













