# Compiler Technology (2)

## Takeaway - Portability
- portability

## Portability

Portability is the notion of using the same code in multiple environments, e.g. multiple compilers for the same language, multiple target CPUs, etc.

Source-level portability has usually been performed using DSLs for conditional compilation (`#ifdef`, `*features*`, etc.)

Compiler research developed various ways of achieving portability, but, these techniques have not, generally, been used for source-level portability.  Part of the problem is that many languages emphasize human-readability over machine-readability, which impedes the ability to use automated code manipulation techniques, and, the portability techniques developed for compiler-buiding.

## Making a Program Portable

1. Write *what* you intend to accomplish (not *how* you want to accomplish it) as a general "script".  In this step, it helps to use a *dataless* language[^dataless] to reduce the temptation to describe the intention using too many details.
2. Debug this general script and make it correct.
3. Use automated rewriting tools to rewrite the above general script into optimized code for a specific CPU, language, application.

[^dataless]: See S/SL for an example of a dataless language.  Or, imagine describing your program using only functions and *handles* to data.  Modern compilers know how to inline functions - let compilers do the work, don't let inlining and optimizing creep into the Design phase. 

## Portability is a Subset of Optimization

Portabilty is a subset of optimization[^ct2subset].

[^ct2subset]: On one dimension, programmers tend not to duplicate code due to efficiency concerns.  On another dimension, DRY (Don't Repeat Yourself) concerns are the issue.  Compiler techniques for portability address most of these issues in an automated manner.

Portability can be achieved by normalizing the program.  Optimization techniques can then be used to automatically port the normalized program to other architectures.

RTL[^ct2rtl] ports programs to disparate CPU architectures using normalization ("everything is a register").

[^ct2rtl]: Fraser and Davidson's [RTL](https://www.researchgate.net/publication/220404697*The*Design*and*Application*of*a*Retargetable*Peephole*Optimizer) technique was used in GCC.

OCG[^ct2ocg] ports programs to disparate CPU architectures using normalization ("everything is a lower-level operation defined using Data Descriptors").

OCG provides a declarative syntax for describing portability decision trees.

[^ct2ocg]: [Orthogonal Code Generation](https://books.google.ca/books?id=X0OaMQEACAAJ&dq=bibliogroup:%22University+of+Toronto+Computer+Systems+Research+Institute+Technical+Report+CSRI%22&hl=en&sa=X&ved=2ahUKEwig1Legm8bqAhWvlHIEHYzzBYEQ6AEwBHoECAEQAQs)

## Projectional Editing

Portability is a subset of Projectional Editing.  

Projectional Editing is a subset of Normalization.



## See Also

[prep - a tool for rewriting code](https://guitarvydas.github.io/2022/01/20/PREP-Tool.html)




