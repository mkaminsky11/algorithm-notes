# Week 2: Resizing Arrays

## Problem
In order to implement a stack and queue which do not have a fixed capacity with an array, the array will need to shrink and grow.

## First stry
`push()` increases size by 1
`pop()` decreases by 1

Expensive because array needs to copy to new array.

## Repeated doubling
In order to resize infrequently, when array is full, create  a new array of twice the size.

```java
public ResizingArray(){
	s = new String[1];
	public void push(String item){
		if(N === s.length){
			resize(2 * s.length);
		}
		s[N++] = item;
	}
	public void resize(int capacity){
		String copy = new String[capacity];
		for(int i = 0; i < N; i++){
			copy[i] = s[i];
		}
		s = copy;
	}
}
```

## Shrinking
Don't want to shrink when half full as this will be inefficient when `push()` and `pop()` are alternated when array is full (thrashing).

Instread, half size of array when it is 1/4 full.

## Problems
```
Suppose that, starting from an empty data structure, we perform N push operations in our resizing array implementation of a stack. How many times is the resize() method called?

answer: logarithmic
```