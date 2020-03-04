# Python3 Interview questions 

References:

[edureka](https://www.edureka.co/blog/interview-questions/python-interview-questions/)

TODO

- [ ] Code example 
- [ ] Review

## Basic Python Interview Questions

* **What is the difference between list and tuples in Python?**

|  List | Tuple  |
|---|---|
|  Lists are mutable i.e they can be edited. |  Lists are mutable i.e they can be edited. |
Lists are slower than tuples. | Tuples are faster than list
Syntax: list_1 = [10, ‘Chelsea’, 20] | Syntax: tup_1 = (10, ‘Chelsea’ , 20)

* **key features of Python**

|  Name | Content  |
|---|---|
| interpreted language | Python does not need to be compiled before it is run |
| dynamically typed | you don’t need to state the types of variables when you declare them or anything like that |
| object orientated programming | it allows the definition of classes along with composition and inheritance. Python does not have access specifiers (like C++’s public, private). |
| first-class objects | they can be assigned to variables, returned from other functions and passed into functions. Classes are also first class objects |

* **What type of language is python ? Programming or scripting ?**

Python is capable of scripting, but in general sense, it is considered as a general-purpose programming language

* **What is pep 8 ?**

PEP stands for Python Enhancement Proposal. It is a set of rules that specify how to format Python code for maximum readability.

* **How is memory managed in Python ?**

Memory management in python is managed by Python private heap space. All Python objects and data structures are located in a private heap. The programmer does not have access to this private heap. The python interpreter takes care of this instead.

The allocation of heap space for Python objects is done by Python’s memory manager. The core API gives access to some tools for the programmer to code.

Python also has an inbuilt garbage collector, which recycles all the unused memory and so that it can be made available to the heap space.

* **What is namespace in Python ?**

A namespace is a naming system used to make sure that names are unique to avoid naming conflicts.

Namespace is a way to implement scope. In Python, each package, module, class, function and method function owns a "namespace" in which variable names are resolved. When a function,  module or package is evaluated (that is, starts execution), a namespace is created. Think of it as an "evaluation context". When a function, etc., finishes execution, the namespace is dropped. The variables are dropped. Plus there's a global namespace that's used if the name isn't in the local namespace.

Each variable name is checked in the local namespace (the body of the function, the module, etc.), and then checked in the global namespace.

Variables are generally created only in a local namespace. The global and nonlocal statements can create variables in other than the local namespace.

* **What is PYTHONPATH ?**

It is an environment variable which is used when a module is imported. Whenever a module is imported, PYTHONPATH is also looked up to check for the presence of the imported modules in various directories. The interpreter uses it to determine which module to load.

* **What are python modules? Name some commonly used built-in modules in Python?**

Python modules are files containing Python code. This code can either be functions classes or variables. A Python module is a .py file containing executable code.

Some of the commonly used built-in modules are: os, sys

* **What is the difference between Python Arrays and lists ?**

Arrays and lists, in Python, have the same way of storing data. But, arrays can hold only a single data type elements whereas lists can hold any data type elements

```python
import array as arr
My_Array=arr.array('i',[1,2,3,4])
My_list=[1,'abc',1.20]
print(My_Array)
print(My_list)
```
Output:

```array(‘i’, [1, 2, 3, 4]) [1, ‘abc’, 1.2]```

* **What is __init__?**

__init__ is a method or constructor in Python. This method is automatically called to allocate memory when a new object/ instance of a class is created. All classes have the __init__ method.

* **What is self in Python?**

Self is an instance or an object of a class. In Python, this is explicitly included as the first parameter. However, this is not the case in Java where it’s optional.  It helps to differentiate between the methods and attributes of a class with local variables.

The self variable in the init method refers to the newly created object while in other methods, it refers to the object whose method was called.

* **How does break, continue and pass work ?**

|Name|Explaination|
|--|--|
|Break|Allows loop termination when some condition is met and the control is transferred to the next statement.|
|Continue| Allows skipping some part of a loop when some specific condition is met and the control is transferred to the beginning of the loop|
|Pass| Used when you need some block of code syntactically, but you want to skip its execution. This is basically a null operation. Nothing happens when this is executed.|

* **What does [::-1} do ?**

[::-1] is used to reverse the order of an array or a sequence.

* **How can you randomize the items of a list in place in Python?**

```python
from random import shuffle
x = ['Keep', 'The', 'Blue', 'Flag', 'Flying', 'High']
shuffle(x)
print(x)
```

* **What are python iterators?**

Iterators are objects which can be traversed though or iterated upon.

* **What is the difference between range & xrange?**

For the most part, xrange and range are the exact same in terms of functionality. They both provide a way to generate a list of integers for you to use, however you please. The only difference is that range returns a Python list object and x range returns an xrange object.

* **What is pickling and unpickling?**

Pickle module accepts any Python object and converts it into a string representation and dumps it into a file by using dump function, this process is called pickling. While the process of retrieving original Python objects from the stored string representation is called unpickling.

* **What are the generators in python?**

Functions that return an iterable set of items are called generators.

* **Whenever Python exits, why isn’t all the memory de-allocated?**

    - Whenever Python exits, especially those Python modules which are having circular references to other objects or the objects that are referenced from the global namespaces are not always de-allocated or freed.
    - It is impossible to de-allocate those portions of memory that are reserved by the C library.
    - On exit, because of having its own efficient clean up mechanism, Python would try to de-allocate/destroy every other object

* **What is a dictionary in Python?**

The built-in datatypes in Python is called dictionary. It defines one-to-one relationship between keys and values. Dictionaries contain pair of keys and their corresponding values. Dictionaries are indexed by keys

```python
dict={'Country':'India','Capital':'Delhi','PM':'Modi'}
```

* **How can the ternary operators be used in python?**

he Ternary operator is the operator that is used to show the conditional statements. This consists of the true or false values with a statement that has to be evaluated for it.

The Ternary operator will be given as:
[on_true] if [expression] else [on_false]

* **What does this mean: \*args, \*\*kwargs? And why would we use it?**

We use *args when we aren’t sure how many arguments are going to be passed to a function, or if we want to pass a stored list or tuple of arguments to a function. **kwargs is used when we don’t know how many keyword arguments will be passed to a function, or it can be used to pass the values of a dictionary as keyword arguments. The identifiers args and kwargs are a convention, you could also use *bob and **billy but that would not be wise.

* **What are negative indexes and why are they used?**

The sequences in Python are indexed and it consists of the positive as well as negative numbers. The numbers that are positive uses ‘0’ that is uses as first index and ‘1’ as the second index and the process goes on like that.

The index for the negative number starts from ‘-1’ that represents the last index in the sequence and ‘-2’ as the penultimate index and the sequence carries forward like the positive number.

The negative index is used to remove any new-line spaces from the string and allow the string to except the last character that is given as S[:-1]. The negative index is also used to show the index to represent the string in correct order.

* **What are Python packages?**

Python packages are namespaces containing multiple modules.

* **What are the built-in types of python?**

    - Integers
    - Floating-point
    - Complex numbers
    - Strings
    - Boolean
    - Built-in functions

* **Does Python have OOps concepts?**

Python is an object-oriented programming language. This means that any program can be solved in python by creating an object model. However, Python can be treated as procedural as well as structural language.

* **What is the difference between deep and shallow copy?**

Shallow copy is used when a new instance type gets created and it keeps the values that are copied in the new instance. Shallow copy is used to copy the reference pointers just like it copies the values. These references point to the original objects and the changes made in any member of the class will also affect the original copy of it. Shallow copy allows faster execution of the program and it depends on the size of the data that is used.

Deep copy is used to store the values that are already copied. Deep copy doesn’t copy the reference pointers to the objects. It makes the reference to an object and the new object that is pointed by some other object gets stored. The changes made in the original copy won’t affect any other copy that uses the object. Deep copy makes execution of the program slower due to making certain copies for each object that is been called.

* **What is Global Interpreter Lock (GIL)**

Python has a construct called the Global Interpreter Lock (GIL). The GIL makes sure that only one of your ‘threads’ can execute at any one time. A thread acquires the GIL, does a little work, then passes the GIL onto the next thread.

* **What is the process of compilation and linking in python?**

The compiling and linking allows the new extensions to be compiled properly without any error and the linking can be done only when it passes the compiled procedure. If the dynamic loading is used then it depends on the style that is being provided with the system. The python interpreter can be used to provide the dynamic loading of the configuration setup files and will rebuild the interpreter.

The steps that are required in this as:

    - Create a file with any name and in any language that is supported by the compiler of your system. For example file.c or file.cpp
    - Place this file in the Modules/ directory of the distribution which is getting used.
    - Add a line in the file Setup.local that is present in the Modules/ directory.
    - Run the file using spam file.o
    - After a successful run of this rebuild the interpreter by using the make command on the top-level directory.
    - If the file is changed then run rebuildMakefile by using the command as ‘make Makefile’.

## OOPS Interview Questions

* **Explain Inheritance in Python with an example.**

Inheritance allows One class to gain all the members(say attributes and methods) of another class. Inheritance provides code reusability, makes it easier to create and maintain an application. The class from which we are inheriting is called super-class and the class that is inherited is called a derived / child class.

They are different types of inheritance supported by Python:

1. **Single Inheritance** – where a derived class acquires the members of a single super class.
2. **Multi-level inheritance** – a derived class d1 in inherited from base class base1, and d2 are inherited from base2.
3. **Hierarchical inheritance** – from one base class you can inherit any number of child classes
4. **Multiple inheritance** – a derived class is inherited from more than one base class.

* **What is monkey patching in Python?**

In Python, the term monkey patch only refers to dynamic modifications of a class or module at run-time.

Consider the below example:

```python
# m.py
class MyClass:
def f(self):
print "f()"
```
We can then run the monkey-patch testing like this:

```python
import m
def monkey_f(self):
print "monkey_f()"
 
m.MyClass.f = monkey_f
obj = m.MyClass()
obj.f()
```
The output will be as below:
```python
monkey_f()
```
As we can see, we did make some changes in the behavior of f() in MyClass using the function we defined, monkey_f(), outside of the module m.

* **Does python make use of access specifiers?**

Python does not deprive access to an instance variable or function. Python lays down the concept of prefixing the name of the variable, function or method with a single or double underscore to imitate the behavior of protected and private access specifiers.

More [detail](https://www.tutorialsteacher.com/python/private-and-protected-access-modifiers-in-python)

## Web Framework

### [Django](./web_frameworks/django/README.md)

### [Flask](./web_frameworks/flask/README.md)

