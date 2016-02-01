# Week 2: Generics

## Problem
What if we want a stack of any type of object (not just Strings). Separate classes for each data type is error-prone and tedious.

## Casting
```java
StackOfObjects s = new StackOfObjects();
Apple a = new Apple();
Orange b = new Orange();
s.push(a);
s.push(b);
a = (Apple) (s.pop()) //runtime error
```

Error-prone if types mismatch.

## Java generics
```java
Stack<Apple> s = new Stack<Apple>();
//     ^----type------------^
Apple a = new Apple();
Orange b = new Orange();
s.push(a);
s.push(b); //ERROR!
a = s.pop();
```

## Implementing
```java
public class Stack<Item>{
	//...
	private class Node{
		Item item;
		Node text;
	}
	//...
	public void push(Item item){
		//...
	}
	//...
	public Item pop(){
		Item item = first.item;
		//...
	}
}
```

For an array, need a hack:
```java
s = (Item[]) new Object[capacity];
```

## Problems
```
Which of the following statements is a type safe way to declare and initialize a Stack of integers?

answer: Stack<Integer> = new Stack<Integer>();
```