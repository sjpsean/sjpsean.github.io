---
layout: single
title:  "Big-O Notation - O(n)"
categories: Algorithms
tags: TIL Big-O Algorithms
---

### Why do we need Big-O notation?

To scale the quality of code by seeing **number of operations (or the degree of increase) that are needed when the elements (or input) increases.**

<!-- ![big-o_complexity_chart]({{ site.url }}{{ site.baseurl }}/assets/images/big-o_complexity_chart.jpeg){: .fill} -->

<!-- <img src="{{ site.url }}{{ site.baseurl }}/assets/images/big-o_complexity_chart.jpeg" alt="" class="half"> -->
<figure class="half">
    <a href="/assets/images/big-o_complexity_chart.jpeg"><img src="/assets/images/big-o_complexity_chart.jpeg"></a>
</figure>


> It is not about how much time it takes, but more about **how many steps it takes to perform.**

## O(n)

In the other word, Linear time.  
Basically, O(n) means a big-O for **a function or an algorithm that operates one time per one element.**

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
findNemo(large);  // O(n) --> Linear Time
```

This function finds ‘nemo’ in the array and operates one time for every element in the array to check if that one is ‘nemo’ or not : `arrray[i] === 'nemo'`. So, we can say it's Big-O is O(n).