```Javascript

class LinkedList {
	constructor() {
		this.head = null;
	}

	// addign a new node in linkedlist
	append(value) {
		let newnode = new Node(value);
		if(!this.head) {
			this.head = newnode;
			return;
		}
		let current = this.head;
		while(current.next) {
			current = current.next;
		}
		current.next = newnode;
	}

	//printing LL
	printList() {
		let current = this.head;
		let result = "";
		while(current.next) {
			result += current.value + '->';
			current = current.next;
		}
		console.log(result + 'null');
	}
}
```

