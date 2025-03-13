# Implement Stack using Array
- In a stack implementation, we need to do push and pop operations at the same end.
- In an array, we can do both operations at the end of the array (or last element) in O(1) time.

```
class Stack {
  constructor() {
    this.items = []; 
  }

  // Push operation
  push(element) {
    this.items.push(element);
  }

  // Pop operation
  pop() {
    if (this.isEmpty()) {
      return "Stack is empty"; 
    }
    return this.items.pop();
  }

  // Peek operation
  peek() {
    if (this.isEmpty()) {
      return "Stack is empty"; 
    }
    return this.items[this.items.length - 1];
  }

  // isEmpty operation
  isEmpty() {
    return this.items.length === 0;
  }

  // Size operation
  size() {
    return this.items.length;
  }

  // Print the stack 
  print() {
    console.log(this.items);
  }
}

// Example Usage
const stack = new Stack();

stack.push(10);
stack.push(20); 
stack.push(30); 
console.log(stack.peek());
console.log(stack.pop());  
console.log(stack.size()); 
console.log(stack.isEmpty());
stack.print();
```

### Output
```
30
30
2
false
[ 10, 20 ]
```

****Time Complexity****: All operations in the Stack Class ( Push , Pop, Peek, isEmpty, Size,) have O(1) time complexity.  `print Stack()`, which is ****O(n).****  

****Auxiliary Space:**** O(1) for all operations.
