---
layout: single
title:  "Array Question - merge sorted arrays"
categories: 
    - Data Structures
tags: 
    - [TIL, Big-O, Algorithms, Data Structures, Arrays, Coding Problem, Array Problem]
---
Merge two sorted arrays to one:

ex) [0, 3, 4, 31], [4, 6, 30] --> [0, 3, 4, 4, 6, 30, 31]

```jsx
function mergeSortedArrays(arr1, arr2) {
    // check if one of the input array is empty.
    if (arr1.length === 0) {
        return arr2;
    }
    if(arr2.length === 0) {
        return arr1;
    }

    // push the smaller number out of the two smallest numbers from each array.
    // repeat that until either one of the array's every element has been pushed.
    let idx1 = 0;
    let idx2 = 0;
    const mergedArray = [];
    while (idx1 < arr1.length && idx2 < arr2.length) {
        if (arr1[idx1] < arr2[idx2]) {
            mergedArray.push(arr1[idx1]);
            idx1++;
        }
        else {
            mergedArray.push(arr2[idx2]);
            idx2++;
        }
    }

    // get the leftovers(elements that are not added to the mergedArray yet) from the arrays.
    for (idx1; idx1 < arr1.length; idx1++) {
        mergedArray.push(arr1[idx1]);
    }
    for (idx2; idx2 < arr2.length; idx2++) {
        mergedArray.push(arr2[idx2]);
    }
    return mergedArray;
}

// test
console.log(mergeSortedArrays([0, 1, 2, 5], [2, 3, 4]));
console.log(mergeSortedArrays([0,3,4,31], [3,4,6,30]));
console.log(mergeSortedArrays([1,2,3,4], [4,5,6,7]));
console.log(mergeSortedArrays([3,4,5,6], [0,1,2,3]));
console.log(mergeSortedArrays([0, 3, 4, 31], 1));
console.log(mergeSortedArrays([0, 3, 4, 31], null));
console.log(mergeSortedArrays(null, null));
console.log(mergeSortedArrays({}, {}));
```

Time complexity = O(n).