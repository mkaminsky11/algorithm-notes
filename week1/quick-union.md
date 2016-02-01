# Week 1: Quick Union

## Date structure
Quick find is too slow. Quick union is a "lazy approach"(doesn't load anything until it has to).

Instead of 1 array, `id[i]` is the parent of `i`, and can have a "forest".
```
root of i is : id[id[id[...id[i]...]]

9
|\
2 4
  |
  3

element: 0 1 2 3 4 5 6 7 8 9
id[]:        9 4 9
               | |
              parents
root:        9 9 9
```

## Problem
```
elements: 0 1 2 3 4 5 6 7 8 9
id[]:     0 9 6 5 4 2 6 1 0 5

find roots of 3 and 7
3->5->2->6->6 (root is 6 since goes to self)
7->1->9->5->2->6 (6)

answer: 6 and 6
```

## Date structure (cont.)
`find` command checks if `p` and `q` have the same root. The `union` command change's the `id` of `p`s root to `id` of `q`s root.


```java
public class QuickUnionUF{
	private int id[];
	public QuickUnionUF(int N){
		id = new int[N];
		for(int i = 0; i < N; i++){
			id[i] = i;
		}
	}

	private int root(int i){
		if(id[i] == i){
			return i;
		}
		return root(id[i]);

		//
		//or
		//

		while(i != id[i]){
			i = id[i];
		}
		return i;
	}

	public boolean connected(int p, int q){
		return root(p) == root(q);
	}

	public void union(int p, int q){
		int i = root(p);
		int j = root(q);
		id[i] = j;
	}
}
```

## Performance
Trees can get tall and the `find` command can get very expensive (up to `N`).

## Problems
```
what is the maximum number of array accesses during the find operation when using the quick-union structure on N elements?

answer: linear (N)
```