**Example 1:***
**Input:** List1: 2 4 8 10, 
List2: 1 3 3 6 11 14

**Output:** Combined List: 1 2 3 3 6 8 10 11 14

**Explanation:** The values in the first list are [2, 4, 8, 10] and in the second list are [1, 3, 3, 6, 11, 14], when combined and sorted give us [1, 2, 3, 3, 6, 8, 10, 11, 14].

**Example 2:**
**Input:**
List1: 7 8, 
List2: 1 3 4 6

**Output:** 1 3 4 6 7 8

**Explanation:** The values in the first list are [7. 8] and in the second list are [1, 3, 4, 6], when combined and sorted give us [1, 3, 4, 6, 7, 8].

# Solution

To merge two sorted linked lists, you can create a function that merges them into a single sorted linked list. Here's how you can implement this in JavaScript:

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

// Function to merge two sorted linked lists
function mergeSortedLists(list1, list2) {
    let dummy = new Node(0); // Temporary dummy node
    let current = dummy;

    let p1 = list1.head;
    let p2 = list2.head;

    while (p1 && p2) {
        if (p1.value < p2.value) {
            current.next = p1;
            p1 = p1.next;
        } else {
            current.next = p2;
            p2 = p2.next;
        }
        current = current.next;
    }

    // Attach any remaining nodes
    if (p1) {
        current.next = p1;
    }

    if (p2) {
        current.next = p2;
    }

    const mergedList = new LinkedList();
    mergedList.head = dummy.next; // Skip the dummy node
    return mergedList;
}

// Example usage:
const list1 = new LinkedList();
list1.append(1);
list1.append(3);
list1.append(5);

const list2 = new LinkedList();
list2.append(2);
list2.append(4);
list2.append(6);

console.log("List 1:");
list1.display();

console.log("List 2:");
list2.display();

const mergedList = mergeSortedLists(list1, list2);
console.log("Merged List:");
mergedList.display();
```

### Explanation:

1. **Dummy Node**: A temporary node is used to simplify appending nodes to the merged list.
2. **Two Pointers**: Pointers `p1` and `p2` traverse the two input lists, selecting the smaller value at each step.
3. **Remaining Nodes**: After one list is fully traversed, any remaining nodes from the other list are appended to the merged list.
4. **Result**: The merged list is returned as a new `LinkedList`.

This algorithm has a time complexity of **O(n + m)**, where `n` and `m` are the lengths of the two lists. Let me know if you'd like help with testing or optimizing this further!