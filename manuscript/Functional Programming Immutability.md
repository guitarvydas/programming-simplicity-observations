# Functional Programming - Immutability

## Takeaway - Immutability

Functional notation only works if mutation of data within functions is disallowed.

Anti-mutation is not exclusive to functional notation.  Any notation that provides *isolation* provides the notational benefits of immutability.

Functional notation breaks down, roughly, into 2 parts:
1. the mechanics of manipulating the notation
2. the insights gained through mathematical reasoning.

The mechanics, (1), is simply "text find-and-replace".  This used to be difficult in its own right, but, now, computers can do much of the rote work of notational manipulation.

People are accustomed to non-interacting objects.  For example, if we have two balloons and we let the air out of one of them, the other balloon is not affected.  The world is full of non-interacting objects.  

The notation for music - a musical score - is usually written out on paper.  The contents of scores are not dependant on other scores.  The scores are *isolated* and contain no inter-dependencies. 

Two computers joined by a wire are non-interacting.  Each computer runs at its own speed with its own *state* without depedencies on one anoter.  We encounter "trouble" (aka Accidental Complexity) when we try to express *all* computers with one set of mathematical equations.  We encounter "trouble" when we try to break a computer program, that runs on a single computer, into multiple indepedent units.  This used to matter when CPUs and Memory were expensive and scarce.

CPUs and Memory are no longer expensive and scarce.

We need a notation for reasoning about isolated components.  This may turn out to be a form of mathematics that deals only with the external properties of components.  In fact, this kind of thing is already happening in Physics.  One lump of equations deals with "macro" Physics, while a different lump of equations deals with "nano" Physics.  We have difficulty finding a "unified field theory" which describes Physics at *all* levels.

Maybe, our understanding of Physics is insufficient.  In the meantime,  each model is useful, as long as we stay within the limits of the respective models.

Note that our understanding of a certain model - of Physics or software - becomes refined over time.  Our models, and, their equations, change.  At one time, it was believed that Atoms were the smallest particle in Physics.  Today, we think differently and speak of sub-atomic particles.

There is no fundamental reason why we should be able to find a *universal* set of equations that explains all of Physics.  We continue to attempt to find a unified field theory.  The models we develop in this quest - even if ultimately wrong - turn out to be useful.

Likewise, there is no reason why we should be able to find a *universal* set of principles that describes *all* of software. 

*One* language for all of software might not exist.

For example, many people find spreadsheets to be useful.  Yet, spreadsheets are not usually provided in most GPLs[^fpi1].  Mathematical models of software can be used to understand spreadsheets at a "nano" level. Such models of software are too nuanced ("compilcated") to be used by spreadsheet users.

[^fpi1]: GPL means General Purpose programming Language.

Mechanical Egineering teaches that objects need to be drawn in 3 views - *front*, *top*, *side*.  In this paradigm, each physical 3D object is represented in 2D as multiple views.  Compressing 3D to 2D requires 3 views.

This may turn out to be the case in software.  Any software problem might need to be addressed using multiple languages.
