# Week 1: Mathematical Models

## Tilde notation
Simplify costs to `N` becasue everything else becomes almost irrelevant when `N` is large.

```
frequency | tilde notation
----------+---------------
N + 2           ~N
0.5(N + 1)     ~0.5N
(N+1)(N+2)     ~N^2
```

## Problems
```
How many array accesses does the following code fragment make as a function of N? (Assume the compiler does not optimize away any array accesses in the innermost loop.)

                        int sum = 0;
                        for (int i = 0; i < N; i++)
                            for (int j = i+1; j < N; j++)
                                for (int k = 1; k < N; k = k*2)
                                    if (a[i] + a[j] >= a[k]) sum++;

answer: ~3/2 N^2 lg N
```