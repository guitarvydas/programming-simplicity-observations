# Astronomy and Cosmology

## Main Takeaway

- epicycles

## Epicycles

Much Accidental Complexity is due to *epicycles* - reparing symptoms instead of addressing fundamental problem(s).

## Code Bloat

Code bloat comes from trying to extend fundamentally small systems to handle all cases, then fixing epicycles (aka accidental complexity) as problems are discovered, then fixing epicycles caused by fixes to the previous epicycles, and so on ...

A solution to this kind of problem is to assume that *one* notation does not need to handle *all* cases.  Switch notations, compose solutions by snapping solutions together.

## Examples

### FP - Functional Programming

Functional Programming is a good notation for creating complicated calculators.  

### StateCharts

StateCharts are a good notation for creating sequencers.  

### Blockchain

Blockchain consists of 2 main technologies
1. cryptography
2. distributed state machines (for time-scrambling the group-derived solutions).

#### Implementing Blockchain

Create specific - but partial - solutions using appropriate notations and isolate those partial solutions. 

Use FP for (1) and StateCharts for (2).

Put each solution into a process.

Create a coordinator process that sequences the partial solutions.

Use IPC, pipes, internet, etc. to have the partial solutions communicate with the coordinator (not with each other).

## See Also

[The Sleepwalkers](https://en.wikipedia.org/wiki/The_Sleepwalkers_(Koestler_book))
[StateCharts](https://guitarvydas.github.io/2020/12/09/StateCharts.html)
[StateCharts 2](https://guitarvydas.github.io/2021/02/25/statecharts-(again).html)
