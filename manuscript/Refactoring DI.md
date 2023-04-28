# Refactoring - DI

## Main Takeaway

- readability, optimization is a detail

## Refactoring DI - Design Intent

It is the Software Architect’s responsibility to make a design readable and understandable.

If one uses a GPL[^rdi1] to express Software Architecture, the Software Architecture becomes hidden behind a sea of detail.

[^rdi1]: GPL stands for General purpose Programming Language

## Tipping Point

There is a psychological tipping point that affects DI Refactoring[^di].

At some point, there is too much code and the solution becomes "too big to re-engineer".

At that point, the act of *coding* overrides the act of *solving*.  We retain the code and throw away possible Architectural improvements.

What is that "tipping point"?

I haven't measured it.

I know that if I use Lisp, I am more likely to throw my code away when I encounter new design changes.

I know that if I use towers of data structures in just about any GPL I am more likely to ignore late architectural changes[^2].  

[^2]: When I try to change the Software Architecture in such cases, the existing code tends to "resist" the changes.  It is as if the Software Architecture has been calcified by the existing code.

I know that if I draw my solution on a whiteboard, I am more likely to accept and implement design changes.[^diagrams]

I know that if I can see my whole solution - say in one eye-full (a window, a page) - then I am more likely to accept and implement design changes.

[^diagrams]: Drawings can be automatically compiled to code.  I favour the use of a minimal subset of SVG as the atomic syntactic element (intead of single characters) - rects, ellipses, lines, text.

[^di]: DI means *Design Intent*.  Often, the term *Software Architecture* is overloaded to mean DI.











