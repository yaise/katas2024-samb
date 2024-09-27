# ADR foundation

## Status
Accepted

## Context
We must choose how to document our architectural plans for ClearView. This includes how to describe the architectural attributes as well how to depict the software component relationships. 
There are many planning, graphing and visualizing tools which makes this decision non trivial. 

## Decision
We will use the following:
* The C4 design language to describe our architecture.
  * We will cover the first 3 layers: Context, Container and Component.
  * We won't cover Code since it is too specific and ill-defined at this point.

C4 is a well established industry norm and is adaptable to our use case. It was also featured in the Katas introduction, and other successful Kata solutions have used it.

* The architectural traits worksheet to specify and prioritize the architectural attributes (-ilities).

The worksheet is a standard form and was used in previous successful Kata solutions. 

## Consequences
This git repo will contains files adhering to the accepted design formats.