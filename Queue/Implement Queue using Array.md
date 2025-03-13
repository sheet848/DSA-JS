# Implement Queue using Array
```
class Queue {
  constructor() {
    this.items = [];
  }

  enqueue(element) {
    this.items.push(element); 
  }

  dequeue() {
    return this.isEmpty() ? "Queue is empty" : this.items.shift();
  }

  peek() {
    return this.isEmpty() ? "Queue is empty" : this.items[0];
  }

  isEmpty() {
    return this.items.length === 0;
  }

  size() {
    return this.items.length;
  }

  print() {
    console.log(this.items.join(" -> "));
  }
}

// Example usage:
const queue = new Queue();
queue.enqueue(1);
queue.enqueue(2);
queue.enqueue(3);
queue.print();
console.log(queue.dequeue());
console.log(queue.peek()); 
console.log(queue.size());
```

### Output
```
1 -> 2 -> 3
1
2
2
```

### Time complexity:

- ****enqueue()**** – O(1): Constant time to add an element.
- ****dequeue()-**** O(n): Linear time due to shifting elements.
- ****peek()-**** O(1): Constant time to access the first element.
- ****isEmpty()-**** O(1): Constant time to check if the array is empty.
- ****size()**** – O(1): Constant time to return the size.
- ****print()**** – O(n): Linear time to join and print elements.

****Auxiliary Space:**** O(1)
