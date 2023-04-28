

# UNIX®

## Main Takeaways

- Isolation
- Coordination Language
- Concurrency
- Pipes

## Anti-Takeaways

- time-sharing
- memory sharing

## Isolation

Isolation means that programs are completely separated from each other and can communicate only over very restricted channels.

In UNIX®, processes are *envelopes* that one can drop *calculators* into.

In UNIX®, garbage collection is performed in a brute-force manner[^unix11] which is more efficient than garbage collection in most modern languages.

[^unix11]: UNIX® uses the *biblical flood* method for garbage collection - wait for a process to die, then wipe the slate clean.

## Coordination Language

PLs have traditionally been restricted to describing synchronous calculators.

Few PLs address the issues of distributed programming.

`/bin/sh` (`&` and `|`) is a DSL for creating higher-level concurrent abstractions.

Distributed programming is, currently, only addressed by second-class, assembler-like operations and libraries.

Unfortunately, UNIX \*sh attempts to avoid the issue of concurrency by force-fitting concurrency into a synchronous mold (called "rendezvous"), instead of providing direct access to concurrency and allowing the Architect to choose the best fit for a particular problem-at-hand.

## PID

PIDs - process ID - are handles to first-class components.

## Concurrency

Concurrency is a programming paradigm.

Parallelism is a tactic.

Parallelism needs to use the concurrent paradigm.

Concurrency is a lifestyle choice.  Parallelism is a greasy hamburger.

## Continuations

Processes are continuation-wannabes.  

UNIX processes (threads) are ad-hoc implementations of continuations and closures, done in C and assembler.

## Dependency Spaghetti

Dependencies make understanding and debugging code harder because of the lack of locality and the lack of structured layers.

Tools that allow programmers to continue using dependencies should be avoided.

UNIX® gave us pipes (good), but UNIX® also gave us *make* (a dependency-eliding band-aid).

## Rendezvous

Rendezvous is an attempt to corral concurrency by making *everything* synchronous.

UNIX® appears to provide concurrency and very convenient inter-process communication (pipes), but then restricts the use of concurrency by hard-wiring rendezvous into the underlying machinery[^u11].

[^u11]: & is used to spawn (fork) a line of script.  This a *tell* that something is wrong with the underlying model.  The model was built under the assumptions that (1) forking is expensive and (2) that asynchrony (concurrency) is more special than synchrony.  Forking is expensive mostly because it needs to create scaffolding to allow the operating system to yank control away from a process at any time.  Yanking control away is expensive, especially if it can occur at random.  Yanking control away violates the principle of locality - processes are allowed to make scheduling decisions (e.g. by using CALL/RETURN) that should only be made by the operating system (i.e. in one, localized place).

## Syntax for Distributed Programming is Minimal

The UNIX shell syntax for distributed programming is muddied by the inclusion of many other features.

This is a lack of "Separation of Concerns"

Shell syntax conflates concurrency issues with string-manipulation issues, shell variables, environment variables, PATH specification, interaction, etc.  Modern shells are a jumble of features.

## Conflation of Programming Languages and O/Ss

UNIX® contains several fundamental advances in programming language features (e.g. `|`, ` &`,  `fork()`, etc).

These programming language advances have, unfortunately, been conflated with Operating Systems and have largely been ignored in programming language designs.

N.B. Function application is not the same as pipelines of isolated components.  Functions send input data (parameters) immediately and immediately invoke the callee.  Pipelines buffer data between components.  Functions use a global variable - The Stack - to pass data between components, and, the callee must share The Stack and execute immediately, while the caller is blocked.  Pipelines, though, require no shared data and allow components to execute at any time.

For a different perspective on the above problems, see, also, [Worlds: Controlling the Scope of Side Effects](http://www.vpri.org/pdf/tr2011001*final*worlds.pdf) and [my thoughts on Worlds](https://guitarvydas.github.io/2021/10/14/Worlds.html).

## Union of Coordination and String Processing and ...

Operating systems are libraries.

Windows, MacOS, Linux are applications.

The *problems* that Windows, MacOS and Linux must solve are *different* from the problems that most apps need to solve.

Not every app should have all of the operating system principles built into it, e.g. not every app needs memory sharing and time-sharing.

Some apps use the concurrent programming paradigm.  This should not mean that they must include all of O/S-style threading.

## Pipes

UNIX popularized pipelines of isolated components.

These advances have been, unfortunately, overlooked due to 
- conflation with heavy technologies, i.e. operating systems
- premature optimization, e.g. the ideas of *isolation* were burned into hardware before they were sufficiently explored, e.g. UNIX® had some useful ideas about *isolation* but these were missed and overshadowed by hardware optimizations (hardware CPUs did not support a shared Stack at first)

Note that *functions* do not fully isolate control flow, hence, pipelines of functions are not the same as UNIX® pipelines.

## Time-Sharing and Memory-Sharing

Techniques for time-sharing and memory-sharing were developed in the mid-1900's based on biases that are no longer true.  

In the mid-1900's, CPUs were expensive and memory was scarce and expensive.

In the 202x's, CPUs and memory are inexpensive, yet we continue to use mid-1900's ideas for developing software.

## See  Also

[Concurrency is not Parallelism](https://www.youtube.com/watch?v=oV9rvDllKEg)