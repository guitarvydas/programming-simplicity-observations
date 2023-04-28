# Multitasking

## Anti-Takeaways

- time-sharing
- memory-sharing

## Mid-1900's

Multitasking is the technique for running multiple programs (apps) on a single computer.

The idea of multitasking was invented in the mid-1900's when CPUs were expensive and memory was limited.

It was assumed that we would need to share the (expensive) CPU and would need to recycle memory.

Small computers - Raspberry PIs, Arduinos, etc. - have changed the ground rules.

CPUs are no longer expensive and memory is abundant.

## How To Avoid Time-Sharing

Use multiple CPUs.  

For example, use many Raspberry PIs, use multiple laptops, use many phones. 

rPIs are cheap.  

Laptops are fairly cheap.  

Smart Phones are cheap (everybody has one).

## How To Avoid Memory-Sharing

Use Send().

Do not rely on function-calling mechanisms.  Function-calling is a notation that *hides* the existence of a shared stack[^mt1].

[^mt1]: The Stack is used for return addresses and for data-passing, i.e. parameter-passing.  The Stack must be shared between functions to enable the function-calling paradigm.  The Stack contains data of many types.

### Immutability

Immutability is but one way to avoid memory-sharing.

### Ownership

Ownership is but one way to avoid memory-sharing.

## Isolation

Isolation is a superset of ownership and non-mutability.

Ownership and non-mutability are but implementation details (lesser forms of isolation, prematurely optimized).

### Deja Vu All Over Again

Have we already tried *isolation*?

Yes - for example UNIX pipelines provide *isolation*.

Yes - distributed processing involves *isolation*.

Yes - HTML + Javascript provides distributed processing.

### Encapsulation

OO-style encapsulation encapsulates data.

Q: Does OO encapsulate control-flow? Consider method over-riding.

### GOTO

GOTO modifies control flow.

Q: Can you read programs written in GOTO style?

### CPS

CPS (Continuation Passing Style) encapsulates control flow and data.

Q: How does CPS compare to GOTO?

Q: Do you find programs written in CPS style to be readable?

### Spaghetti, Complexity, etc., etc.

If a component is *isolated*, then, we don't care - can't care - if it uses mutable state, or, is complex, or, is coded in a non-structured manner.

### ICs - Integrated Circuits

Electronics ICs are built using oxides (rust).

We run software on top of various oxides.

When we pull out a 7400 chip out of a circuit and replace it with a 7400 from another manufacturer, do we care what variation of oxide the other manufacturer used?

### Homebrew NMOS Transistor Step by Step - So Easy Even Jeri Can Do It

Consider this video:

[Homebrew NMOS Transistor Step by Step - So Easy Even Jeri Can Do It](https://www.youtube.com/watch?v=w*znRopGtbE).


Q: Does Jeri's NMOS transistor use immutable state?  

Q: Does Jeri's NMOS transitor use ownership?  

Q: Do you care?

Q: Do your answers change if Jeri were to build a CPU instead of single transistor?

## Referential Transparency

Referential Transparency refers to the idea that one Component can replace another Component.

Q: What is the base minimum required for Referential Transparency?  Pick only one, the most important one:
- Immutable State  
- Ownership  
- Isolation

In Hardware Design (e.g. TTL), "Referential Transparency" is called by a different name - "pin-for-pin replacement".

 





