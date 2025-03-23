
```Javascript

class doublyLinkedList {
	constructor() {
		this.head = null;
		this.tail = null;
	}

	addItem(value) {
		const newNode = new Node(data);
	    if (!this.head) {
		    this.head = newNode;
		    this.tail = this.head;
	    } else {
		    this.tail.next = newNode;
		    newNode.prev = this.tail;
		    this.tail = newNode;
	    }
	    this.length++;
	    return this;
	}

	isEmpty() {
		if(this.head === null) {
			return true;
		}
		return false;
	}

	display() {
		if(!this.isEmpty()) {
			let current = this.head;

			while(current !== null) {
				console.log(current.data);
				current  current.next;
			}
		}
	}
	
}
```