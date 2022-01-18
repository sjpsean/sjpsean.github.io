---
layout: single
title:  "Array Question - reverse string"
categories: 
    - Data Structures
tags: 
    - [TIL, Big-O, Algorithms, Data Structures, Arrays, Coding Problem, Array Problem]
---


Create a function that reverses a string:

ex) 'any strings 123' should be: '321 sgnirts yna'

```jsx
function reverseString(str) {
    // check input
    if (!str || typeof str !== 'string') return false;

    let array = new Array();
    for (let i = str.length - 1; i >= 0; i--) {
        array.push(str[i]);
    }
    return array.join('');
}

console.log(reverseString("sungjin park"));
console.log(reverseString("fu"));
console.log(reverseString(""));
console.log(reverseString(null));
console.log(reverseString(12));

// using built-in method
function reverseStringSimple(str) {
    return str.split('').reverse().join('');
}

console.log(reverseStringSimple('sungjin park'));

// Or... string reverse in one line
console.log('something'.split('').reverse().join(''));
```

All of these methods take O(n) time complexity (n = input string’s length).