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

    // Function to reverse the linked list
    reverse() {
        let prev = null;
        let current = this.head;
        let next = null;

        while (current) {
            next = current.next; // Store the next node
            current.next = prev; // Reverse the current node's pointer
            prev = current; // Move prev and current one step forward
            current = next;
        }
        this.head = prev; // Update head to the new head
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

console.log("Original List:");

list.display();

list.reverse();

console.log("Reversed List:");

list.display();
```

