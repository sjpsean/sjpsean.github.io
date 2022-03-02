---
layout: single
title:  "Data Structures - Linked List"
categories: 
    - Data Structures
tags: 
    - [TIL, Big-O, Algorithms, Data Structures, Linked List]
---

### What is Linked List?

Linked list is formed with nodes that contains a value and a pointer that points to the next node.

The first node is called `head` and the last one is called `tail`. Tail’s pointer will point to `null`.

### What is a pointer?

Reference to something else in memeory. In other words, it works as an address of a value or a data.

### Time Complexity of Linked List

- Access - **O(n)**
    - this is because it doesn’t have an index. Linked list always starts from the head to the tail to access data.
    
    traversing through a linked list is slower than an array because the data it stores is scattered in the memory.
    
- Search - **O(n)**
- Insertion - **O(n)**
- Deletion - **O(n)**
    
    Similar to hash map, but has a form of an order.
    

### Single vs Double

- Singly Linked List
    
    +simple implementation.
    
    +Lesser memory and less operation.
    
    -Cannot be iterated.
    
    less memory, fast insertion and deletion. Less searching, less adding in the front.
    
- Doubly Linked List
    
    +iterated from the front or back.
    
    +delete previous one  is easier.
    
    -complex to implement
    
    -require more storage, extra operation when adding and deleting. 
    
    no problem on memory, good operation on searching.
    

### Pros

- Fast **Insertions**
- Fast **Deletion**
- Ordered
- Felxible Size

### **Cons**

- Slow **lookup**
- More memory is needed

Why choose linked list? - Simplicity and ability to grow and shrink.

Where it’s used? - file systems, browser history



example of implementing a singly linked list:

```jsx
class Node {
    constructor(value) {
        this.value = value;
        this.next = null;
    }
}

class LinkedList {
    constructor(value) {
        this.head = {
            value: value,
            next: null
        }
        this.tail = this.head;
        this.length = 1;
    }

    append(value) {
        const newNode = new Node(value);
        this.tail.next = newNode;  // adding new node next to the last node.
        this.tail = newNode;  // update tail with new node, so next time when append, newer node will be added next to this node.
        this.length++;
    }

    prepend(value) {
        const newNode = new Node(value);
        newNode.next = this.head;
        this.head = newNode;
        this.length++;
    }

    insert(index, value) {
        const newNode = new Node(value);
        
        if (index == 0) {
            this.prepend(value);
            return this;
        }
        else if (index == this.length) {
            this.append(value);
            return this;
        } else if (index < 0) {
            console.log('index out of range. index < 0');
            return false;
        } else if (index > this.length) {
            console.log('index out of range. index > length');
            return false;
        }
        
        let nodeBeforeIndex = this.traverseToIndex(index-1);
        newNode.next = nodeBeforeIndex.next;
        nodeBeforeIndex.next = newNode;
        this.length++;
    }

    remove(index) {
        if (index < 0) {
            console.log('index out of range. index < 0');
            return false;
        } else if (index >= this.length) {
            console.log('index out of range. index > length');
            return false;
        }

        if (index == 0) {
            this.head = this.head.next;
            this.length--;
            return this;
        }
        
        const nodeBeforeIndex = this.traverseToIndex(index-1);
        nodeBeforeIndex.next = nodeBeforeIndex.next.next;
        
        if (index == this.length - 1) this.tail = nodeBeforeIndex;
        this.length--;
        return this;
    }

    traverseToIndex(index) {
        let counter = 0;
        let currentNode = this.head;
        while(counter !== index){
          currentNode = currentNode.next;
          counter++;
        }
        return currentNode;
      }

    show() {
        let node = this.head;
        while (node != null) {
            console.log(node);
            node = node.next;
        }
        console.log('tail: ' + this.tail.value);
        console.log('length: ' + this.length);
    }
}

const myLinkedList = new LinkedList(1);
myLinkedList.append(2);
myLinkedList.append(3);
myLinkedList.insert(3,4);
myLinkedList.remove(3);
myLinkedList.show();
```

example of implementing a doubly linked list:

```jsx
class Node {
    constructor(value) {
        this.value = value;
        this.next = null;
        this.prev = null;
    }
}

class DoublyLinkedList {
    constructor(value) {
        this.head = {
            value: value,
            next: null,
            prev: null
        };
        this.tail = this.head;
        this.length = 1;
    }

    append(value) {
    const newNode = new Node(value);
    newNode.prev = this.tail
    this.tail.next = newNode;
    this.tail = newNode;
    this.length++;
    }

    prepend(value) {
        const newNode = new Node(value);
        this.head.prev = newNode
        this.head = newNode;
        this.length++;
    }

    insert(index, value){
        const newNode = new Node(value);

        if (index == 0) {
            this.prepend(value);
            return this;
        }
        else if (index == this.length) {
            this.append(value);
            return this;
        } else if (index < 0) {
            console.log('index out of range. index < 0');
            return false;
        } else if (index > this.length) {
            console.log('index out of range. index > length');
            return false;
        }
    
        const leader = this.traverseToIndex(index-1);
        const follower = leader.next;
        leader.next = newNode;
        newNode.prev = leader;
        newNode.next = follower;
        follower.prev = newNode;
        this.length++;
    }

    traverseToIndex(index) {
      //Check parameters
      let counter = 0;
      let currentNode = this.head;
      while(counter !== index){
        currentNode = currentNode.next;
        counter++;
      }
      return currentNode;
    }

    show() {
        let node = this.head;
        while (node != null) {
            console.log(node);
            node = node.next;
        }
        console.log('tail: ' + this.tail.value);
        console.log('length: ' + this.length);
    }
  }
```