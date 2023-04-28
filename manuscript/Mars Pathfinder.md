

# Mars Pathfinder Disaster

## Anti-Takeaway

- fixing the symptom instead of the cause

## Mars Pathfinder Disaster

The [Mars Pathfinder disaster](https://www.rapitasystems.com/blog/what-really-happened-software-mars-pathfinder-spacecraft) caused the Mars Pathfinder software to behave unexpectedly after the unit landed on Mars.

## Priority Inversion

The mis-behaviour was ostensibly caused by "priority inversion".  

This was seen as a bug in the RTOS (realtime operating system).

From my perspective, the bug was due to the problem of pushing a notation beyond its "comfort zone".

Functional notation is appropriate for reasoning about calculators, i.e. synchronous sets of inputs which always cause synchronous sets of outputs.  The simplicity of this paradigm is lost when it is applied to concurrent processes, as witnessed by the accidental complexity that caused priority inversion.

The priority inversion bug was later addressed by the addition of more complexity (priority inheritance) which repaired the immediate problem in the notation, but did not address the deeper problem (that of using a single notation outside of its boundaries of simplicity).

## See Also

See the section on Epicycles (Astronomy, Cosmology)
