# Week 2: Iterators

## Goal
Allow client to go through elements of clients but not to know structure and representation of the stack.

## `Iterable`
A class which has a method which returns an `Iterator`. An `Iterator` has methods `hasNext()` and `next()`.

longhand:
```java
Iterator<String> i = stack.iterator();
while(i.hasNext()){
	String s = i.next();
	System.out.println(s);
}
```

shorthand (yay!):
```java
for (String s: stack){
	System.out.println(s);
}
```

## Linked-list implementation
```java
import java.util.Iterator;
public class Stack<Item> implements Iterable<Item>{
	//...
	public Iterator<Item> iterator() {
		return new ListIterator();
	}
	public class ListIterator implements Iterator<Item>{
		private Node current = first;
		public boolean hasNext(){
			return current != null;
		}
		public void remove(){	
			// no supported, throw error
		}
		public Item next(){
			Item item = current.item;
			current = current.next;
			return item;
		}
	}
}
```

## Array implementation
```java
import java.util.Iterator;
public class Stack<Item> implements Iterable<Item>{
	//...
	public Iterator<Item> iterator(){
		return new ReverseArrayIterator();
	}
	public class ReverseArrayIterator implements Iterator<Item>{
		private int i = N;
		public boolean hasNext(){
			return i > 0;
		}
		public void remove(){
			//no supported
		}
		public Item next(){
			return s[--i];
		}
	}
}
```

## Problems
```
Suppose that we copy the iterator code from our linked list and resizing array implementations of a stack to the corresponding implementations of a queue. 

Which queue iterator(s) will correctly return the items in FIFO order?

answer: linked list iterator only
```