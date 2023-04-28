# Compiler Technology (3)

## Takeaway - Optimization
- optimization

## Design and Optimization Don't Mix

Most modern programming languages, e.g. Haskell, Python, JavaScript, etc., etc. emphasize writing programs that are optimized[^ct3rp] for speed and space.

[^ct3rp]: Relational programming and functional progamming languages (like Haskell) are trying to distance themselves from optimization-driven thinking, but, have a long way to go.  Basically, any language that insists on programmers having to define user-defined types and data is usually asking Designers to specify too much detail (aka optimization).  Designers might define types and relationships between types without delving into details (like "is this an int64?" ; there is no need to tie types down to their bit-wise representations during Design - that is best left for Production Engineering).

### Separation of Concerns

To Design a program in the least amount of time possible, leave low-level optimization out of the picture and do only the Design work. striving to make it correct.

Early programming systems used to call this "Rapid Prototyping".

Early languages, like BASIC and Lisp provided IDEs that allowed programmers to explore the parameters to a Design.  These IDEs were usually in the form of REPLs[^ct3repl].

[^ct3repl]: REPL means Read-Eval-Print-Loop

Languages were, then, contorted to appease compilers.  This injected Optimization into the Design process. 

The compiler world developed ways to separate optimization away from programming languages. 

In the mid-1900's it was impossible to build programming systems that maintainted such separation and we developed "General Purpose programming Languages" as a stop-gap measure.

### PEG

In the 2000's, a technology, called PEG[^ct3peg], was invented.  This technology can be used to express Designs in a layered manner and to have computers convert the Designs into running code.

[^ct3peg]: See References for PEG.

Ostensibly, PEG was meant to be used to build compilers, but, PEG can be use to separate Design from Optimization.

Many programmers have not yet realized the potential of PEG technology.

We can - now - 
1. express Designs in a portable manner
2. dust off compiler techniques to rewrite and optimize[^ct33] designs for specific products.

[^ct33]: Optmize at a low level.  Large sweeping Design optimizations still need to be specified by Designers.

## Optimizing a Program Automatically

Making a program boring aids automation.

Normalizing a program makes it more repetive and boring.

Machines can execute boring processes.  

The more boring a task (program), the more automatable it is.

Readability - for humans - detracts from boring-ness, and, makes automation more difficult.

At first, human assembler programmers produced "better" code than compilers.  Compilers needed to work on normalized programs, whereas (human) assembler programmers invented clever ways to use CPU registers.  Later, optimization techniques caught up with the techniques that human assembler programmers used[^ct34].  Now, almost no one writes assembler in lieue of using HLLs.

[^ct34]: GCC was the first popular compiler to produce code as good as human assembly programmers could produce. 

Complex compiler optimizations were made possible by the fact that repetitive patterns could be (automatically) matched and replaced.

## Transpiling - Using Existing Languages as Assembly Code

Compilers, such as GCC, convert source code from one text format, e.g. C, into other text formats, e.g. assembler.

This "technique" could be used to convert text from one language into another, using the second language as "assembler".

For a simple example, the HLL statement
```
print "Hello World"
```
can be transpiled into JavaScript as:
```
console.log ("Hello Word")
```
or into C++ as
```
cout << "Hello World!";
```
or, into Lisp as:
```
(format *standard-output* "Hello World")
```
Or, we might transpile
```
2 * (42 - 1) / 9
```
into WASM
```
(module
 (func $custom (result f64)
 ;; 2*(42-1)/9
 f64.const 42
 f64.const 1
 f64.sub
 f64.const 2
 f64.mul
 f64.const 9
 f64.div
 f64.neg
)

 (export "custom" (func $custom))
```

## Failure Drive Design

In a blog post, I describe FDD - Failure Driven Design.

The goal of this technique is to have the computer write most of the code.

Ohm-JS (PEG) and compiler optimization techniques make FDD a practical workflow for Designing programs.

## See Also

[WASM Arithmetic Compiler POC](https://guitarvydas.github.io/2021/05/15/WASM-Arithmetic-Transpiler.html)
[Failure Driven Design](https://guitarvydas.github.io/2021/04/23/Failure-Driven-Design.html)
[Ohm](https://ohmlang.github.io).
