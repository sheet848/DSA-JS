**Example 1:**

**Input Format:** 5->1->2, N=2
**Result**: 5->2

**Explanation**: The 2nd node from the end of the linked list is 1. Therefore, we get this result after removing 1 from the linked list.

**Example 2:**

**Input Format:** 1->2->3->4->5, N=3
**Result**: 1->2->4->5

**Explanation**: The 3rd node from the end is 3, therefore, we remove 3 from the linked list.

To remove the N-th node from the end of a singly linked list in an optimal way, we can use the **two-pointer technique**. Here's the implementation in JavaScript:

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

    // Function to remove the N-th node from the end
    removeNthFromEnd(n) {
        let dummy = new Node(0);
        dummy.next = this.head;
        let slow = dummy;
        let fast = dummy;

        // Move fast pointer n steps ahead
        for (let i = 0; i < n; i++) {
            if (fast.next === null) {
                console.log("N is greater than the length of the list");
                return;
            }
            fast = fast.next;
        }

        // Move both pointers until fast reaches the end
        while (fast.next !== null) {
            slow = slow.next;
            fast = fast.next;
        }

        // Remove the N-th node
        slow.next = slow.next.next;

        // Update the head in case the first node was removed
        this.head = dummy.next;
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

list.removeNthFromEnd(2); // Removes the 2nd node from the end
console.log("After Removing 2nd Node from End:");
list.display();
```

### Explanation:

1. **Dummy Node**: A dummy node is introduced to simplify edge cases, such as removing the head node.
2. **Two Pointers**: The `fast` pointer is moved `n` steps ahead. Then both `slow` and `fast` pointers move one step at a time until `fast` reaches the end of the list.
3. **Delete Node**: The `slow` pointer stops at the node before the target node, allowing the removal of the N-th node by updating the `next` reference.
4. **Time Complexity**: This solution has a **O(n)** time complexity, as the list is traversed only once.

This is an optimal approach, and it elegantly handles scenarios where `n` equals the length of the list. Let me know if you'd like any additional details!