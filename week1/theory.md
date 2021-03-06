# Week 1: Theory of Algorithms

## Types of analysis
Bounds on costs:
**Best case** is "easiest" input and provides a goal for all inputs
**Worst case** provides a guarantee for all inputs

### Example
Array access for brute-force 3-sum:
**Best**: `~1/2 N^3`
**Average**: `~1/2 N^3`
**Worst**: `~1/2 N^3`

Binary search:
**Best**: `~1` (find it right away)
**Average**: `~ lg N`
**Worst**: `~ lg N`

## Optimal algorithm
Can provide a performance guarantee and no algorithm can provide a better performance guarantee.

## Notations
**Big theta**: classify
**Big Oh**: develop upper bounds (`theta(N^2)` and smaller)
**Big Omega**: develop lower bounds (`theta(N^2)` and larger)