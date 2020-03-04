# General Programing Interview questions 

* **What is a programming language ? How many kinds of programming languages ?**

A programming language is a notation designed to connect instructions to a machine or a computer. Programming languages are mainly  used to control the performance of a machine or to express algorithms. At present, thousand programming languages have been implemented.

There is no overarching classification scheme for programming languages. Usually, programming languages can be classified into a few types based on heir specialties, aas well as their own advantages and  disadvantages. One specific language can belong to more than one type.

**Procedural Programming Languages** is used to execute a sequence of statements which lead to a result. Typically, this type of programming language uses multiple variables, heavy loops and other elements, which separates them from functional programming languages.

**Functional Programming Languages** focus on the return values of functions

**Object-oriented Programming Language** view the world as a group of objects that have internal data and external accessing parts of that data. Encapsulation, Abstraction, Inheritance and Polymorphism are its characteristics.

**Scripting Programming Languages** support for development of large systems. For example, they may not have compile-time type checking. Usually, these languages require tiny syntax to get started.

* **Differentiate Interpreted languages and Compiled languages**

Both are human-readable code and are converted to computer-readable machine code by interpreter and compiler perspectively.

**Compiled Languages** are converted directly into machine code that the processor can execute. As a result, they tend to be faster and more efficient to execute than interpreted languages. They also give the developer more control over hardware aspects, like memory management and CPU usage.

Compiled languages need a “build” step - they need to be manually compiled first. You need to “rebuild” the program every time you need to make a change. Examples of pure compiled languages are C, C++, Erlang, Haskell, Rust, and Go.

**Interpreted Languages** will be run by Interpreters line by line and execute each command. Interpreted languages were once known to be significantly slower than compiled languages. But, with the development of just-in-time compilation, that gap is shrinking.

Examples of common interpreted languages are PHP, Ruby, Python, and JavaScript.

* **Low-level languages vs High-level languages**

The definitions of these terms are quite weak. A guideline is that low-level language is close to the hardware; a high-level language is abstract. Programming languages generally fall somewhere between the two in a spectrum.

**Low-level**: machine code, assembly language.

**System-leve**l (basic abstractions and control flow): C

**Mixed / General purpose** (both high and low-level constructs): C++

**Application-level** (too high-level for certain types of real-time, embedded): Java, C#, Python …

**Abstract / High-level** (based on Maths rather than hardware): Haskell, Erlang, SML, OCaml ..

* **Heap vs Stack, Stack overflow, Heap Fragmentation**

**Stack** is used for static memory allocation and **Heap** for dynamic memory allocation, both stored in the computer's RAM .

Variables allocated on the stack are stored directly to the memory and access to this memory is very fast, and it's allocation is dealt with when the program is compiled. When a function or a method calls another function which in turns calls another function etc., the execution of all those functions remains suspended until the very last function returns its value. The stack is always reserved in a LIFO order, the most recently reserved block is always the next block to be freed. This makes it really simple to keep track of the stack, freeing a block from the stack is nothing more than adjusting one pointer.

Variables allocated on the heap have their memory allocated at run time and accessing this memory is a bit slower, but the heap size is only limited by the size of virtual memory . Element of the heap have no dependencies with each other and can always be accessed randomly at any time. You can allocate a block at any time and free it at any time. This makes it much more complex to keep track of which parts of the heap are allocated or free at any given time.

* [Garbage Collection](https://guide.freecodecamp.org/computer-science/garbage-collection/)
* **List some general concepts of programming languages**



* Passing arguments as value or reference, and different
* OOP and its characteristics with example
* OODA and example
* Package, Module, Components, Library, Framework, Platform
* How to make your code better
* How to different senior vs junior developer