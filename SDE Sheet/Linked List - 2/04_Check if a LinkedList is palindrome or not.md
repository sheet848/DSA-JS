To check if a linked list is a palindrome, you can do it in an efficient manner using the following steps:

1. Find the middle of the linked list.
2. Reverse the second half of the linked list.
3. Compare the first half with the reversed second half.
4. Restore the original order of the list (optional, if needed).

Here’s the JavaScript implementation:

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

    // Function to check if the linked list is a palindrome
    isPalindrome() {
        if (!this.head || !this.head.next) {
            return true; // Empty or single node list is always a palindrome
        }

        // Step 1: Find the middle of the list
        let slow = this.head;
        let fast = this.head;
        while (fast !== null && fast.next !== null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        // Step 2: Reverse the second half of the list
        let prev = null;
        let current = slow;
        while (current) {
            let next = current.next;
            current.next = prev;
            prev = current;
            current = next;
        }
        let secondHalfHead = prev; // The head of the reversed second half

        // Step 3: Compare both halves
        let firstHalfHead = this.head;
        while (secondHalfHead) {
            if (firstHalfHead.value !== secondHalfHead.value) {
                return false; // If mismatch, not a palindrome
            }
            firstHalfHead = firstHalfHead.next;
            secondHalfHead = secondHalfHead.next;
        }

        // The list is a palindrome
        return true;
    }

    // Function to display the list
    display() {
        let current = this.head;
        while (current) {
            process.stdout.write(current.value + " -> ");
            current = current.next;
        }
        console.log("null");
    }
}

// Example usage:
const list = new LinkedList();
list.append(1);
list.append(2);
list.append(2);
list.append(1);

console.log("Linked List:");
list.display();

console.log("Is Palindrome?", list.isPalindrome());
```

### Explanation:

1. **Middle of List**:
    - Use the slow and fast pointer technique to find the middle of the list.
2. **Reverse the Second Half**:
    - Reverse the portion of the list starting from the middle node.
3. **Compare Both Halves**:
    - Compare the first half of the list with the reversed second half. If all nodes match, it's a palindrome.
4. **Restore the Original Order** (Optional):
    - If needed, you can reverse the second half again to restore the original list structure.

This approach runs in **O(n)** time complexity with **O(1)** space complexity. Let me know if you'd like further details!