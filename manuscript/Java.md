# Java

## Main Takeaways

- Java popularized GC.
- Java popularized the concept of VM - Virtual Machines.

## Anti-Takeaways from Java

- backtrace

## Garbage Collection

Java popularized GC.

Smalltalk made GC accessible.

GC first appeared in Lisp (approx. 1956).

## Backtrace

Backtrace is no better than the core dumps in the mid-1900's.

Backtrace often contains information that is irrelevant to the problem-at-hand.

Backtrace often shows what went wrong inside the underlying technology.  This doesn't help pinpoint the cause(s) of the problem(s) in the problem-at-hand.

Backtraces usually consist of many lines of output.  This, usually, is merely noise that impedes debugging progress.  

One line of informative output should be enough.

It is not enough to give *all* information in an error message (or warning).  Messages that are respectful of the ultimate users of the information, winnow information down and hide the rest of the information.









