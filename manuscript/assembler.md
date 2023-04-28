## Assembler (Ultra Advanced Programming)

Revelation: strings of bytes (e.g. ASCII) could be "parsed" to convert mnemonic words into binary opcodes.

For example, the string "RET" could be pattern-matched and replaced by the hex byte 0xC9.  This process mapped the 3-byte sequence
```
0x52
0x45
0x54
```

to the 1-byte sequence:
```
0xC9
```

Revelation: "RET" and "RETX" were parsed the same if a shortest match strategy was used.  The fix was to use a longest match strategy and make certain characters special. Whitespace was used to mark the end of any word. We call such special characters *delimiters*.  This led to the concept that whitespace is not allowed in mnemonic words. Note, that whitespace is used in prose, but is disallowed in programming languages.  A phrase in prose consists of several words separated by whitespace, whereas a phrase in a programming language is composed of syntactic constructs, like `if then else`, using words that contain no whitespace.

So, the 3-byte sequence, above, became a 4-byte sequence[^space]
```
0x52
0x45
0x54
0x20
```

[^space]:FYI - 0x20 is ASCII for "Space".  Practically, "Tab" - 0x09 - was used more often for cave-man-level pretty-printing purposes, but, still mapped to the same 1-byte sequence:
```
0xC9
```
It was discovered that *operands* of opcodes could, also, be parsed in similar ways. Comma was treated as a sub-class of delimiters:
```
MOV R0,(R7)+
```
Note that assembler used 2 very important, but subtle, tricks:
1. separation of operators and operands 
2. line-oriented

Both of these tricks make it easier to write programs that write programs. Tricks such as these led to invention of apps call 'compilers'.

### Separation of operators and operands
This is what is called "orthogonal code" and is espoused in Cordy's thesis[^ocg].

The "orthogonal code" technique is familiar to most programmers in the form of the *gcc* compiler.  An early form of orthogonal coding was Fraser/Davidson's Peephole technology[^rtl].

*GCC* uses orthogonal code techniques first, then optimizes the generated code using techniques that are described in the Dragon Book[^dragonbook] to generate assembler code that rivals assembler code written manually by human assembler programmers.  *GCC* is so good, that just about no-one bothers to write assembler any more.  At first, the concept of using compilers was thought to be too inefficient to be practical, and, was laughed at.  *GCC* changed such ideas.

[^dragonbook]: https://en.wikipedia.org/wiki/Principles_of_Compiler_Design (revised https://en.wikipedia.org/wiki/Compilers:_Principles,_Techniques,_and_Tools)

Unfortunately, the orthogonal programming technique has been ignored in the development of most programming languages.

Programming languages *could* be categorized as:
- operation phrases
- operands.

But, programming language designers fell under the spell of "one language to rule them all" and conflated control flow (operation phrases) with operands.

OOP (Object Oriented Programming) is a description of *operands* and could be used effectively in an orthogonal programming language.

### Line-Oriented Source Code
Another "trick" that helps in writing programs that write programs is the use of normalization.

One form of normalization is the idea of using lines of text to delimit programming phrases.

For example:
```
MOV R0,(R7)+
MOV R1,(R7)+
```
Is pattern-matched as 2 separate lines.  This "trick" makes pattern-matching easier.

"Easier" is a subjective term and a psychological trick.  If a technique is "easy enough", it will be used, and, become an idiom, and, will relieve the minds of smart people to think about more lofty problems.

Line-oriented assembly code was so "easy" to automate that it allowed programmers to invent higher-level programming languages, and, compilers, and, interpreters.

"Compilers" are simply "apps" directed at programmers.  Compilers stand on the shoulders of other apps-for-programmers, like assemblers.

#### UNIX® Shell Pipelines - Line-Oriented
A shining example of line-oriented source code being used to create bigger and better programs is the UNIX® shell and *pipelines*.

The UNIX® shell hard-wired the notion of *lines of text* into its structure.  

A slate of tools emerged from this simple, subtle assumption.  Tools like *grep*, *REGEX*, *sed*, *awk*, etc.

Programming languages have evolved into using a *structured* syntax, where programming phrases (like `if then else`) cross line boundaries and are recursive.

The UNIX® assumption of *everything is a line* is not good enough to handle most modern languages.  Lines are not recursive, where the syntax of textual programming languages is recursive.

### Aside - Tree-Oriented Source Code
A different approach to parsing is found in the language Lisp.

In Lisp, all source code is structured in the form of trees.  Lisp uses the concept of *list*s. Lisp source code is written in the form of *parse tree*s made from *list*s.  A unit of source - a Lisp function call - is a list (instead of a line) in a very rigid structure.  First, comes the name of the function, and the rest of the list (if any) contains the arguments to the function.  This format is often called Reverse Polish Notation[^rpn].

Like line-oriented assembler, this normalized structure makes it "easy" to write code that writes code.  Lisp notation led to the notion of *macros*[^cmacros].  Lisp macros are essentially code generators.

Unlike line-oriented assembler, the lisp list structure is recursive and can be used to write code that contains other code, i.e. functions that call functions that call functions, and so on.

[^cmacros]: Lisp macros are much more powerful that what is thought of as macros in other languages, like C.  Lisp macros are like plug-ins.  Lisp macros are functions that modify the operation of the Lisp compiler and interpreter.  Lisp macros are functions that run at compile-time.

[^rpn]: In fact, there is nothing "reverse" about this notation, it is a prefix notation.
