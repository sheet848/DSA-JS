**Example 1:****Input:** LL: 1  2  3  4  5 

**Output:** 3
**Explanation:** Node with value 3 is the middle node of this linked list.

**Example 2:****Input:** LL: 1  2  3  4  5  6

**Output:** 4
**Explanation: ** In this example, the linked list has an even number of nodes hence we return the second middle node which is 4.

# Tortoise and Hare Algorithm

```Javascript

class Node {
    constructor(value) {
        this.value = value;
        this.next = null;
    }
}

class LinkedList {
    constructor() {
        this.head = null;
    }
    
    // Function to add a node to the list
    append(value) {
        const newNode = new Node(value);
        if (!this.head) {
            this.head = newNode;
            return;
        }

        let current = this.head;

        while (current.next) {
            current = current.next;
        }
        current.next = newNode;
    }

    // Function to find the middle element of the list

    findMiddle() {
        let slow = this.head;
        let fast = this.head;

        while (fast !== null && fast.next !== null) {
            slow = slow.next; // Slow pointer moves one step
            fast = fast.next.next; // Fast pointer moves two steps
        }
        return slow ? slow.value : null; // Return the middle node's value
    }

    // Function to display the list
    display() {
        let current = this.head;
        while (current) {
            console.log(current.value + " -> ");
            current = current.next;
        }
        console.log("null");
    }
}

  

// Example usage:

const list = new LinkedList();
list.append(1);
list.append(2);
list.append(3);
list.append(4);
list.append(5);

console.log("Original List:");
list.display();

const middle = list.findMiddle();
console.log("Middle Element:", middle);
```

### Explanation:

1. **Two Pointers**: Use two pointers, `slow` and `fast`.
    - `slow` moves one step at a time.
    - `fast` moves two steps at a time.
2. **Middle Element**: When `fast` reaches the end of the list, `slow` will be at the middle element.

This technique is efficient with a time complexity of **O(n)** and doesn't require additional storage. If the number of nodes is even, this will return the second middle node. Let me know if you'd like to expand or modify this!