```Javascript

class LinkedList {
	function searchKey (head, key) {
		let current = head;

		while ( current !== null) {
			if(current.data === key) {
				return true;
			}
			current = current.next;
		}

		return false;
	}
}
```