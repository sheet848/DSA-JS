**Example 1:**
**Input:**
 Linked list: [1,4,2,3]
       Node = 2
**Output:**
Linked list: [1,4,3]
**Explanation:** Access is given to node 2. After deleting nodes, the linked list will be modified to [1,4,3].

**Example 2:**
**Input:**
 Linked list: [1,2,3,4]
       Node = 1
**Output:** Linked list: [2,3,4]
**Explanation:**
 Access is given to node 1. After deleting nodes, the linked list will be modified to [2,3,4].

# Solution

To delete a given node in a linked list in **O(1)** time complexity, you can achieve this by copying the value of the next node into the given node and then bypassing the next node. Here's the implementation in JavaScript:

```javascript
class Node {
    constructor(value) {
        this.value = value;
        this.next = null;
    }
}

// Function to delete a given node (O(1) approach)
function deleteNode(node) {
    if (node === null || node.next === null) {
        console.log("Node cannot be deleted using this method");
        return;
    }

    // Copy the value of the next node to the current node
    node.value = node.next.value;

    // Remove the next node
    node.next = node.next.next;
}

// Example usage:
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

const list = new LinkedList();
list.append(1);
list.append(2);
list.append(3);
list.append(4);
console.log("Original List:");
list.display();

// Assume we want to delete the node with value 2
let nodeToDelete = list.head.next; // Node with value 2
deleteNode(nodeToDelete);

console.log("After Deleting Node:");
list.display();
```

### Explanation:

1. **Why O(1)?**:
    
    - Normally, deleting a node in a singly linked list requires traversing the list to find the previous node. But in this approach, we skip that traversal.
    - By copying the value and the `next` reference of the next node into the current node, we "delete" the current node in constant time.
2. **Limitation**:
    
    - This approach works only if the given node is not the tail (last node), as there is no next node to copy from.

Let me know if you'd like further clarification or enhancements!