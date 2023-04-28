

# ORG Charts

## Main Takeaways

- Business organizations are built in a scalable manner.
- Business organizations are described by ORG Charts.


## Trees


ORG Charts are usually expressed as *acyclic trees*[^oc1] that are stricly layered.

[^oc1]: Note that generalized DAGs can "skip over" and layers and weld layers together.  See the Scalability section.  CSE (Common Subexpression Elimination) eliminates shared tree nodes but requires that the nodes be bundled together, decreasing scalability and constraining potential parallelism.  Business organizations are not structured as DAGs but as strict trees.  A counter-example might be a shared mail room, where several departments share the same mail room.  If a tree of business units were to be cleaved off into a separate organization, the shared mail room would need to be cloned.

Managers at higher levels in the ORG Chart pass commands/requirements down to mid-level managers.  Mid-level managers pass commands/requirements down to lower-level managers and so on until the commands reach the bottom (leaves) of the tree.

Mid-level managers "report" upwards to higher-level managers providing summaries of activities and eliding details.

In a smooth-running business, no manager - at any level - is swamped by detail.

## Breaking the Tree Structure

Businesses use the phrases "*micro-management*" and "*going over the boss's head*" to describe non-scalable violations of the organization's tree structure.

In software, we call these kinds of violations *graphs* instead of *trees*.

## Scalability

The above structure makes businesses *scalable*.

These same principles can be applied to software design.

For example
- a software architecture is scalable if it is arranged as a tree.
- a software architecture is *not scalable* if it is arranged as a graph or a DAG (with shared nodes at different layers).

## Optimizations

Optimizations often transform tree-like structures into DAG-like structures.

Some optimizations modify code and make code unscalable.





