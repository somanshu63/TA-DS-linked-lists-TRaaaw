- Create a class named `Node` that is responsible for storing the value and a reference to the next node.
- Create another class named `LinkedList` that will manage multiple nodes and will do operations like adding, removing, searching etc. This class will accept one parameter the head(initial) value that will be the first value of the linked list. If the user doesn't pass the first value default to `null`

- Make sure to add the following methods in the `LinkedList` class.

  - `insertHead`
    It will add the new node to the beginning of the linked list.

  - `removeHead`
    It will remove the new node to the beginning of the linked list.

  - `forEach`
    This method on linked list will behave similar to `Array.forEach`. It will accept a callback function and will execute the callback function will the value of each node.

  - `printAll`
    Calling this method on linked list will print the values of all nodes together in a string. Where the values will be separated by comma. Like ` 1, 3, 4, 5`

  - `size`
    It will be a getter method that will return the length of the linked list.

  - `find`
    It will accept a callback function and return the first value which matched the condition in callback function. If no value matched the condition return `-1`.

- Additions Methods:

  - `insertTail`
    It will add the new node at the end of the linked list.

  - `removeTail`
    It will remove the new node at the end of the linked list.

```js
// Your code goes here

class Node {
  constructor(value) {
    this.next = null;
    this.value = value;
  }
}

class LinkedList {
  constructor(firstValue = null) {
    this.head = firstValue ? new Node(firstValue) : firstValue;
    this.tail = this.head;
  }
  insertHead(value) {
    let node = new Node(value);
    if (!this.head) {
      this.head = this.tail = node;
      return node;
    }
    node.next = this.head;
    this.head = node;
    return node;
  }
  insertTail(value) {
    let node = new Node(value);
    if (!this.tail) {
      this.head = this.tail = node;
      return node;
    }
    this.tail.next = node;
    this.tail = node;
    return node;
  }
  removeHead() {
    if (!this.head) {
      alert(`There is not items in the linked list`);
      return;
    }
    let nodeToRemove = this.head;
    this.head = nodeToRemove.next;
    return nodeToRemove;
  }

  forEach(cb) {
    let current = this.head;
    while (current) {
      cb(current.value);
      current = current.next;
    }
  }
  printAll() {
    this.forEach(console.log);
  }
  size() {
    let length = 0;
    let current = this.head;
    while (current) {
      ++length;
      current = current.next;
    }
    return length;
  }
  find(cb) {
    let current = this.head;
    while (current) {
      if (cb(current.value)) {
        return current.value;
      }
      current = current.next;
    }
    return -1;
  }

  findPrevNode(node) {
    if (!node) {
      return null;
    }
    if (node === this.head) {
      return null;
    }
    let current = this.head;
    while (current) {
      if (current.next === node) {
        break;
      }
      current = current.next;
    }
    return current;
  }
  removeTail() {
    if (!this.tail) {
      alert(`There is not items in the linked list`);
      return;
    }
    let nodeToRemove = this.tail;
    this.tail = this.findPrevNode(this.tail);

    if (this.tail) {
      this.tail.next = null;
    }
    if (nodeToRemove === this.head) {
      this.head = null;
    }

    return nodeToRemove;
  }
}

// Test
let list = new LinkedList(10);
list.insertHead(9);
list.insertHead(8);
list.insertTail(11);
list.insertTail(12);
list.printAll(); // 8 9 10 11 12
list.forEach(alert); // alerts 8 9 10 11 12 one after another
console.log(list.size()); // 5
list.removeHead();
console.log(list.size()); // 4
list.printAll(); // 9 10 11 12
list.removeTail();
console.log(list.size()); // 3
list.printAll(); // 9 10 11
console.log(list.find((v) => v > 10)); // 11
console.log(list.find((v) => v > 100)); // -1
```
