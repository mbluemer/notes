# Architectural Styles and the Design of Network-based Software Architectures
by Roy Thomas Fielding (2000)

## 1 | Software Architecture

### 1.1 | Run-time Abstraction

A *software architecture* is an abstraction of the run-time elements of a software system during some phase of its operation.
- Each level of abstraction has its own architecture
- Architecture may change during various operational phases
- It's key to note that architectural design and source code structure are separate design activities even though closely related

### 1.2 | Elements

The architecture is defined by a configuration of elements that are constrained in their relationship in order to achieved desired architectural properties.

It'd dangerous to consider documentation to be part of the architecture because, just like building architecture, the physical elements live a life disembodied from the original rationale.

The various element types are *components* that perform transformations on data, *data* that contains the information to be used and transformed, and *connectors* to hold together various parts of the architecture.
