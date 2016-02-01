# Week 1: Quick Union Improvements

## Weighting
Modify quick union to avoid tall trees by keeping track of size of each tree and balance by linking root of smaller tree to root of larger tree.
```
quick union:

small tree          large tree
 |            or     |
large tree           small tree

weighted:

large tree
  |
small tree <-- chooses better alternative
```

To implement, change the `union` command:
```java
int i = root(p);
int j = root(q);
if(i == j) return; //already linked
if(sz[i] < sz[j]){  //p is smaller, link to larger
	id[i] = j;      //set as root
	sz[j] += sz[i]; //since elements added, increase size
}
else{ //q is smaller, link to larger
	id[j] = i;
	sz[i] += sz[j];
}
```

## Weighted performance
Depth of any node is at most `lg N`(lg = log base 2).

## Path compression
After getting the `root` of `p`, set `id` of `p` to point to the root, so we don't have to go through the entire tree again to find the root.

To implement, edit `root` function:
```java
private int root(int i){
	while(i != id[i]){  //old code, checks if goes to self
		id[i] = id[id[i]]; //move the root up (NEW!)
		i = id[i]; //old code
	}
	return i;
}
```
## Performance
With path compression and weighting, can make unions and finds with `10^9` objects take 6 seconds instead of 30 years.

## Problems
```
0           8
+-+-+-+-+   |\
| | | | |   7 9
1 2 3 4 5   |
            6

when union(3,6) is applied, which id[] entry changes?

answer: id[8], because its tree is smaller (4 elements) in comparison to 0's tree (6 elements), so it is merged into 0's tree.
```