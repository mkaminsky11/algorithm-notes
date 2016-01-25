# Week 1: Quick Find

## Data structure
An integer `id[]` of size `N` and `p` and `q` are connected if and only if they have the same id.

```
element  0 1 2 3 4 5 6 7 8 9
id[] =   0 1 1 8 8 0 0 1 8 8
               | |       | |
are connected -+-+-------+-+
because have same id
```
To find, check if same id. To merge components containing `p` and `q`, change all elements whose id is `id[p]` to `id[q]` (eager approach).

Initialize to ids equal to element:
```
element 0 1 2 3 ...
id[] =  0 1 2 3 ...
```
...or in java...
```java
public class QuickFindUF{
	private int[] id;
	public QuickFindUF(int N){
		id = new int[N];
		for(int i = 0; i < N; i++){ //N array accesses
			id[i] = i;
		}
	}

	//then find elements

	public boolean connected(int p, int q){
		return id[p] === id[q]; // 2 array accesses
	}

	//join elements
	public void union(int p, int q){
		var pid = id[p];					// 1 access
		var qid = id[q];					// 1 access
		for(int i = 0; i < id.length; i++){ // at most 2N + 2 array accesses
			if(id[i] === pid){            // 2 accesses each time * N accesses
				id[i] = qid;
			}
		}
	}
}
```

## Performance
Initialize is linear (N), union is linear (N), find is constant (1). `N * N * 1 = N^2`, so as N increases, array accesses increase as a quadratic.

This is too slow!

## Problems
```
what is the maximum number of array entries that can change during one union() call?

answer: N - 1
```