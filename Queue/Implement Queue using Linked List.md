# Implement Queue using Linked List
- In a Queue using a Linked List, each element (node) contains a value and a reference to the next node. 
- The queue follows the FIFO (First In, First Out) principle, with enqueue operations adding to the rear and dequeue operations removing from the front.

## Why This Implementation of Queue Using Linked List is More Efficient than Array Implementation of Queue in JavaScript?

Implementing a queue using a linked list is often more efficient than using an array in JavaScript because:

1. Adding or removing elements at the beginning or end of a linked list is O(1) (constant time). With arrays, adding/removing at the beginning is O(n) (linear time) because elements need to be shifted.
2. Memory is allocated only when a new element is added. There’s no unused memory.
3. If the queue size is smaller than the array capacity, memory is wasted. If the queue grows, resizing the array can also lead to temporary memory inefficiency.

```
class Node {
    constructor(data) {
        this.data = data;
        this.next = null;
    }
}

class Queue {
    constructor() {
        this.front = null;  
        this.rear = null; 
        this.size = 0; 
    }
    enqueue(data) {
        const newNode = new Node(data);
        if (this.isEmpty()) {
            this.front = newNode;
            this.rear = newNode;
        } else {
            this.rear.next = newNode;
            this.rear = newNode;
        }
        this.size++;
    }
    dequeue() {
        if (this.isEmpty()) {
            return null; 
        }
        const removedNode = this.front;
        this.front = this.front.next;
        if (this.front === null) {
            this.rear = null;
        }
        this.size--;
        return removedNode.data;
    }
    peek() {
        if (this.isEmpty()) {
            return null;
        }
        return this.front.data;
    }
    isEmpty() {
        return this.size === 0;
    }
    getSize() {
        return this.size;
    }
    print() {
        let current = this.front;
        const elements = [];
        while (current) {
            elements.push(current.data);
            current = current.next;
        }
        console.log(elements.join(' -> '));
    }
}

// Example Usage:
const queue = new Queue();
queue.enqueue(10);
queue.enqueue(20);
queue.enqueue(30);
queue.print(); 

console.log(queue.dequeue());
queue.print();

console.log(queue.peek()); 
console.log(queue.getSize());
console.log(queue.isEmpty());
```

### Output
```
10 -> 20 -> 30
10
20 -> 30
20
2
false
```

****Time complexity:**** 
All operations in the Linked list implementation of Queue (enqueue, dequeue, peek, isEmpty, isFull, getSize) have ****O(1)**** time complexity.  

****Auxiliary Space:**** O(n)
