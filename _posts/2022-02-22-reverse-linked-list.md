---
layout: single
title:  "Linked List Question - reverse"
categories: 
    - Data Structures
tags: 
    - [TIL, Big-O, Algorithms, Data Structures, Linked List, Coding Problem, Linked-List Problem]
---
Reversing elements in sigly linked list.

```jsx
function reverse(linkedList) {
    // check if there is only one node
    if (!linkedList.head.next) {
        return linkedList.head;
    }

		// we need to change second node to point to the first node 
		// and hold on to where second node was pointing.
		// second node becomes first and the node we were holding on will be the second to move up the list.
    let first = linkedList.head;
    linkedList.tail = linkedList.head;
    let second = first.next;
    while(second) {
        const temp = second.next;
        second.next = first;
        first = second;
        second = temp;
    }
    linkedList.head.next = null;
    linkedList.head = first;
}
```