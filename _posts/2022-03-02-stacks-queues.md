---
layout: single
title:  "Data Structures - Stacks & Queues"
categories: 
    - Data Structures
tags: 
    - [TIL, Big-O, Algorithms, Data Structures, Stack, Queue]
---

### What is Stacks?

- it’s like a stack of plates.
    
    Only have access to the last one added.
    
    last in first out (LIFO)
    

ex) undo

### What is Queues?

- it’s like a line in cafeteria.
    
    first in first out (FIFO)
    

ex) printer

### Time Complexity of Stack

- lookup- **O(n)**
- pop - **O(1)**
- push - **O(1)**
- peek - **O(1)**

### **Pros**

- Fast add/delete
- Fast peek
- Ordered

### **Cons**

- Slow lookup

<aside>
✅ Fast, but used only in a sepcific purpose.

</aside>

example of implementing a stack using linked list:

```jsx
class Node {
    constructor(value) {
        this.value = value;
        this.next = null;
    }
}

class Stack {
    constructor() {
        this.top = null;
        this.bottom = null;
        this.length = 0;
    }

    peek() {
        return this.top;
    }

    push(value) {
        const newNode = new Node(value);
        if (this.length === 0) {
            this.top = newNode;
            this.bottom = newNode;
        } else {
            const oldTop = this.top;
            this.top = newNode;
            this.top.next = oldTop;
        }
        this.length++;
    }

    pop() {
        if (!this.top) {
            return null;
        }
        if (this.top === this.bottom) {
            this.bottom = null;
        }
        const poppedTop = this.top;
        this.top = this.top.next;
        this.length--;
        return poppedTop;
    }
}
```

example of implementing a queue using linked list:

```jsx
class Node {
    constructor(value) {
        this.value = value;
        this.next = null;
    }
}

class Queue {
    constructor() {
        this.first = null;
        this.last = null;
        this.length = 0;
    }

    peek() {
        console.log(this.first);
        return this.first;
    }

    enqueue(value) {
        const newNode = new Node(value);
        if (this.length === 0) {
            this.first = newNode;
            this.last = newNode;
        } else {
            this.last.next = newNode;
            this.last = newNode;
        }
        this.length++;
    }

    dequeue() {
        if (!this.first) {
            return null;
        }
        if (this.first === this.last) {
            this.last = null;
        }
        const oldFirst = this.first;
        this.first = this.first.next;
        this.length--;
        return oldFirst;
    }
}
```