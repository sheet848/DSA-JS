**Example 1:**
**Input:**
List 1 = [1,3,1,2,4], List 2 = [3,2,4]
**Output:**
2
**Explanation:** Here, both lists intersecting nodes start from node 2.

**Example 2:**
**Input:**
 List1 = [1,2,7], List 2 = [2,8,1]
**Output:**
 Null
**Explanation:** Here, both lists do not intersect and thus no intersection node is present.

Here’s an efficient way to find the intersection point of two linked lists forming a "Y" shape using JavaScript. We'll use the two-pointer technique:

```javascript
class Node {
    constructor(value) {
        this.value = value;
        this.next = null;
    }
}

// Function to find the intersection point of two linked lists
function findIntersection(head1, head2) {
    let pointer1 = head1;
    let pointer2 = head2;

    // Traverse both lists. When a pointer reaches the end of one list, it switches to the other list.
    while (pointer1 !== pointer2) {
        pointer1 = pointer1 ? pointer1.next : head2;
        pointer2 = pointer2 ? pointer2.next : head1;
    }

    // If pointers meet, there is an intersection; otherwise, null is returned.
    return pointer1 ? pointer1.value : null;
}

// Example usage:
const head1 = new Node(1);
head1.next = new Node(2);
head1.next.next = new Node(3);
head1.next.next.next = new Node(4);

const head2 = new Node(5);
head2.next = head1.next.next; // Intersection at node with value 3

console.log("Intersection point:", findIntersection(head1, head2));
```

### Explanation:

1. **Two Pointers**:
    - Start both pointers at the heads of the two lists.
    - Traverse both lists, and when one pointer reaches the end, it switches to the head of the other list.
2. **Cycle Alignment**:
    - This ensures both pointers traverse an equal number of nodes, aligning them at the intersection point if it exists.
3. **Intersection Check**:
    - When the two pointers are equal (i.e., meet), that node is the intersection point.
    - If the pointers don't meet, the lists have no intersection.

This approach works in **O(n + m)** time complexity and uses **O(1)** space. Let me know if you'd like help testing or expanding this further!