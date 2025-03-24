To reverse a linked list in groups of size `k`, you can implement a function that processes the list in chunks of `k` nodes and reverses them iteratively or recursively. Here's a JavaScript implementation:

```javascript
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

    // Function to reverse the linked list in groups of size k
    reverseInGroups(k) {
        this.head = this._reverseInGroups(this.head, k);
    }

    _reverseInGroups(head, k) {
        if (!head) return null;

        let current = head;
        let next = null;
        let prev = null;
        let count = 0;

        // Reverse the first k nodes of the list
        while (current !== null && count < k) {
            next = current.next;
            current.next = prev;
            prev = current;
            current = next;
            count++;
        }

        // Recursively reverse the remaining list and connect
        if (next !== null) {
            head.next = this._reverseInGroups(next, k);
        }

        // prev is now the head of the reversed group
        return prev;
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
list.append(6);
list.append(7);
list.append(8);

console.log("Original List:");
list.display();

list.reverseInGroups(3); // Reverse in groups of 3
console.log("Reversed in Groups of 3:");
list.display();
```

### Explanation:

1. **Iterative Reversal**:
    - Reverse the first `k` nodes using a while loop.
    - Track the next group using the `next` pointer.
2. **Recursion for Remaining Groups**:
    - After reversing the first group, recursively reverse the rest of the list.
    - Connect the current group's tail (`head.next`) to the new head of the next group.
3. **Time Complexity**:
    - The function processes each node exactly once, resulting in **O(n)** time complexity.
4. **Space Complexity**:
    - The space complexity is **O(n/k)** due to recursive calls (one for each group).

Let me know if you'd like me to elaborate further or assist with testing this!