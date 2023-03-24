Using the linked list class you created in the previous exercise implement stack and queue:

- Implement Stack using the following methods
  - `add` Adds an element to the stack
  - `remove` Removes an element from the stack
  - `peek` returns the first element from the top of the stack
  - `printAll` print all the elements of the stack from one after another from the top
  - `isEmpty` Returns `true` if the stack is empty

**YOU HAVE TO USE LINKED LIST TO STORE DATA**

```js
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

class Stack {
  constructor() {
    this.store = new LinkedList();
  }
  get length() {
    return this.store.size();
  }
  add(newValue) {
    this.store.insertTail(newValue);
    return this.store.size();
  }
  remove() {
    return this.store.removeTail().value;
  }
  peek() {
    return this.store.tail.value;
  }
  printAll() {
    this.store.printAll();
  }
  isEmpty() {
    return this.store.size() === 0;
  }
}

// Test 1

const stack = new Stack();

stack.add(10);
stack.add(12);
stack.add(120);
stack.add(1);
stack.add(4);

console.log(stack.remove()); // => 4
console.log(stack.length); // => 4
console.log(stack.remove()); // => 1
console.log(stack.length); // => 3

console.log(stack.peek()); // 120

console.log(stack.isEmpty()); // false

console.log(stack.remove()); // => 120

console.log(stack.add(100)); // 3

console.log(stack.peek()); // => 100

console.log(stack.remove()); // => 100
console.log(stack.remove()); // => 12
console.log(stack.remove()); // => 10

console.log(stack.isEmpty()); // true
```

- Implement Queue using the following methods
  - `enqueue` Add the element to the queue
  - `dequeue` Removes an element from the queue
  - `peek` returns the first element from the top of the queue
  - `printAll` print all the elements of the queue from one after another from the top
  - `isEmpty` Returns `true` if the queue is empty

**YOU HAVE TO USE LINKED LIST TO STORE DATA**

```js
class Queue {
  // your code goes here
}

// Test 1

const queue = new Queue();

queue.enqueue(10);
queue.enqueue(12);
queue.enqueue(120);
queue.enqueue(1);
queue.enqueue(4);

console.log(queue.dequeue()); // => 10
console.log(queue.length); // => 4
console.log(queue.dequeue()); // => 12
console.log(queue.length); // => 3

console.log(queue.peek()); // 120

console.log(queue.isEmpty()); // false

console.log(queue.dequeue()); // => 120

console.log(queue.peek()); // => 1

console.log(queue.dequeue()); // => 1
console.log(queue.dequeue()); // => 4

console.log(queue.isEmpty()); // true
```
