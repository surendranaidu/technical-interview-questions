# Data Structure Interview questions

Reference:

* [Medium-Diving into data structures](https://medium.com/omarelgabrys-blog/diving-into-data-structures-6bc71b2e8f92)

## **What is Data Structure ?**

Simply put, a data structure is a container that stores data in a specific layout. This “layout” allows a data structure to be efficient in some operations and inefficient in others. Your goal is to understand data structures so that you can pick the data structure that’s most optimal for the problem at hand.

5 fundamental behaviors of data structure are: access, insert, delete, find, & sort

## **Why do we need Data Stucture ?**

As data structures are used to store data in an organized form, and since data is the most crucial entity in computer science, the true worth of data structures is clear.

No matter what problem are you solving, in one way or another you have to deal with data — whether it’s an employee’s salary, stock prices, a grocery list, or even a simple telephone directory.

Based on different scenarios, data needs to be stored in a specific format. We have a handful of data structures that cover our need to store data in different formats.

## Array

An array (One dimensional Array) is an ordered collection of items, where each item inside the array has an index. Items are placed next to each other in the continious memmory. All items have the same type

* Multidimensional Array

It’s basically an array of arrays, where each item in this array itself contains another array.

* Jagged array

It’s a Multidimensional array where each item can have different sizes.

## List

It’s a collection of items (called nodes) ordered in a linear sequence

* Linked List:

It’s a collection of nodes, where each node has a value and a link to the next node in the list.

* Doubly Linked List

* Circular Linked List

## Stack

It’s a collection of items where we add and remove items to and from the top of the stack.

A stack can be easily implemented either using an array or a linked list

The Basic Operations of Stacks are are: push(), pop(), & peek(). push is for pushing a new element on the top of the stack, and pop will return (and remove) the element at the top, while peek will get the element at the top without removing it.

## Queues

It’s a collection of items where we add items to the end and remove items from the front of the queue.

As with stacks, a queue can be implemented either using an array or a linked list. Just like a stack, queue support operations: add(), remove(), & peek().

* Priority Queues

it’s a queue, where items with higher priority step ahead of items with lower priority in the queue.

## Deque

It’s a queue and a stack at the same time.

## Hash Tables

It’s a typical data structure to implement an associative arrays; mapping keys to values.

The big benefit of hash tables over arrays and over linked lists is they’re very fast, both for looking at whether an item exists or finding a specific item in a hash table, and for inserting and deleting items.

### How it works ?

Input Data (keys) will be run through the hash function, getting a specific hash value out (usually an integer). Then, it will assign the value to an array element with the index equals to the returned hash integer value.

![Hashing](https://miro.medium.com/max/500/1*bDtDJ-JgV8BsxvOQFx7_jQ.png)

### Collision

We can expect that a hash collision will arise; when we get the same hash value for different keys. But, how to manage it?

One solution is each location in bucket now contains a simple collection, like an array, or a linked list. Once we get to the location with multiple values, the hash table will traverse that internal list to find what we’re looking for.

![SCT](https://miro.medium.com/max/500/1*3Uzpz0rRxGhH_XlsmQyZvQ.png)

This is what is called the “Separate Chaining Technique” in hash tables. Now, there are other techniques for managing collisions inside hash tables, including open addressing, Cuckoo hashing, hop-scotch, and Robin Hood hashing.

## Set

It’s an unordered collection of items, with no repeated values.

Unlike an array, or values in an associative array, or a linked list, sets do not allow duplicates. You cannot add the same object, the same value twice to the same set.

Sets are designed for very fast lookup, to very quickly be able to see if we already have a value contained in a collection.

## Tree

It’s a collection of nodes, where each node might link to one, or two, or more nodes.

![Tree](https://www.tutorialspoint.com/data_structures_algorithms/images/binary_tree.jpg)

* Binary Trees

A binary tree is just a tree with maximum of two child nodes for any parent node. Binary trees are often used for implementing a wonderfully searchable structure called a “Binary Search Tree” or “BST”.

* Binary Search Trees (BST)

It’s a specific type of binary tree, where the left child node is less than its parent, and a right child node is greater than its parent.

![BST](https://cdn.programiz.com/sites/tutorial2program/files/bst-vs-not-bst.jpg)

* **How Binary Search Trees Work?**

The the rule is that the left child node must be less than its parents, and a right child node must be greater than its parents, and that rule follows all the way down in the tree.

And as we insert new nodes with values, the rule will always be followed to make sure that the tree stays sorted.

So, It is a data structure that naturally stays sorted and it’s sometimes called “A Sorted Tree” or “An Ordered Tree”.

* **Binary Search Tree Vs Hash Table**

Both are fast for insertion, fast for deletion, fast for accessing any element even at large sizes. But, because binary search trees stay sorted, they allow us to get all the items out of the tree in order, where the hash table doesn’t guarantee a specific order.

## Heaps

It’s a specific type of binary tree, where we add nodes from top to bottom, left to right, and child nodes must be less (or greater) than or equal their parents.

Heaps are usually implemented using the idea of a binary tree, not a binary search tree but still, a binary tree. They’re a way of implementing other abstract data types like the priority queue.

* **Min Vs Max Heap**

A min heap states that any child node must be greater than (or equal) its parent node, while a max heap states that any child node must be less than (or equal) its parent node. However, we don’t care if a node is less than or greater than it’s sibling.

![Heap](https://www.geeksforgeeks.org/wp-content/uploads/MinHeapAndMaxHeap.png)

## Graphs

It’s a collection of nodes, where a node can link to multiple other nodes, no specific sequence, no root node.

![Graph](https://www.geeksforgeeks.org/wp-content/uploads/undirectedgraph.png)

* Graph Theory In Mathematics

Because graphs in computer science are so closely linked to graph theory in mathematics. It is common to hear mathematical terms used. So, In graph theory, we call the nodes “vertices”, and the links between them are referred to as “edges”.

* Graphs Usage

We could use a graph to model a social network with each node a person. Or, modeling the distances between cities. We could model a ethernet network in an office, or in an entire building, or a city.

* Direct & Undirect Graphs

We can also say whether those edges should have a direction to them or not.

![directVsUndirectGraph](https://datafreakankur.com/wp-content/uploads/2018/12/image-39.png)

In some situations, it makes sense that any edge, any connection between two vertices, is only one-way; So, node A is connected to node B, while the reverse is not true; node B is NOT connect to node A.

In other situations, you might want to be able to follow that edge, that link, in either direction; So, node A is connected to node B, and also node B is connected to node A.

* Weighted Graphs

You can also give every edge a weight; associating a number, with each of the edges.

![WeightedGraph](https://static.packt-cdn.com/products/9781786467355/graphics/ab2a72e9-61f2-4fe0-9bb9-c8533968ffef.jpg)

You could do this to represent, say, the distances between cities, if you were trying to calculate the shortest route between multiple locations. Or, you could use a weight to indicate which edges take priority over other edges.

## Comparison between data structures

![Comparison](https://miro.medium.com/max/2680/1*TXcoRpFxDTdRl0YYawE3XA.png)

## Languague Support

|Type|C++|Java|C#|Python
|--|--|--|--|--|
|Dynamic Arrays|std:vector|ArrayList|ArrayList|list
|Linked List|list|LinkedList|LinkedList|-
|Stacks|stack|Stack|Stack|-
|Queues|queue|Queue|Queue|queue
|Deque|deque|Deque|-|deque
|Priority Queues|priorty_queue|PriorityQueue|PriorityQueue|PriorityQueue|
|Associative Arrays|std::map|Map, HashMap, HashTable|Dictionary<TKey,TValue>,Hashtable and StringDictionary, SortedDictionary|dict
|Sets|std:set|Set|HashSet. SortedSet|set, fronzenset
|Graph|-|-|-|-