
## Other Syntaxes

Random comments about miscellaneous syntaxes / technologies ...

Programming doesn't have to mean text-only.  The goal is to control (use) a computer.  The goal is to generate instructions for the computer to follow.  Somehow.

### Spreadsheets
- Maybe the most successful non-programmer syntax is the spreadsheet.
- flat grid
- list of builtin functions
- simple set of rules
	- grid + palette of possible functions to use
	- no decisions to be made about using nor extending the technology
	- simple, uncomplicated, "simplicty is the lack of nuance"
	- grade-school math, simple equations
	- simple syntax for accessing cells - row, column - no need to remember names
	- future: instead of naming cells, show different views
	- e.g. dependencies on other cells
		- Racket-like lines
	- e.g. synonyms, e.g. \$A1\$B2 is, also, called "Total", also, called "Sum of Column (\$C3:\$C99)"
	- use hotkey to toggle between \$A1\$B2 syntax and synonyms
	- there is no "one language to rule them all", different users may want different names, allow switching via synonym toggling
	- synonyms can apply to code, too
		- "y = *slope* times *x* + *y offset*" is, also, "y = mx + b"
		- λ functions are barking up this tree

### Relational Programming
- PROLOG
	- granddaddy of declarative programming
	- uses backtracking to perform exhaustive search
	- sneered at in 1950s, due to biases that favoured speed optimization
	- backtracking driven by desire to conserve memory
- miniKanren
	- does not use backtracking, but, also, implements exhaustive search
	- coagulates all possible outcomes and feeds set of outcomes forward
	- prunes outcomes that cannot happen from the set of possibilities
	- final result = set of all possible ways to satisfy a goal
	- not concerned with expending memory, hence, doesn't need to use backtracking
		- backtracking is difficult to implement
		- backtracking is difficult to understand
- what not how - declarative programming
	- Relational Programming splits problems into two parts 
		1. What
		2. How
		- What is specified by the human programmer
		- How is implemented in an engine, freeing the human to think about the larger problem instead of dealing with details

### Everything is a String
- Lisp treats everything as Lists, there are some languages that treat everything as strings
- SNOBOL
	- the granddaddy of string-based languages and string matching
- Icon
	- grew out of SNOBOL
- TCL/tk
	- TCL is a scripting language based on treating all data as strings of characters
	- tk is a library for creating graphical views on data that grew out of the ability to suppress details like how the data is actually structured (e.g. integers vs. strings, etc.)
		- the details are all still there, but are elided at the top level
		- the details are buried in the TCL engine
- Parsing
	- string-matching technology usually associated with compiler building
	- compilers are simply big transpiler apps
		- convert a string of characters into another string string of characters
		- high-level language text converted into assembler text (and/or to bits)
### Scripting
- like "everything is a string", but, includes files and redirection
- scripting is still *programming*, it uses scripts to control behaviour of computers
- example: /bin/sh
- example: emacs lisp
- example: cmd.exe
- often a "dynamic language" which punts typechecking to runtime

### Hypercard
- https://en.wikipedia.org/wiki/HyperCard
- https://hcsimulator.com

### Dataless Programming Languages
- dataless languages - don't require programmers to define data, just declare the existence of data
	- e.g. "handles" in operating systems
	- e.g. S/SL (Syntax/Semantic Language, Holt, et al) https://research.cs.queensu.ca/home/cordy/pub/downloads/ssl/
	- powerful enough for implementing compilers (e.g. PT Pascal, Concurrent Euclid, etc.)

### Concept: Orthogonal Programming Languages
- based on dataless languages, Cordy's Orthogonal Code Generator, and GCC's RTL
- OOP is ½ of the story
- control flow is the other ½
- data representation
	- Objects are often expressed as Classes with Methods
		- similar to mathematics concept of conditional functions
	- control flow is often expressed as *syntax*
		- syntax can, now, be quickly built using Ohm-JS (improved PEG)

### WASM
- Lisp-like syntax
- uniform syntax
- intended to replace JavaScript in websites
- intended to be "more efficient" than JavaScript
- attempt to add type information on operands and operators while using recursive assembler-like syntax

### VPLs
- StateCharts
		- StateCharts exhibit a lot of goodness
			- encapsulation
			- parental authority
			- diagrams instead of text for control-flow aspects
				- text can be used where it makes sense
		- reading of Harel's paper: https://guitarvydas.github.io/2020/12/09/StateCharts.html
- Scratch
	- ostensibly for children
	- hampered by synchronous mindset
	- https://scratch.mit.edu
- Full Metal Jacket
	- attempt at a pure functional visual syntax
	- https://www.fmjlang.co.uk/fmj/FMJ.html
- Drakon
	- rocket science
	- better than flowcharts (less ad-hoc)
	- transpiled to multiple languages, like Erlang, Python, Lua, etc.
	- https://drakon-editor.sourceforge.net
	- https://drakonhub.com/en/
- FBP
	- components that use streams of data
	- all components are asynchronous by default
	- https://en.wikipedia.org/wiki/Flow-based_programming
	- noFlo
		- grafts many concepts of FBP onto JavaScript
		- components are not asynchronous by default
		- https://noflojs.org
- node-red
	- one input port
		- need to look "inside" to see what inputs are supported
		- single input port assumption sprayed throughout node-red source code
			- not easily changeable
	- components are not asynchronous by default
		- function-calling (call-stack) remains at the heart of the notation/implementation
	- https://nodered.org
- LabVIEW
	- big, flat diagrams
	- doesn't encourage layered abstraction
	- encumbered by synchronous mindset
	- https://www.ni.com/en-ca/shop/labview.html
- ProGraph
	- diagrams of OO Objects
	- fundamentally synchronous, does not encourage independent layers
	- defunct
	- https://en.wikipedia.org/wiki/Prograph
- UML
	- "modeling" instead of "compiling"
		- very few constructs can be compiled to code, too abstract/ad-hoc
		- notable exception: StateCharts can be compiled to code
	- https://en.wikipedia.org/wiki/Unified_Modeling_Language
- hybrid
	- need detail to program a computer
	- text PLs provide detail for calculator-like operations
	- what does VPL provide beyond what text already provides?
- whither Diagram Compilers? Tech Diagrams?

### Low-Code
- deja vu all over again, used to be called RAD
- RAD - Rapid Application Development, 
- interpolate, cannot extrapolate

### HTML
- declarative description of websites
- needs JS as a crutch for imperative operations that aren't handled in declarative syntax
- the most common portable syntax
	- every browser on every computer, on every phone and every tablet supports HTML
	- assembler is more common, but not portable

### XML
- generalization of HTML
- attempt to parameterize HTML, resulting in complication

### Declarative Programming
- Barliman
	- https://www.youtube.com/watch?v=er_lLvkklsk
- Relational Programming
	- swipl
		- https://www.swi-prolog.org
	- miniKanren
		- http://minikanren.org

### TXL
- functional language for exploring syntaxes for existing languages
- http://txl.ca

### AI generates Code
- generated / trained code based on code in github
- synchronous - since most code in github is fundamentally synchronous, the training data is fundamentally synchronous, hence, the generated code is fundamentally synchronou
- ChatGPT
	- https://openai.com/blog/chatgpt/
- Copilot
	- https://github.com/features/copilot

### ROS, Behavior Trees
- Robot Operating System
	- complicated libary of functions that support asynchronous control using synchronous functions
	- https://www.ros.org
- Behavior Trees
	- epicycle to add *time* back into functional/synchronous code
	- "tick" is the same as "synchronous clock" in hardware design
	- builds asynchronous state machines on top of synchronous code, uses "tick" to step the state machines
	- https://navigation.ros.org/tutorials/docs/using_groot.html

### 1950s Text-based Programming Languages
- The difference between 1950s text based programming and more modern diagrams is that in the 1950s text needed to be arranged in non-overlapping grids of characters, whereas in 2022++ *text* is just another figure on the diagram.  
	- Figures can overlap.  
	- Figures can be moved around.  
	- Figures do not imply sequential sequencing.

### Smalltalk
- Smalltalk, like Lisp, doesn't have much of a syntax
- control flow implemented using "tricks" such as passing closures ("blocks") to functions
	- e.g. `if` is essentially a function that consists of 3 closures
		1. test expression (returns an Object of type Boolean)
		2. `then` block ("ifTrue:" message to Boolean Object)
		3. `else` block ("ifFalse:" message to Boolean Object)
- Methods are synchronous function calls
	- "message passing" is synchronous, not asynchronous