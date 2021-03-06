# Week 1: Observations

## Example
given `N` distinct integers, how many triples add to zero?
```
8ints.txt:
8
30 -40 -20 -10 40 0 10 5

java ThreeSum 8ints.txt
4
```

Brute force:
```java
int count = 0;
int N = a.length;
for(int i = 0; i < N; i++){
	for(int j = i+1; j < N; j++){
		for(int k = j+1; k < N; k++){
			if(a[i] + a[j] + a[k] == 0){
				count++;
			}
		}
	}
}
```

## Observing Time
Can observe a stopwatch.
```java
Stopwatch sw = new Stopwatch();
//do stuff
double time = sw.elapsedTime();
```

Brute force is very slow for large data sets.

## Problems
```
Suppose that you make the following observations of the running time T(N) (in seconds) of a program as a function of the input size N. Which of the following functions best models the running time T(N)?

of the running time T(N) (in seconds) of a program as a function of the input size N. Which of the following functions best models the running time T(N)?

N	T(N)
1,000	0.0
2,000	0.0
4,000	0.1
8,000	0.3
16,000	1.3
32,000	5.1
64,000	20.5

answer: 5.0×10−9×N2
```