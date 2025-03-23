```Javascript

class LinkedList {
	reverseDLL() {
	    let current = this.head;
	    let temp;
	    while (current) {
	      temp = current.prev;
	      current.prev = current.next;
	      current.next = temp;
	      current = current.prev;
	    }
    [this.head, this.tail] = [this.tail, this.head];
  }
}

```