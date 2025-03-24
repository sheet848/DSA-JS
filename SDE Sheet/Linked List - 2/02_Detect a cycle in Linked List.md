**Example 1:**

**Input Format**:

LL: 1 2 3 4 5
**Result**: True

**Explanation**: The last node with the value of 5 has its 'next' pointer pointing back to a previous node with the value of 3. This has resulted in a loop, hence we return true.

**Example 2:**

**Input Format:**
LL: 1 2 3 4 9 9
**Result:** False

**Explanation**: : In this example, the linked list does not have a loop hence returns false.

# Optimal Solution

To detect a cycle in a linked list, you can use Floyd's Cycle Detection Algorithm, also known as the **two-pointer technique** (slow and fast pointers). This is an efficient approach with **O(n)** time complexity and **O(1)** space complexity.

Here's the JavaScript implementation:

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

    // Function to detect a cycle in the linked list
    detectCycle() {
        let slow = this.head;
        let fast = this.head;

        while (fast && fast.next) {
            slow = slow.next; // Move slow pointer by 1 step
            fast = fast.next.next; // Move fast pointer by 2 steps

            // If slow and fast pointers meet, there's a cycle
            if (slow === fast) {
                return true;
            }
        }

        return false; // No cycle detected
    }
}

// Example usage:
const list = new LinkedList();
list.append(1);
list.append(2);
list.append(3);
list.append(4);

// Create a cycle for testing
list.head.next.next.next.next = list.head.next; // Node with value 2 points back

console.log("Does the linked list have a cycle?", list.detectCycle());
```

### Explanation:

1. **Two Pointers**:
    - Use two pointers: `slow` moves one step at a time, and `fast` moves two steps at a time.
2. **Cycle Detection**:
    - If there is no cycle, the `fast` pointer will eventually reach the end (`null`).
    - If there is a cycle, the `slow` and `fast` pointers will eventually meet.
3. **Time and Space Complexity**:
    - **Time Complexity**: O(n), as we traverse the list.
    - **Space Complexity**: O(1), as no extra space is used.

This method is efficient and widely used for detecting cycles. Let me know if you'd like help understanding this or need further assistance!