```Javascript

class LinkedList {
	function countNodes(head) {
		let count = 0;
		let current = head;

		while(current !== null) {
			count++;
			current = current.next;
		}

		return count;
	}
}

```