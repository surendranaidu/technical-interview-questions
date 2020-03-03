# Interview Questions

Some common questions that software developers should prepare

## 1. Common questions

These questions used for most of developers from general concept of programming, testing and os architect

### 1.1 [General programming](./common/general/README.md)

You might be asked about :

* Kinds of programming languages, Interpreted vs compiled languages
* Low-level languages vs High-level langues
* Heap vs Stack, Stack overflow, Heap Fragmentation
* Garbage Collection
* List some general concepts of programming languages
* Passing arguments as value or reference, and different
* OOP and its characteristics with example
* OODA and example
* Package, Module, Components, Library, Framework, Platform
* How to make your code better
* How to different senior vs junior developer

### 1.2 [Concurrency programing](./common/concurrent/README.md)

* Why is testing multithreaded/concurrent code so difficult?
* Multithreading vs Multiprocessing
* What is a race condition? Code an example, using whatever language you like.
* What is a deadlock? Would you be able to write some code that is affected by deadlocks?
* What is process starvation? If you need, let's review its definition.
* What is a wait free algorithm?

### 1.3 [Code versioning](./common/versioning/README.md)

* What's a rebase
* How to modify commit that had been pushed
* What’s is cherry pick

### 1.2 [Testing](./common/testing/README.md)

* Why test
* Kinds of Test
* Mocking

### 1.3 [Network](./common/network/README.md)

* OSI Model
* TCP VS UDP
* HTTP vs HTTPS
* HTTP 1 vs 2 vs 3
* MTTP vs Websocket
* MQTT vs RPC
* FPT vs SCP
* VPN

### 1.4 [OS Concept](./common/os/README.md) (Optional)

* CPU core vs CPU Threads
* CPU vs GPU
* Linux distributions, core
* Real time OS
* Arm vs x86
* RISC vs CISC

## 2. Data structure and Algorithms

### 2.1 [Data Structure](./data-structure/README.md)

Array, Linked List, Hashtable, Binary Tree

### 2.2 [Algorithms](./algorithms/README.md)

* Complexity, Time complexity CPU complexity

### 2.3 Path Finding Algorithms

* Dijkstra
* A star

## 3. [Code Practices](code_practices/README.md)

Choose any language then implement some programs like this

* Write a program to execute the Bubble sort algorithm.
* Write a program to produce Star triangle.
* Write a program to produce Fibonacci series.
* Write a program to check if a number is prime.
* Write a program to check if a sequence is a Palindrome.
* Write a one-liner that will count the number of capital letters in a file. Your code should work even if the file is too big to fit in memory.
* Write a sorting algorithm for a numerical dataset
* Looking at the below code, write down the final values of A0, A1, …An.

```python
A0 = dict(zip(('a','b','c','d','e'),(1,2,3,4,5)))
A1 = range(10)A2 = sorted([i for i in A1 if i in A0])
A3 = sorted([A0[s] for s in A0])
A4 = [i for i in A1 if i in A3]
A5 = {i:i*i for i in A1}
A6 = [[i,i*i] for i in A1]
print(A0,A1,A2,A3,A4,A5,A6)
```

## 4. [Code Design](design/README.md)

* Design Pattern: Creational, Behavior, Structural
* Tell me about Inversion of Control and how it improves the design of code.
* Write a snippet of code violating the Don't Repeat Yourself (DRY) principle. Then, fix it.
* How would you deal with Dependency Hell?
* Mechanisms for achieving Separation of Concerns
* What's the difference between cohesion and coupling?
* What is refactoring useful for?
* Are comments in code useful? Some say they should be avoided as much as possible, and hopefully made unnecessary. Do you agree?
* What is the difference between design and architecture?
* In your opinion, why has Object-Oriented Design dominated the market for so many years?

## 4. Programming Language

### 4.1 [C++](./languages/c++/README.md)

### 4.2 [Python](./languages/python/README.md)

### 4.3 [Javascript](./languages/javascript/README.md)

### 4.4 [TypeScript](./languages/typescript/README.md)

## 5. [Backend Developer](./backend/README.md)

## 6. [Frontend Developer](./frontend/README.md)

## 7. [Mobile Developer](./mobile/README.md)

## 9. [Devops Developer](./devops/README.md)

## 10. [Software Architect](./architect/README.md)

**Note** This is in development. I appreciate your contribution. Pull requests are welcome :heart_eyes: