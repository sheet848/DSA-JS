# Heap
A Heap is a special ****Tree-based Data Structure**** that has the following properties.

- It is a complete [Complete Binary Tree](https://www.geeksforgeeks.org/complete-binary-tree/).
- It either follows max heap or min heap property.

A [****Min-Heap****](https://www.geeksforgeeks.org/introduction-to-min-heap-data-structure/) is a complete binary tree in which the value in each node is smaller than all of its descendants.

****A**** [****Max-Heap****](https://www.geeksforgeeks.org/introduction-to-max-heap-data-structure/) is a complete binary in which root node must be the greatest among all its descendant nodes and the same thing must be done for its left and right sub-tree also.

## Min Heap

Mapping the elements of a heap into an array is trivial: if a node is stored an index k, then its left child is stored at index 2k + 1 and its right child at index 2k + 2.

### How is Min Heap represented?
Let us go through the representation of Min heap. So basically Min Heap is a complete binary tree. A Min heap is typically represented as an array. The root element will be at Arr[0]. For any ith node, i.e., ****Arr[i]**** 

> - ****Arr[(i -1) / 2]**** returns its parent node.
> - ****Arr[(2 * i) + 1]**** returns its left child node.
> - ****Arr[(2 * i) + 2]**** returns its right child node.

### Operations of Heap Data Structure

- ****Heapify:**** a process of creating a heap from an array.
- ****Insertion:**** process to insert an element in existing heap time complexity O(log N).
- ****Deletion:**** deleting the top element of the heap or the highest priority element, and then organizing the heap and returning the element with time complexity O(log N).
- ****Peek:**** to check or find the most prior element in the heap, (max or min element for max and min heap).

## Max Heap
A [****max-heap****](https://www.geeksforgeeks.org/introduction-to-max-heap-data-structure/) is a [complete binary tree](https://www.geeksforgeeks.org/complete-binary-tree/) in which the value in each node is greater than the values in the descendant nodes.

Mapping the elements of a heap into an array is trivial: if a node is stored at index k, then its left child is stored at index 2k + 1 and its right child at index 2k + 2.

### How is Max Heap represented?
A-Max Heap is a Complete Binary Tree. A-Max heap is typically represented as an array. The root element will be at Arr[0]. Below table shows indexes of other nodes for the ****ith**** node, i.e., Arr[i]: 

> __Arr[(i-1)/2] Returns the parent node.__   
> __Arr[(2*i)+1] Returns the left child node.__   
> __Arr[(2*i)+2] Returns the right child node.__

### Operations of Heap Data Structure:

- ****Heapify:**** a process of creating a heap from an array.
- ****Insertion:**** process to insert an element in existing heap time complexity O(log N).
- ****Deletion:**** deleting the top element of the heap or the highest priority element, and then organizing the heap and returning the element with time complexity O(log N).
- ****Peek:**** to check or find the most prior element in the heap, (max or min element for max and min heap).
