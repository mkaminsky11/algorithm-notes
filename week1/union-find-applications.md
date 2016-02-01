# Week 1: Union Find Applications

## Uses
Games, image processing (understanding how to label areas), physics, etc.

## Percolation
A model for physical systems with an `N` by `N` grid of "sites". System "percolates" if and only if top and bottom are connected by open sites.

real-world examples:

| model | system | vacant site | occupied site | percolates |
| ----- | ------ | ----------- | ------------- | ---------- |
electricity | material | conductor | insulated | conducts
fluid flow | material | empty | blocked | porous 

1. create an object for each site and name them `0` to `N^2 - 1`
2. sites are in the same component if connected by open sites
3. percolates if and only iff any site on bottom row is connected to site on top row (`connected()`)

__trick__: introduce 2 virtual sites and connections to top and bottom. Percolates if and only if top and bottom virtual sites connected.