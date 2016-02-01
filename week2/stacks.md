# Week 2: Stacks

## Fundamental data types
Value: collation of objects. It has operations `insert`, `remove`, `iterate` and a test if empty.

When removing an item in a **stack**, remove the most recently added.
+ `push` to add, `pop` to remove
+ LIFO = "last in first out"

In an **queue**, remove the least recently added
+ `inqueue` and `dequeue`
+ FIFO = "first in first out"

## Stack API
```java
public class StackOfStrings
	StackOfStrings() //create empty
	void push(String item)
	String pop() //return most recently added and remove it
	boolean isEmpty()
	int size()
```

To read strings into stack
```java
public static void main(String[] args){
	StackOfStrings stack = new StackOfStrings();
	while(!StdIn.isEmpty()){
		String s= StdIn.readString();
		stack.push(s);
	}
}
```

## Linked-list representation
Maintain pointer to the first node in a linked list and insert/remove from the front.

Nodes have strings in them and references to next item.
```java
private class Node{
	String item;
	Node next;
}
```
### `pop`
Saving item to return: `String item = first.item`
Delete first node: `first = first.next`
Return saved item: `return item`

### `push`
Save a link to the list: `Node oldFirst = first`
Create new node: `first = new Node()`
set the instance variables: `first.item = "whatever string"` `first.next = oldFirst`

### Put it all together
```java
public class LinkedStackOfStrings{
	private Node first = null;
	private class Node{
		String item;
		Node next;
	}

	public boolean isEmpty(){
		return first == null;
	}

	public void push(String item){
		Node oldFirst = first;
		first = new Node9);
		first.item = item;
		first.next = oldFirst;
	}

	public String pop(){
		String item = first.item;
		first = first.next;
		return item;
	}
}
```

## Performance
For linked-list, a stack with `N` takes about `40 N` bytes not including the strings themselves.

## Array stack
Use array `s[]` to store `N` items on a stack. `push` addes new item at `s[N]`, and `pop` removes item from `s[N-1]`. However, will overflow and needs to be resized (__covered later__).

```java
public class ArrayStack{
	private String[] s;
	private int N = 0;

	public ArrayStack(int capacity){
		s = new String[capacity];
	}

	public boolean isEmpty(){
		return N == 0;
	}

	public void push(String item){
		s[N++] = item; //gets item, then increments
		
		//or
		
		s[N] = item;
		N++
	}

	public String pop(){
		return s[--N];

		//or

		String item = s[N];
		N--;
		s[N] = null;
		return item;
	}
}
```

## Problems
```
Given a reference first to the first node of a null-terminated linked list with at least two nodes, what does the code fragment below do?

Node x = first;
while (x.next.next != null) {
	x = x.next;
}
x.next = null;

1-+ x
  2-+ x.next
    3-+ x.next.next
      4-+
        null

2-+ x
  3-+ x.next
    4-+ x.next.next
      null

3-+ x
  4-+ x.next
    null x.next <---x.next.next == null, so stop

x.next = null, so...
3-+ x
  null x.next

answer: since 4 is deleted, this code deletes the last node.
```