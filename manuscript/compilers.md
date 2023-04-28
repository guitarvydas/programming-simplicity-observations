
## Compilers

How do you build a compiler?

A compiler is just an app.  

A compiler is an app aimed at developers.

A compiler is a "complicated" app and involves a lot of programming techniques.

The point of a compiler is to convert text, written in some higher-level language, to assembler text and, ultimately, to binary opcodes that sequence the operation of computers.

A programming language - compiled or interpreted - is just a cave-man version of a programming IDE. Ultimately, programmers want to inject binary opcodes into electronic machines. Programming languages let programmers create opcodes while checking for a plethora of common mistakes.

The "worst" problems in building compilers are:
- how to generate fast/small binary code
- how to generate code quickly, so that developers have short turn-around times
	- early progams were written on punch-cards
	- punch-cards would be dropped into the hopper of a card reader, then the data on the cards was fed, electronically, to the computer, and, the computer would run the program and output results on paper
	- turn-around times for this process were something like 10's of minutes
		- programmers did not want to stand in line at the card reader, so they chose to carefully preen their code before going to the card reader
		- turn-around times were around one program run per day
		- computer time was expensive, and, access to computers was "billed"
			- programmers avoided blowing out their accounts and billings by double-checking their code for simple mistakes
	- running a compiler was a billable event, so compilers that were fast and small were favoured
### Compilers vs. Interpreters

#### Interpreter
An interpreter is an app that inputs a program written in some programming language.

An interpreter steps through source code and immediately acts on every instruction written into the code.

If the interpreter encounters a *loop*, it seeks to the next instruction and blindly executes it - even it has already seen the instruction before.

A hand-held calculator is an example of an interpreter. You press numbers on the keypad then hit and operator key, like `+`.  The calculator immediately interprets the operation and displays the result of the operation on an electronic display or on paper.  Early versions of calculators were completely implemented using ad-hoc electronic circuitry.  Even earlier, calculator were implemented entirely with mechanical wheels and pulleys.  Even earlier than that, calculators were implemented in wood and paint (e.g. slide rules).  Even earlier than that, calculators were implemented using brute force banks of humans who performed calculations on paper and clay tablets. 

A CPU is an interpreter.  It steps through an array of binary instructions (opcodes) and immediately executes each instruction as it is encountered.

The body of a CPU consists of a *case statement* that picks apart every instruction, in sequence, and a block of actions for each instruction.

The *case statement* and the *actions* are implemented as hard-wired bits of electronics.

#### Compiler
A Compiler is a specialized app for developers.

A compiler attempts to separate code into two big chunks 
1. code which needs to burn CPU cycles at runtime
2. code which can be pre-calculated and does not need to use CPU cycles at runtime (this kind of code *does* need to burn CPU cycles at compile time, but, it is assumed that compile-time happens much less frequently than runtime, and therefore, compile-time costs can be amortized to reduce the final cost of the product from the end-users' point of view).

For example, imagine a piece of code such as
```
var a = 1;
var b = 2;
loop exactly 10 times
	var c = a + b;
end loop
```
An interpreter will blindly recalculate the value of c the same way 10 times.

A compiler will notice that `c` is redundantly calculated in the loop 10 times.  A compiler will move the calculation out of the loop and try to make the code something like:

```
var a = 1;
var b = 2;
var c = a + b;
```

In fact, a compiler might try to do more, like noticing that `a` and `b` are constants and, therefore, `c` is a constant.  But, we won't go there in this discussion.

A compiler restructures the code and then outputs binary opcodes that are "optimized" to reduce the number of CPU cycles burned at runtime, or, to decrease the size of the binary code (or, many other kinds of things).

A compiler does not directly execute the code, it simply optimizes the array of binary opcodes which will be interpreted at runtime.

### How Do You Write Code That Figures Out What Can Be Pre-Compiled?

How do you write this kind of app?  In other words, how do you write a compiler?

This is just like any programming problem.  There are many solutions to this problem.

One very common approach is to redefine the programming language.  The redefinition makes it easier for the compiler app to spot opportunities for optimization.

In essence, this approach puts the onus on the programmer to help out the compiler app.

I call this approach "compiler appeasement".  It trades off the use of human brain cells for stroking the compiler app in "just the right way" in lieue of using those brain cells for thikning about more lofty problems.

A glaring example of compiler appeasement is the concept of *declaration before use*.  The human programmer is expected to declare every variable that will be used in the program in order to allow the compiler to double-check for typos.  Worse, *declaration before use* requires human programmers to restructure their code to ensure that declarations of variables all appear in the code before any actual instructions that use the declared variables appear in the code.  This restriction was invented in the 1950s when it mattered that compilers be lean and fast.  *Declaration before use* allows compiler-writers to write compiler apps that need to make only one pass through the source code.  In 2022++, it is not necessary to make compilers this lean and this fast, but, programming language designers continue to use *declaration before use* rules in their language designs.  Multi-pass conversion programs were well-known in the 1950s - assemblers were built to scan source code multiple times - so, it is obvious that the decision to use one-pass compilation was a conscious decision and was not made due to lack of existing techniques.

Another glaring example of compiler appeasement is the use of types and classes. During the design phase of a project, programmers don't necessarily want to specify all types in detail[^types], but are required to do so in order to use modern programming languages.  Lisp showed that it was possible to use gradual typing.  ML showed that it was possible to infer types automatically (using a machine).  These ideas are only slowly leaking out into the popular programming language world. 

[^types]: Some programmers like to lean on type checkers to help them iteratively produce internally-consistent designs.  This is a *choice* and should not be a *requirement*.

### Compilers Are Interpreters

Compilers, are themselves, interpreters.

Compilers interpret their own app code, and, breathe-in programs, and, spit-out optimized binaries.  Compilers interpret their own code immediately with the goal of producing optimized binary code for other programs.

In analogy, compilers are like hand-held calculators that need more expensive hardware than that needed for calculators.

### Tokens, Tokenization

One of the problems of writing compiler apps is the fact that certain character strings appear in the source code over and over again.

Scanning the same string repeatedly burns CPU cycles and introduces the chance of making compiler-writing mistakes in the string-scanning code.

To reduce these burdens, compilers do as much of the string-scanning up-front, and encode strings as cheaper-to-use numeric codes.

Parts of compilers that perform up-front string-scanning are called *scanners*.

In modern languages, scanners are simply glorified maps (hash tables).  The scanner code collects up incoming characters and looks for word/phrase boundaries, usually defined by delimiters like whitespace.  Once a complete word is found, it is replaced by a more-efficient code.

For example, the scanner might find the word "then" in the source code and replace it with a code number like 8.  The downstream bits of the compiler "know" that 8 means "then", or they can look this information up in a table (map).  The string "then" is usually 5 bytes long (four letters plus a NULL), whereas the code 8, is one byte long.  The string "then" is potentially variable in length, whereas the code 8 is always fixed size.  Variable-length string matching uses up more CPU cycles than using fixed-size codes, since, codes are usually handled directly by the CPU whereas variable-string-matching usually requires many CPU instructions (usually in a Loop). 

Delimeters are nothing special.  Delimiters are simply characters. Each programming language defines a set of rules for what is considered to be a delimiter and what is considered to be some other kind of character.  Over time, it has become conventional to treat whitespace as delimiters and characters in the ASCII range 33..127 as other kinds of characters. In fact, the range of characters is further sub-divided and classified as "digit", "letter", etc.

It has, also, become conventional to classify whole words into categories, broadly *keywords* and other *identifiers* and *operators*.  Keywords are words that have special meaning in the language, like `if`, `then`, `else`, etc., and operators are usually single characters[^more] that don't look like words to human eyes, e.g. `+`, `>`, `"`.  Most other words fall into the bag of being *identifiers*, i.e. word-like strings that have no special meaning in the language, for example, words like "x", "xyz", etc. 

[^more]: sometimes more than one character, like "<=", ">>", "+=", "\=\=\=", etc.

### Trees

Compiler-writers often structure their designs using *tree* data structures.

TODO: syntax tree

### AST vs CST
Compiler-writers often use the abbreviation "AST" and "CST" to mean certain variations of tree data structures.

"AST" usually means *abstract syntax tree*.

"CST" usually means *concrete syntax tree*.

These data structures are almost the same, except that ASTs usually encode all of the *possible* choices whereas CSTs usually encode only what was pattern-matched in the incoming, user source code.

Usually, an AST forms a specification for the pattern matcher.

Usually, a CST is the output of a pattern matcher.

The pattern matcher is most often called a *parser*.

In analogy, a simple sample REGEX specification might look like:
```
.replace(/x\([uvw]\)z/,"\1")
```
In this case `/x\([uvw]\)z/` would be like the AST *before* the pattern-matching operation. `\1` would hold the CST *after* the pattern matching operation.  Neither the AST nor the CST contain all of the user's input text, but the CST contains the users' input text broken down into pieces that were matched by the matching engine.  In practice, a real CST produced by a parser would probably contain more pieces and more detail than can be shown in this simplified example.

In the above simple example, the AST encodes pattern-matching information such as:
1. first, match the letter "x"
2. then, match one letter which might be a "u" or a "v" or a "w".
3. then, match one more letter, "z".

This information is encoded in some way and handed to the pattern-matching engine.  The engine is just a block of code that understands the encoding. The engine does the work of matching the input source characters against the encoding.  The encoding is usually in the form of a *tree*[^tree].

So, the engine receives a set of details encoded in a *tree* data structure and it produces a pared-down *tree* that contains a break-down of what was matched in the source code.  The first kind of tree is called an AST. The second kind of tree is called a CST.

[^tree]: "Tree" is a shorthand word that programmers use to talk about a certain kind of data structure.  Most normal humans like to draw equivalent data structures as a set of nested boxes, say on a whiteboard or on a scrap of paper.  Programmers, though, like to unwind the nested boxes and draw them out in something that resembles an ORG Chart.

### Tree Driven Compilation
A natural way to represent possible matches (parses) is to specify possibilities as *trees* and to construct pruned trees of what was actually matched in the source code.  The specification tree is called an AST, and the match is called a CST.

Given that the pattern matcher - the parser - produces tree data structures, it is natural to hand bits of app code onto the trees, like Christmas ornaments hung on a bare Christmas tree, that do "the rest" of the work of coverting the input source code into arrays of binary opcodes.

Since pattern matching - scanning and parsing - has become easy to handle, the "rest of the work" is actually the difficult part of writing compilers.  

This stuff is "just more code", but it can be overwhelmingly large and tricky to get right.

Firstly, the compiler needs to do semantic analysis, then it needs to do allocation, then it needs to emit dumb code, then it needs to optimize the dumb code to become better code, and so on.

Once a compiler has been fully written and debugged by hanging code bits off of the AST, the result is hard to understand - the code is a wall of overlapping details.

Can you improve on the use of trees?

Yes.

Can you improve on the whole process, breaking the compiler down into smaller, more understandable, more manageable chunks?

Yes.

Ohm-JS uses trees but keeps subsections highly separated.  One section performs pattern matching, another section deals with the information contained in the trees.  Using Ohm's concept of multiple semantic operations, it is possible to subdivide the big task of compiling text programs into smaller pieces each of which do "one thing well".

#### DSLs, APIs, Opcodes

As an aside, consider DSLs (Domain Specific Languages) and APIs (Application Programming Interfaces) and, even, CPUs themselves (opcodes).

The point of developing and using DSLs is to focus on smaller tasks.  For example, SQL is a DSL designed for database manipulation.  Instead of using ad-hoc code written in some 3GL programming language (e.g. Python, Haskell, Rust, etc.) it becomes possible to focus solely on the database aspect of a problem solution, using SQL.

APIs have a similar intent.  APIs form tight funnels for accessing myriads of features provided by library code.  APIs are tuned for focusing on specific problems and to eschew details that don't apply - at that level - to the specifc problems.

CPU opcodes are the same kind of thing.  Internally, CPU chips are huge blobs of electronic circuitry.  Opcodes define a narrow access to the circuitry.  The opcode API restricts what can be done, but covers the majority of use-cases needed to form an electronic solution to some problem.

Likewise, programming languages are APIs layered over top of opcodes.  Programming Languages further restrict what is possible to do with the electronic circuitry, but, Programming Languages also provide checks for common mistakes made by programmers.

This DSL/API/opcode strategy can be taken further.  One can define more and more specific solutions to use-cases.  These solutions can build on existing DSL/API/opcode interfaces, tuning them for greater detail within smaller domains.
From this viewpoint, something like SQL appears to be too grossly general.  One doesn't want general solutions to the database problem, one wants specific solutions to specific applications of databases for specific use-cases.  I use the term SCN - Solution Centric Notation - to mean such tiny, fine-tuned nano-DSLs.  The main reason that SCNs are not more common is that building nano-DSLs appears to be difficult and time-consuming, causing programmers to program specific solutions using ad-hoc code written in 3GL programming languages, like Python, Rust, etc.  The SCN "problem" then becomes "how does one build SCNs quickly (in an afternoon)?".  There are ways to do this.

### Do One Thing Well
The concept espoused by UNIX® and especially shell pipelines is the idea of chopping a problem up into many smaller subdivisions, then addressing each subdivision in a more focussed manner without dealing with details that aren't related to the subdivision.  

This doesn't mean that unrelated details are ignored, it simply means eliding details and not having them intrude on thinking about the problem/solution-at-hand.  

This is much like what compilers do - they optimize programs by subdividing programs into two portions
1. the bits that need to be done at runtime
2. the bits that can be done before runtime.
All of the details in the program are addressed, but, subdivisions are made as to *when* the details are addressed (compiletime or runtime)

This concept seems to have been buried by the mistaken belief that nested functions are the same as pipelines.  Synchronous functions cannot chop a problem up into smaller independent parts because synchronous functions are synchronous and not independent.  Synchronous functions rely on use of the callstack, whereas asynchronous components use queues instead of the callstack.

### Syntax Driven Compilation
 Compilers can be built in a pipeline manor subdividing the tasks into smaller parts, but, something needs to be used as glue to combine the smaller tasks into a larger whole.

Syntax-driven compilation uses "syntax" as the glue.  Sequencing a walk through the syntax of a program allows programmers to hang bits of code off of the branches of the AST while focussing  totally on a single sub-problem.

Syntax-driven compilation can be used to form a serial pipeline, where each stage in the pipeline uses the syntax of unique nano-DSLs to guide applications of bits of code.

For example, the first stage of semantic analysis is to gather up all of the declarations into a table, or a tree of tables based on scopes.

A syntax-driven first-pass of semantic analysis would accept a stripped-down syntax and look only at declarations in the language, skipping over all other constructs.  

This first-pass would re-emit the incoming code mostly "as is", but remove all declarations.  The subsequent passes are not interested in declarations, so they are not included in the downstream code.  In essence, the CST that is sent further downstream is pruned to remove all of the details that have already been handled - in this case all declarations.

This first-pass of semantic analysis would visit every declaration and create entries in a symbol table.  It would not bother to emit the declarations themselves.  In places that this first-pass skips over incoming code, the first-pass simply re-emits the code to its output.

The parser pass, which precedes the semantic pass, would remove all syntactic noise to produce a machine-readable, albeit not human-friendly, tree of the important parts of the program-to-be-compiled.

This process is very similar to the concept of walking the CST, except that each pass is allowed to modify - pare down and reformat - the CST before sending it downstream to subsequent passes.

##### Efficiency
Changing a tree and then re-parsing it in subsequent passes might create efficiency issues.  

Is it cheaper to keep the CST intact and to walk it multiple times, or, is it cheaper to modify the CST, or, is it cheaper to leave the CST unmodified and to simply skip over uninteresting parts?  

From a Designers' perspective, it matters only in how one's attention is directed and focussed - it is easier for a human programmer to focus on a problem, when there is no noise to ignore [^coredump].  I.E. using multiple passes and multiple nano-DSLs is useful in the Design phase of a project.

From a Production Engineers' perspective, though, size and speed matter - keeping the noise intact might help speed up the process or might use up less memory.  I.E. from a Production Engineers' perspective, it is better to squish bits of code together in order to save time and space at runtime.

It might be possible build a smart editor that changes the opacity of already-considered CST nodes and allows nodes to be dynamically inserted and modified.

[^coredump]: This is similar to the debugging of "core dumps" in earlier programming systems.  Eventually, core dumps were replaced by 1-line error messages that helped programmers to focus on mistakes and errors instead of spending time digging through too much information. I liken "throw" in modern languages to core dumps. Throws usually supply too much information and cause programmers to pause while trying to discern information that is meaningful to their specific problem (bug).

The pipeline strategy is, in fact, a 1950s optimization for keeping things small - K.I.S.S.[^kiss].  In 1950, it was considered good form to make code footprints as small as possible.

Regardless of the 1950s emphasis which is no longer applicable, the KISS mentality is relevant today, in 2022++, as a way of subdividing problems into smaller and smaller bits, ignoring their actual code size.

[^kiss]: https://en.wikipedia.org/wiki/KISS_principle

### Compiler Phases
Compilers can be subdivided into several main phases, regardless if the phases are made explicit or are conflated with code for other phases.

1. scanner
2. parser
3. semantic analysis
4. code emitter
5. optimization

#### Scanner
The Scanner phase accepts input text in the form of a stream of characters and outpus a revised stream where strings of characters have been replaced by Tokens.  

Tokens are less expensive to handle in the subsequent phases.

#### Parser
The Parse is a pattern matching phase.

It checks that all tokens are arranged in a sequence that makes sense relative to the grammar of the language begin compiled.

When invalid token sequences are found, the Parser creates error messages.

The error messages produced by Parsers are called "syntax errors".

A significant feature of Parser design is to keep the Parser chugging along when an error has been detected.

Parsers that quit after finding only the first error are considered unfriendly.

Again, in the 1950s, computers were much slower than in 2022++.  Fixing only one syntax error at a time was a laborious, time-consuming process.

#### Semantic Analysis
The Semantics phase checks for mistakes that are not found in the Parsing phase.

To this end, Semantics analyzers consist of two main sub-phases:
1. gathering informatin from declarations
2. checking variable and identifier usage against gathered information.

The simplest checks include:
- checking for typos by ensuring that programmers have explicitly declared every identifier
- checking function calls by simply counting the number of parameters in function calls against how they are declared
- checking the "type" of every parameter in every function call against how the functions are declared
- checking the "type" of every variable and every expression to ensure that they are used in compatible ways, as defined by the programming language.

Modern type checkers do work well beyond the above-listed simple checks.  One wonders whether the traditional parts of the Semantic Phase need to be further subdivided, e.g. shallow-check vs. deep-check.  The driving questions would be "would the feedback to programmers be faster with such a subdivision?  Is it worth doing deep-checks when violations of shallow-checks have been detected?" 

#### Code Emitter
The Code Emitter phase produces first-cut code that corresponds to the program-to-be-compiled.

The pentultimate code emission strategy is used by GCC and espoused in Cordy's thesis "Orthogonal Code Generator"[^ocg].  

Code is first emitted for a fictitious architecture, then, secondly,  fine-tuned and ported to the actual target architecture.  

GCC uses RTL which was documented as a peephole technology by Fraser/Davidson[^rtl]

[^ocg]: https://books.google.ca/books/about/An_Orthogonal_Model_for_Code_Generation.html?id=X0OaMQEACAAJ&redir_esc=y

[^rtl]: https://www.researchgate.net/publication/220404697_The_Design_and_Application_of_a_Retargetable_Peephole_Optimizer

5. optimization
The optimizer refines the emitted code to be more optimal in some dimension, e.g. speed, size.

Some optimizations require global restructuring of the CST, which implies that this phase may precede the Code Emitter phase.

Full-blown optimization can be time-consuming and resource-consuming.  Such full-blown optimization is not required during Design, but is required during Production Engineering.  GCC supplies command-line options	to control the amount of optimization, e.g -O options.

See the Dragon book[^dragon] for further information about optimization.

[^dragon]: https://en.wikipedia.org/wiki/Compilers:_Principles,_Techniques,_and_Tools


#### Portability and Target Architectures
Each kind of CPU has a different set of opcodes with differing capabilities.

For example, some CPUs support operations, like ADD, that deal only with integers or certain sizes (e.g. 8-bits, 16-bits, etc).  Other architectures support the same kinds of operations with larger ranges of operands (e.g. 32-bits and 64-bits in addition to smaller sizes).  

The main factor driving such architectural decisions is cost.  It costs more space on IC chips to support wider kinds of numbers.  This cost affects factors like die size, pin count and final cost to the consumers.

Compilers, especially for modern languages, are expected to emit code for a wide class of architectures - and, to ensure that the code is semantically the same for each architecture regardless of final instruction count and speed.

For example, programmers expect the C statement `a = b + c;` to work the same on 8-bit processors as well as on 64-bit processors.  Type analysis provides information to compilers as to what kinds of instructions to emit.  Peepholing[^rtl] and MISTs[^ocg] provide convenient ways to write decision trees that automate code sequence selection.

##### Peephole
A peepholer consists of a small, sliding window used to pattern match certain instruction sequences and to replace them by other instruction sequences.

For example, we invent a simple case:
```
...
MOV R3,R5
MOV R0,1
MOV R2,R0
ADD R2,R3
...
```
In this case, let us imagine a 2-instruction window.

In this case, the peepholer looks for redundant MOVes of a constant through one register into another, e.g. 
```
MOV R0,1
MOV R2,R0
```
will be replaced by
```
MOV R2,1
```

The peepholer looks at the first pair of instructions
```
MOV R3,R5
MOV R0,1
```

and doesn't find the pattern that it's looking for.  The peepholer does nothing and moves the window down to the next pair of instructions
```
MOV R0,1
MOV R2,R0
```
This is the pattern that it's looking for, so it replaces the pair of instructions with one instruction, then moves the window down to see:
```
MOV R2,1
ADD R2,R3
```
This does not match the pattern that it's looking for, so the peepholer does nothing, moves the window down and discovers that it is finished.

The final optimized code is:
```
...
MOV R3,R5
MOV R2,1
ADD R2,R3
...
```
which, in this case, is one instruction shorter (and faster).

It should be obvious that the window can be made larger and the set of patterns made more interesting and parameterized.

This strategy was easy to code up in *awk* and should be easy to code up in more recent languages that support REGEX, e.g. JavaScript, Python, etc.  REGEX is not actually needed - any string matcher will do.  REGEX makes it easy to specify string matches as long as the patterns don't cross line boundaries or break any REGEX rules.

##### MIST - Decision Tree

The term MIST means Machine Independent Strategy Tree.

The compiler produces code for a ficticious architecture that consists of a set of small operations - an IR (Intermediate Representation).  For example, an IR operation might be `a := b + c`

The tree is specified by a human compiler-writer and includes consideration for the kinds of operands that might be used with the IR.  For example, the tree contains conditions like "if the operand is a constant integer that fits in 8 bits", or, "the operand is a temporary slot on the stack", or, "the operand is in a slot in the global heap", etc.

The compiler code includes an engine (a function) that walks the tree and selects the "best" code for a given intermediate instruction vs. a real CPU architecture.

Fundamentally a MIST encodes a decision tree - a set of choices for how code might be emitted

The snapshot below was taken from the original thesis.  The MIST encodes some choices for `a:=b+c`.  The default choice is near the top of the tree.  As one moves down the tree, each desicion branch is guarded by a condition based on the operands, with "K" meaning "compile-time constant".  For example, if the operand `b` is the same as `a` and the operand `c` is the constant `1`, the final choice is to use an `INC` instruction. The thesis goes into more detail, including various IR instructions and various target architectures.

{width:"40%"}
![IMG_0090.png](resources/IMG_0090.png)
### REGEX - Regular Expressions
REGEX is a DSL for pattern matching strings on line boundaries.

REGEX syntax is fairly sparse.  Patterns are specified as characters interspersed with special characters and symbols.  REGEX specifies a way to capture sub-matches and names these submatches with numbers, e.g. `1`, `\2`, etc.  When used for match replacement, REGEX can capture sub-matches and use the captures to create new strings.  

For example, the JavaScript snippet below flips the matched characters and surrounds them with new (upper-case) characters.
```
var s = 'xaybz';
var s2 = s.replace (/x(a)y(b)z/, "F$2G$1H");
console.log (s2);
```
In UNIX® versions of REGEX, the replacement numbers are preceded by backslashes, e.g. `\1`, `\2`, etc.

REGEX originated in the compiler world as a way to formalize the building of Scanners.

One of the first REGEX libraries, `regex.c`, was written by Henry Spencer[^hs]

REGEX can be found in various languages, like Perl, JavaScript, Python, Common Lisp, etc.

One can develop and test REGEXs on the website regex101[^regex101].

[^hs]: https://en.wikipedia.org/wiki/Henry_Spencer

[^regex101]: https://regex101.com

The Dragon Book[^dragon] explains algorithms for compiling REGEX syntax into state machines for pattern-matching strings.

#### BNF
A notation called Backus-Naur Form[^bnf] - BNF - was invented for succinctly specifying pattern matchers.  

[^bnf]: https://en.wikipedia.org/wiki/Backus–Naur_form

Pattern matching specifications are called *grammars*.

Research into Language Theory focused on specifying *context free grammars*.  

Context free grammars are a subset of more general grammars.  Context free grammars consider patterns to match given any surrounding context.  For example, "then" might be specified to match the same way anywhere in the source code.  In a context free grammar the line
```
x = then
```
would always be considered to be 
1. an identifier 'x'
2. an operation '='
3. a keyword 'then'.

Whereas in a context-dependent grammar, the meaning of 'then' might be determined differently because it appears on the right-hand-side of an assignment.  It might be that `then` is taken to be part of an 'if-then-else' statement in one context, but `then` is taken to be a variable name in an assignment context, like `x = then`.  In this simple example, `then` has two different interpretations and the interpretations depend on the surrounding context.

All modern programming languages employ context free grammars.  Very old languages, like some versions of FORTRAN, employed more ad-hoc heuristics for parsing characters that depended on surrounding context.

The context free grammar assumption makes parsing some kinds of sequences impossible, like recursive matching of matched brackets.  (See PEG, below).

### YACC, LEX, Bison, etc.
Several tools were developed for helping to write Scanners and Parsers.

Scanners were often written with the LEX program.

Parsers were often written with the YACC program.

Bison is a GNU variant of the YACC tools.

Newer compiler tools, like ANTLR and LLVM, have been developed.

PEG (Parsing Expression Grammars) work differently from YACC and CFG-based parser generators.  PEG can parse patterns that CFGs can't.

- PEG
- WAM, gprolog, swipl?
- Small-C
In the 1950s/1960s/1970s/1980s just about all software code was closed source.  It was difficult to get to see how code was written.

Students at some universities were able to legally see the source code for UNIX®.  The cost for obtaining a source license for UNIX® source code was high.  Only some universities could afford to pay for license and to allow their students to see the code.

One magazine, Dr. Dobb's Journal of Calisthenics and Orthodontia, published the full source to a subset C compiler, called "Small C"[^smallc].

The compiler could be compiled and run on PDP-11 computers and it produced assembler code for the 8080 CPU architecture.  The assembler code produced by the compiler was in text form and could be inspected and understood.

The compiler did not optimize the generated assembler code.  The compiler worked in a sub-optimal manner, using strings and string comparisons instead of tokens.  This made it even easier to understand the mapping from C to 8080.

This simple compiler influenced a number of hobbyists and programmers, giving them a deep understanding of how compilers work.

[^smallc]:https://en.wikipedia.org/wiki/Small-C

### PEG
PEG - Parsing Expression Grammars[^bford] automatically create Parsers in a manner that is significantly different from CFG-based parser generators.

PEG makes it practical to parse constructs that CFG-based technologies cannot parse.  Most notably, PEG can parse matching pairs of brackets.  This simple difference makes is possible to imagine parsing in a new way.  PEG makes it possible to write smaller grammars that "skip over" uninteresting bits of text.  For example, to extract the names of all functions defined in a C file, using CFG technology, one must write a full grammar for C first.  With PEG technology, it is possible to write grammars using less code and smaller grammars, saying something like "a function definition is an optional type, followed by a name followed by stuff enclosed in parentheses, followed by stuff enclosed in brace brackets".  Only the function names are interesting - in this simple example - whereas all of the other stuff is noise that can be ignored.  PEG allows you to loosely define "noise", whereas CFGs make you spell out all of the details contained in the "noise".  So, instead of writing a huge grammar for a huge language, PEG lets us write smaller, 1-line grammars that match only what we're intested in.

PEG, though, produces confusing results when trying to parse source code that has mis-matched brackets, i.e. syntax errors.  

This confusion is similar to what happens when strings in source code are improperly terminated and cross line boundaries.

Hence, small, PEG-based barnacle matchers are practical only for well-formed source.  It might be better to use both technologies - CFG parsing while debugging syntax problems in source code, then PEG quickie parsers for everything else.  

You don't imagine writing quikie parsers using CFG technologies, but, you can imagine writing such quickies using PEG technologies.

### Ohm
Ohm, and Ohm-JS, are improved versions of PEG.

A subtle, but important, point is that PEG requires you to write grammars that include details about whitespace.  Ohm fixes this problem.

Most PEG libraries, require you to embed "semantic" code into the grammar itself.  Semantic code is the second half of pattern-matching-replacing programs.  "Now that I've matched this input text, what do you want me to do with the matching bits?".  

Embedding semantic code into grammars makes the grammars less readable.  Grammars basically become walls of details and use-cases.

Ohm fixes this embedding problem.  

Ohm grammars remain readable.

The semantics code is pushed off into another layer.  

This may seem to be a minor UX detail, but it is significant.  Keeping the grammar readable makes it possible for the Designer to concentrate only on the grammar at first.  Once the grammar is debugged, the semantics can be added (elsewhere) and the additions make sense in the context of the Design.  This kind of "separation of concerns" makes it possible to others, e.g. newly on-boarded employees, to come down the learning curve more quickly.  Separation of concerns makes it possible to maintain and upgrade code with much more confidence and fewer bugs.

Ohm-JS, also, comes with a tool call Ohm-Editor.  This is essentially a REPL for developing and debugging grammars.  This tool is vital in speeding up development and making the result more robust. 

Even if not using Ohm, one should consider using Ohm-Editor to help write grammars.

Ohm could become as useful as REGEX syntax that is built-into programming languages.  Ohm, based on PEG, can match text that REGEX cannot easily match. For example, Ohm can match multi-line constructs while REGEX was originally intended to match only single-line constructs.  Ohm can be used to match many modern programming languages, whereas, REGEX makes such matching hard work.  Furthermore, the DSL syntax of REGEX is "uglier" than Ohm's syntax.

The use of a mixture of Ohm and REGEX matching, results in a new style of programming.  Perl brought REGEX down from the compiler-building moutain.  Ohm-JS can bring PEG down to programmers who would normally not consider building compilers, yet, want to perform simple pattern-matching chores, such as input validation. 1-line input validation is easily handled by REGEX.  Ohm opens up the design space to include multi-line input validation and nano-syntaxes.

[^bford]: https://www.researchgate.net/publication/2882170_Parsing_Expression_Grammars
