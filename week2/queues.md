# Week 2: Queues

## Queue API
```java
public class QueueOfStrings{
	QueueOfStrings()
	void enqueue(String item)
	String dequeue()
	boolean isEmpty()
	int size()
}
```
Looks like this:
```
++ <-- enqueue()
||
++
||
++
||
++ --> dequeue()
```

## Linked-list queue
Need to maintain 2 pointers, to the first and last item in the list.

```java
public class QueueOfStrings{
	private Node first, last;
	private class Node{
		String item;
		Node next;
	}

	public boolean isEmpty(){
		return first == null;
	}

	public void enqueue(String item){
		Node oldLast = last;
		last = new Node();
		last.item = item;
		last.next = null;
		if(isEmpty()){ first = last; }
		else{ oldLast.next = last; }
	}

	public String dequeue(){
		String item = first.item;
		first = first.next;
		if(isEmpty()){ last = null }
		return item; 
	}
}
```
## Problems
```
Suppose that you implement a queue using a null-terminated singly-linked list, maintaining a reference to the item least recently added (the front of the list) but not maintaining a reference to the item most recently added (the end of the list). What are the worst case running times for enqueue and dequeue?

answer: linear time of enqueue (because it would have to find "last" as it is not stored by iterating thorugh the list), and constant for dequeue.
```