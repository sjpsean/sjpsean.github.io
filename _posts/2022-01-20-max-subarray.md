---
layout: single
title:  "Array Question - maximum subarray"
categories: 
    - Data Structures
tags: 
    - [TIL, Big-O, Algorithms, Data Structures, Arrays, Coding Problem, Array Problem]
---

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

A subarray is a contiguous part of an array.
 
`Example 1:
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.`

`Example 2:
Input: nums = [1]
Output: 1`

`Example 3:
Input: nums = [5,4,-1,7,8]
Output: 23`

### Brute force approach

```jsx
    /* naive answer
    for i
    have an 'array' with size of i
    fill up the array with numbers in nums from the beginning.
    get the sum of all numbers in the array and store it in 'sum'.
    
    compare sum with the one before and if it is bigger, store bigger sum.
    
    if not every numbers in nums went through the process, drop first number 
		in the array and add next number from nums.
    */
```

### Better answer - O(n)

Using Kadane's Algorithm

```jsx

function maxSubArray(nums) {
    let maxSum = nums[0];
    let currSum = nums[0];
    for (let i = 1; i < nums.length; i++) {
        currSum = Math.max(nums[i], nums[i] + currSum);
    // Check if it adds up to a bigger value (meaning it is worth to keep on adding)
			// How? By comparing the sum and the last number that has been added. 
			// if the last number is bigger than the sum, that means adding what was before is a minus.
    // If currSum makes nums[i] smaller, currSum restart the process from nums[i].

        maxSum = Math.max(currSum, maxSum);
     // maxSum will store the biggest currSum.
    }
    return maxSum;
}

// test
console.log(maxSubArray([-2,1,-3,4,-1,2,1,-5,4]));
console.log(maxSubArray([1]));
console.log(maxSubArray([5,4,-1,7,8]));
```