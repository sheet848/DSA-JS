```Javascript

class LinkedList {
	delete(value) {
        if (!this.head) {
            console.log("List is empty");
            return;
        }

        // If the head node is to be deleted
        if (this.head.value === value) {
            this.head = this.head.next;
            return;
        }

        let current = this.head;
        while (current.next && current.next.value !== value) {
            current = current.next;
        }

        if (current.next) {
            current.next = current.next.next;
        } else {
            console.log("Value not found in the list");
        }
    }

}
```