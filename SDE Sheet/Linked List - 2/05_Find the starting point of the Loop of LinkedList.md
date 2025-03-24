To find the starting point of a loop in a linked list, Floyd’s Cycle Detection Algorithm (also called the **two-pointer technique**) can be extended. Here's the step-by-step process and its JavaScript implementation:

### Steps:

1. **Detect the Cycle**:
    - Use a slow pointer and a fast pointer to check for the existence of a cycle.
2. **Find the Meeting Point**:
    - Once the slow and fast pointers meet, it means there’s a cycle.
3. **Locate the Start of the Loop**:
    - Reset one pointer to the head of the linked list while keeping the other at the meeting point. Move both pointers one step at a time until they meet again. The meeting point is the starting node of the loop.

### Implementation:

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

    // Function to find the starting point of the loop
    findLoopStart() {
        let slow = this.head;
        let fast = this.head;

        // Step 1: Detect cycle using slow and fast pointers
        while (fast && fast.next) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow === fast) {
                break; // Cycle detected
            }
        }

        // If no cycle is detected, return null
        if (!fast || !fast.next) {
            return null;
        }

        // Step 2: Find the start of the loop
        slow = this.head; // Reset slow pointer to head
        while (slow !== fast) {
            slow = slow.next;
            fast = fast.next;
        }

        return slow; // This is the starting point of the loop
    }
}

// Example usage:
const list = new LinkedList();
list.append(1);
list.append(2);
list.append(3);
list.append(4);
list.append(5);

// Create a loop for testing
list.head.next.next.next.next = list.head.next; // Node with value 2 forms the loop

const loopStart = list.findLoopStart();
if (loopStart) {
    console.log("The loop starts at node with value:", loopStart.value);
} else {
    console.log("No loop detected");
}
```

### Explanation:

1. **Cycle Detection**:
    - The fast pointer moves two steps while the slow pointer moves one step. If they meet, a cycle exists.
2. **Finding the Start of the Loop**:
    - When a cycle is detected, reset one pointer to the head and move both pointers one step at a time. The point where they meet is the start of the loop.
3. **Time Complexity**:
    - O(n), as the linked list is traversed at most twice.
4. **Space Complexity**:
    - O(1), as no additional space is used.

This method is efficient and reliable. Let me know if you’d like further details or examples!