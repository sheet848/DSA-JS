```Javascript

class LinkedList{

	deleteNode(node) {
    if (!node || !node.next || !node.prev) {
      return "Invalid node or node not present in the list";
    }
    node.prev.next = node.next;
    node.next.prev = node.prev;
    node.next = null;
    node.prev = null;
  }
	
}
```
