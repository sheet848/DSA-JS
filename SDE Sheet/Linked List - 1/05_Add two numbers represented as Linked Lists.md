**Problem Statement**: Given the **heads** of two non-empty linked lists representing two non-negative integers. The digits are stored in **reverse order**, and each of their nodes contains a single digit. Add the two numbers and return the **sum** as a linked list.

**Examples**:

**Input Format**: 
(Pointer/Access to the head of the two linked lists)

num1  = 243, num2 = 564

l1 = [2,4,3]
l2 = [5,6,4]

**Result**: sum = 807; L = [7,0,8]

**Explanation**: Since the digits are stored in reverse order, reverse the numbers first to get the or                                                original number and then add them as → 342 + 465 = 807. _**Refer to the image below.**_

Adding two numbers represented as linked lists involves simulating the addition digit by digit, just like adding numbers manually. Here's the JavaScript implementation:

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

    // Function to append a node to the list
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

// Function to add two numbers represented as linked lists
function addTwoNumbers(list1, list2) {
    let p1 = list1.head;
    let p2 = list2.head;
    let carry = 0;
    const result = new LinkedList();

    while (p1 || p2 || carry) {
        const val1 = p1 ? p1.value : 0;
        const val2 = p2 ? p2.value : 0;

        const sum = val1 + val2 + carry;
        carry = Math.floor(sum / 10);
        const digit = sum % 10;

        result.append(digit);

        if (p1) p1 = p1.next;
        if (p2) p2 = p2.next;
    }

    return result;
}

// Example usage:
const list1 = new LinkedList();
list1.append(2);
list1.append(4);
list1.append(3); // Represents the number 342

const list2 = new LinkedList();
list2.append(5);
list2.append(6);
list2.append(4); // Represents the number 465

console.log("List 1:");
list1.display();

console.log("List 2:");
list2.display();

const result = addTwoNumbers(list1, list2);
console.log("Sum:");
result.display();
```

### Explanation:

1. **Nodes Represent Digits**: Each node in the linked list represents a digit, with the least significant digit (ones place) at the head.
2. **Digit-by-Digit Addition**: The values of corresponding nodes are added, along with any carry from the previous digit. If one list is shorter, treat missing values as 0.
3. **Carry Handling**: Any carry-over from addition is propagated to the next digit, and a new node is created for each sum.
4. **Result**: The final linked list represents the sum, with the least significant digit at the head.

This implementation handles carry propagation and different-length lists effectively. Let me know if you'd like further assistance!