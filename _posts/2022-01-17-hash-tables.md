---
layout: single
title:  "Data Structures - Hash Tables"
categories: 
    - Data Structures
tags: 
    - [TIL, Big-O, Algorithms, Data Structures, Hash Tables, Map, Hash, Object]
---
## What is a Hash Table?

### Hash table in different languages

= Map / HashMap- **Java**

= Dictionary - **Python**

= Object - **Javascript** (object is a type of Hash Table) 

= Hash - **Ruby**

= Unordred map - **C++**

[https://en.wikipedia.org/wiki/Comparison_of_programming_languages_(associative_array)](https://en.wikipedia.org/wiki/Comparison_of_programming_languages_(associative_array))

### How do Hash Tables store data?

key → **Hash function** → index (address to store the value) → key-value both get stored.

- **Hash function** decides where to put data
- Data is not stored next to each other. Hard to **iterate** through the data in the table.

### What is Hash Function?

function that generates a value of fixed length for each input.

1. It’s one way. Finding the input from the hash is practically impossible.
2. Same ouput for same input, but different for every input (idempotent).
3. O(1) time complexity.

### Time Complexity of Hash Tables

- Access - **O(1)**
- Search - **O(1)**
    - lookup might take O(n) depending on the hash function
- Insertion - **O(1)**
- Deletion - **O(1)**

### Collision

Collision happens when more than one data happen to have same hash value that more than one data is being stored in the same key, connected with linked-list. 

- When collision happens, reading and writing becomes O(n)

How to avoid collision? 

[https://en.wikipedia.org/wiki/Hash_table#Collision_resolution](https://en.wikipedia.org/wiki/Hash_table#Collision_resolution)

### **Pros**

- Quick **access** to certain **values**.
- **Inserting** is typically O(1) without collision.
- Flexible **keys**

### **Cons**

- **Unordered**. No concept of order. It’s not stored next to each other.
- **Slow key iteration**.
- Use more space.

example of implementing a hash table:

```jsx
class HashTable {
  constructor(size){
    this.data = new Array(size);
	}

// hash function
  _hash(key) {
    let hash = 0;
    for (let i =0; i < key.length; i++){
	    hash = (hash + key.charCodeAt(i) * i) % this.data.length
    }
    return hash;
  }

// [0, [[key, value], [], ...], 0, 0, [[]], ...]
  set(key, value) {
    let address = this._hash(key);
    if (!this.data[address]) {
      this.data[address] = [];
    }
    this.data[address].push([key, value]);
    return this.data;
  }

  get(key){
    const address = this._hash(key);
    const currentBucket = this.data[address]
    if (currentBucket) {
      for(let i = 0; i < currentBucket.length; i++){
        if(currentBucket[i][0] === key) {
          return currentBucket[i][1]
        }
      }
    }
    return undefined;
  }
}

const myHashTable = new HashTable(50);
```