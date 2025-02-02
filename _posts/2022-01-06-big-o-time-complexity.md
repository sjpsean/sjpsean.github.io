---
layout: single
title:  "Big-O Notations (Time Complexity)"
categories: Algorithms
tags: TIL Big-O Algorithms
---
Big-O Notations for Time Complexity

- What causes time complexity?
    - Operations (+, -, *, /)
    - Comparisons (<, >, ==)
    - Looping (for, while)
    - Outside function call (function())

## O(1)

- Constant time - number of operations is a constant that doesn’t change.

For example,

```jsx
const large = new Array(100).fill('element');

function logFirstTwoBoxes(boxes) {
	console.log(boxes[0]);
	console.log(boxes[1]);
	console.log(boxes[2]);
}

logFirstTwoBoxes(large); // O(1) - Constant time
// no matter how big the array(or any kind of input) gets, the number of operations will be the same.
```

This function will have three console logs `boxes[0], boxes[1], boxes[2]` no matter how big the input `boxes` get.


## O(log n)

- Number of elements to lookup gets divided by half for each operation.
- Binary Search Tree's lookup speed.

Think of a **phonebook**. We don’t need to check every elements. We can only check if the name could be on the next pages or the pages before. After decision is made, we don’t need to consider the pages that will not have the name we are finding.


## O(n)

- Linear time - number of operations increases linearly as number of input increases.

Basically, **a function or an algorithm that operates one time per one element.**

For example,

```jsx
const nemo = ['nemo'];
const large = new Array(100).fill('nemo');

function findNemo(array) {
	let t0 = performance.now();
	for (let i = 0; i < array.length; i++) {
		if (array[i] === 'nemo') {
			console.log('Found NEMO');
		}
	}
}
findNemo(large);  // O(n) - Linear Time
```

This function finds ‘nemo’ in the array and operates one time for every element in the array to check if that one is ‘nemo’ or not : `arrray[i] === 'nemo'`. So, we can say its Big-O is O(n).


## O(n^2)

- Quadratic time - number of operations increases quadratically.

Most of the time, this is because there is a **nested for loop**.

For example,

```jsx
// Log all pairs of array
const boxes = ['a', 'b', 'c', 'd', 'e'];

function logAllPairsOfArray(array) {
	for (let i = 0; i < array.length; i++) {
		for (let j = 0; j < array.length; j++) {
			console.log(array[i], array[j]);
		}
	} // nested for loop
}
logAllPairsOfArray(boxes);  // O(n^2) - Quadratic time
```

## O(n!)

- Factorial time

O(n * (n-1) * (n-2) * ... * 1) → each element is nesting a loop inside of nested loops.

For example,

```jsx
function f(n) {
	if (n === 0) {
		console.log("done");
		return;
	}
	for (let i = 0; i < n; i++) {
		f(n-1);
	}
}

f(10); // O(n!) - Factorial time
// f(10) will call 10 f(9)'s, f(9) will call 9 f(8)'s and so on.
// f(n) will call n f(n-1)'s, and so on
// for n { for n-1 { for n-2 { ... { return }
// O(n!)
```