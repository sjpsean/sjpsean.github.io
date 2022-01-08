---
layout: single
title:  "Big-O Notations (Space Complexity)"
categories: Algorithms
tags: TIL Big-O Algorithms
---
Big-O notations for Space Complexity

- What causes space complexity?
    - Variables
    - Data Structures
    - Function call
    - Allocations
    

## O(1)

The function doesn’t add more space.

For example,

```jsx
function boo(n) {
    for (let i = 0; i < n; i++) {
        console.log('boo!');
    }
}

boo(100); // Space Complexity O(1)
```

## O(n)

The function will add n more spaces.

```jsx

function fillNewArray(n) {
    var newArray = [];
    for (let i = 0; i < n; i++) {
        newArray[i] = '*';
    }
    return newArray;
}

fillNewArray(100); // Space complexity O(n)
```