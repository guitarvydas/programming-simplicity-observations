

# Waterfall Design

## Main Takeaway

- The happy path.

## Anti-Takeaways from Waterfall Design

- Other paths are ignored and/or treated as second class issues.
- Waterfall Thinking is more prevalent than believed.

## Happy Path

The Happy Path is the path through code when "everything goes right".

## Other Paths

Software must deal with other paths through code - paths to execute when something fails.

Other paths are important in distributed code, e.g. internet. 

Connections might fail.

Connections might time out due to other reasons, e.g. taking too long to respond.

Such conditions are not actually *failure* - they are part of the problem-at-hand.

## Second Class Paths

Most current PLs make it easy to write code for the happy path.

Most current PLs address programming for other paths as second class issues, e.g. by providing syntactical warts, like exceptions.

## Waterfall Thinking

Thinking and coding *only* for the happy path is Waterfall Design.

## StateCharts

StateCharts address, both, happy paths and other paths in the same way, using the same programming syntax and contstructs.

## Functions

Functional notation is unbalanced when used as an *all-in-one* programming notation.

With functions, the happy Path is first-class, and other paths are considered to be secondary.

Functions address only the happy path - e.g. the workflow is input -> process -> then return a value. 

Exceptions in functional languages use a different syntax and follow a different dynamic call chain than the happy path, making such paths harder to reason about.

## Send ()

`Send ()` moves data between components.  The concepts of `parameter` and `return` are subsumed by `Send ()`.

`Send ()` does not differentiate between the happy path and other paths.

The syntax is the same for happy path and other paths.

The Architect can design code for multiple paths without resorting to syntactic ornaments.

## Drakon

[Drakon](http://drakon-editor.sourceforge.net/) treats other paths as first class citizens.

The Drakon tutorials are very good introductions to happy+other path notation:

- [Part 1](https://drakonhub.com/files/drakon*part1*eng.pdf)
- [Part 2](https://drakonhub.com/files/drakon*part2*eng.pdf)
- [Part 3](https://drakonhub.com/files/drakon*part3*eng.pdf)

I favor `Event Driven Component Based Programming` and consider Drakon to be a subset of CBP (Drakon would be a good way to implement leaf components).

## Concurrency

It is difficult to implement non-happy-paths using synchronous, non-concurrent code.

It is easier to implement other paths (and the happy path) in the concurrent paradigm. Aynchronous code and parallel code is easier to design in the concurrent paradigm[^wf1].

[^wf1]: It is possible to write asynchronous and parallel code in the synchronous paradigm, but, it is not as easy as writing such code in the concurrent paradigm.

Most current PLs treat asynchrony as a second class paradigm.

It is straight-forward to *simulate* concurrency using synchronous operating systems (See [CALL/RETURN Spaghetti](https://guitarvydas.github.io/2020/12/09/CALL-RETURN-Spaghetti.html))  [*Note that multitasking and threading are, also, merely simulations of concurrency*.]

## Tell: Backtraces

Backtraces are a *tell* that indicates happy-path-only thinking.

Backtraces are poor debugging tools[^wf2], but, one backtrace is not enough for debugging concurrent applications.

[^wf2]: No better than core dumps of the mid-1900's.

The fact that a language provides a single backtrace mechanism shows that the desiger(s) was not thinking about concurrency and was inventing a programming language for the happy-path-only paradigm.

Designing for the the happy-path-only paradigm is often a result of Waterfall thinking.

Waterfall thinking is the idea that programs will not fail and only need to address the happy path.

## Tell: Poor Error Messages

Poor error messages are a *tell* that happy-path-only thinking has been used in the design. Error handling is avoided and relegated to second class status.

Elm claims to have good error messages.

Compiler research developed error handling in the mid-1900's.

For example, you do not expect a compiler to produce multi-line warnings, multi-line error messages and to stop after the first error.  

C produced reasonable error messages.  SBCL does not produce reasonable error messages[^wf3]. JavaScript programs avoid the issue of errors and simply don't check for many classes of problems, relying on *throw*.

[^wf3]: SBCL gives *too many* error messages for any one mistake, making those error messages essentially useless for debugging.

Early Lisps included experimental constructs for handling warnings and errors, e.g. restarts.  Lisp suffered a dimunition of deubgging and rapid prototyping abilities when CL was standardized,  wherein compilatility was emphasized in lieue of design-turnaround.

## FP - Functional Programming

Using FP, one is encouraged to deal with the happy path and to relegate other paths - exceptions and errors - to second class status.

This is not surprising, since FP is based on functions, see above.

## FP Encourages Waterfall Design

Functional programming, where code is written for the happy path and all other paths are relegated to *exception handling*, encourages an insidious form of Waterfall Design.

In this mode of thinking, programmers are encouraged (by the Programming Language) to deal with only one path through the program and to "predict" - before-hand - how the system will behave.

*Prediction of behaviour* is a fundamental aspect of Waterfall Design.

A *tell* for this kind of thinking is the fact that many sofware systems are becoming more fragile.  

GUIs (for example `Typora` and `draw.io`) rely on layout algorithms that work well only on the happy path, but behave in strange ways for other paths, including interactive situations.

A tight lattice of mathematical reasoning breaks when any of its underlying assumptions are violated.  Such behaviour is experienced as fragility in the UX.

Waterfall design assumes that one step follows another (i.e. the steps are synchronous, not asynchronous (like mouse-drive GUIs))

Anti-waterfall design assumes that any step can occur at any time (i.e asynchronous).

It is *possible* to design non-fragile UXs using FP, but the FP paradigm encourages the avoidance of non-synchronous operations.  In the FP paradigm, it is more natural to assume that concurrency must be tamed and to accept that *rendezvous* must be used in a pervasive manner.  *Redezvous*, by virtue of treating all operations in a synchronous manner, decreases the opportunities for parallelism and efficiency unless tricky work-arounds are employed.  The world is asynchronous, people inherently understand concurrency[^wf4]. 

[^wf4]: For example, cooking recipes often contain concurrent instructions.  Businesses work best when all departments work independently.  Children learn to play piano with all 10 fingers.  Guitar chords contain 6 simultaneous notes.