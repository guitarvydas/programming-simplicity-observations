# APIs

## Main Takeaway

- restricted interface between components

## Input APIs

APIs usually specify only the *input* side of software components.

## Output APIs
Full APIs must include, both, *input* and *output* descriptions.

Dependency management is often conflated with APIs.  Ideally, there should be *no* dependencies between software components.

Note that it is not enough to specify the *return type(s)* of a function.  The function's *dependencies* must be specified.  

Dependencies include 
- references to all functions that are called by a function
- all of the types used by a function
- etc.

## DLLs
DLLs - .dll, .so, .dylib files - are one form of output API (created using indirection which is resolved by the linker).

DLLs are not currently formalized to the point of being first-class output APIs.

## Imports

Some languages require the use of *imports* statements to specify the dependencies of modules (functions, types)

Such *imports* statements can form output APIs.

## Normalized Interfaces, APIs

Input APIs and output APIs should look the same.

Currently we specify output APIs using a variety of syntaxes, e.g. exceptions, synchronous return values, etc.

## Components

A Component is described by
- a name
- an input interface
- an output interface.

N.B. Currently, we create APIs that contain too much detail, a result of flatness instead of layering.  Libraries are hard to use because of the fact that too much detail is exposed at the top levels[^api1].  

[^api]: Parameterized types only address the symptoms of the problem.  Ultimately, parameterized types result in unreadable code - everything becomes so abstract as to be non-understandable.

A part of this problem is that types are treated as flat entities, instead of being composed as layers and pipelines.  

We want very simple, generic types to form the interface between pluggable software units, but, we want to filter incoming data through restrictive type filters (pipelines of filters) before using them inside functions.  

We want to strip outgoing data down to minimalist types for easy interchange.

Maybe, we want all data to carry around "type signatures" which can be used by filters.  Removing such type signatures at compile-time is an optimization that impacts plugability of components.  We were convinced, by mid-1900s biases, that stripping type information at compile-time was necessary without fully realizing that the cost of doing so impacted distributed computing (i.e. internet, IoT, blockchain, etc.).











