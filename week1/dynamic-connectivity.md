# Week 1: Dynamic Connectivity

## Union find
Given a set of `N` objects, find if there is a path connecting two objects. `union` connects objects, `connected` checks if connected

```
0  1-2 3-4
5-6  7 | |
       8 9

union(4,3)
union(3,8)
...etc

connected(0,7) -> false
connected(8,9) -> true 
```
Even if not direct connection `8->3->4->9`.

## Assumptions:
+ `p` is connected to `p` (reflexive)
+ if `p->q`, then `q->p` (symmetric)
+ if `p->q` and `q->r`, then `p->r` (transitive)

## Connected components:
```
0 1  2-3
 /   |/|
 4-5 6 7

 {0} {1 4 5} {2 3 6 7}
```
Maximal group which are mutually connected. **find query** checks if in same component, **union command** replaces two components with their union.

```java
public class UF
	UF(int N) //initialize (0 to N-1)
	void union(int p, int q) //connect p and q
	boolean connected(int p, int q) //are they in same component
	int find(int p) //component indentifier for p(0 to N-1)
	int count() //number of components
```

## Problems
### 1
```
number of components in: 1-2 3-4 5-6 7-8 7-9 2-8 0-5 1-9

1-2 3-4 5-6 9-7-8

3-4 0-5-6 9-7-8-2-1
          +-------+

answer: 3
```