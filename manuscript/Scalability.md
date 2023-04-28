

# Scalability

## Main Takeaway

- Scalability requires the lack of dependencies.


## Scalability

Techniques and tools that permit dependencies to exist, or encourage the use of dependencies, inhibit scalability, e.g.

- package managers, npm, etc.
- make

## Isolation

Isolation leads to scalability.

Well-defined and narrow interfaces allow for easier management of scalability[^sc1].

[^sc1]: N.B. This means that elaborate types and large APIs inhibit scalability.  The least elaborate type is *void* (aka *array of bytes*) and the least large API has but a single entry.  This does not mean that elaborate types and APIs cannot be used, but, it only means that elaborate types and APIs need to be layered in a scalable fashion (for example: as pipelines of increasing complexity).







