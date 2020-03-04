# Concurrent Programing Interview questions

* **Why is testing multithreaded/concurrent code so difficult?**

Your test might be multithreaded/concurrent too then it causes complex things happen. Testing should be simple so that it can verify your code.

* **Multithreading vs Multiprocessing**

Multithreading mean you span threads within a process which share the same memory space.

Multiprocessing mean that you run your code in different process. Only multiprocess can make code running parallel.

* **What is a race condition? Code an example, using whatever language you like and resolve it**

* **What is a race condition?**

This is one of the major issues in concurrent programming. Concurrent access to shared resources can lead to race condition. A race condition may be defined as the occurring of a condition when two or more threads can access shared data and then try to change its value at the same time. Due to this, the values of variables may be unpredictable and vary depending on the timings of context switches of the processes.

* Code example

```python
import threading

x = 0

def increment_global():

   global x
   x += 1

def taskofThread():

   for _ in range(50000):
      increment_global()

def main():
   global x
   x = 0

   t1 = threading.Thread(target= taskofThread)
   t2 = threading.Thread(target= taskofThread)

   t1.start()
   t2.start()

   t1.join()
   t2.join()

if __name__ == "__main__":
   for i in range(5):
      main()
      print("x = {1} after Iteration {0}".format(i,x))

```

In the output shown below, we can see the effect of race condition as the value of x after each iteration is expected 100000. However, there is lots of variation in the value. This is due to the concurrent access of threads to the shared global variable x.

Output

```python
x = 100000 after Iteration 0
x = 54034 after Iteration 1
x = 80230 after Iteration 2
x = 93602 after Iteration 3
x = 93289 after Iteration 4
```

* Resolve

Using **lock**

```python
import threading

x = 0

def increment_global():

   global x
   x += 1

def taskofThread(lock):

   for _ in range(50000):
      lock.acquire()
      increment_global()
      lock.release()

def main():
   global x
   x = 0

   lock = threading.Lock()
   t1 = threading.Thread(target = taskofThread, args = (lock,))
   t2 = threading.Thread(target = taskofThread, args = (lock,))

   t1.start()
   t2.start()

   t1.join()
   t2.join()

if __name__ == "__main__":
   for i in range(5):
      main()
      print("x = {1} after Iteration {0}".format(i,x))
```

* **What is a deadlock? Would you be able to write some code that is affected by deadlocks?**

    - What is a deadlock?

Deadlock happen when you write thread code that tries to acquire more than one mutex lock at once

    - Example

```python
a_lock = threading.Lock()
b_lock = threading.Lock()

def foo():
    with a_lock:
         ...
         with b_lock:
              # Do something
              ...

def bar():
    with b_lock:
         ...
         with a_lock:
              # Do something (maybe)
              ...

t1 = threading.Thread(target=foo)
t1.start()
t2 = threading.Thread(target=bar)
t2.start()
```

**How to resolve**

    - Enforcement of ordering rule
    - Assigning each lock in a unique manner to the program.
    - Only allowing multiple locks to be acquired in ascending order.

Sample solution in python

```python
with acquire(lock_state_2, lock_state_1):
with acquire(lock_state_1, lock_state_2:
```

* **What is process starvation? If you need, let's review its definition.**

Starvation is the phenomena in which a process is not able to acquire the desired resources (like processor, I/O device etc) for a very long time to progress with its execution.

* **What is a wait free algorithm?**

There are two types of non-blocking thread synchronization algorithms - lock-free, and wait-free. Their meaning is often confused. In lock-free systems, while any particular computation may be blocked for some period of time, all CPUs are able to continue performing other computations. To put it differently, while a given thread might be blocked by other threads in a lock-free system, all CPUs can continue doing other useful work without stalls. Lock-free algorithms increase the overall throughput of a system by occassionally increasing the latency of a particular transaction. Most high- end database systems are based on lock-free algorithms, to varying degrees.

By contrast, wait-free algorithms ensure that in addition to all CPUs continuing to do useful work, no computation can ever be blocked by another computation. Wait-free algorithms have stronger guarantees than lock-free algorithms, and ensure a high thorughput without sacrificing latency of a particular transaction. They’re also much harder to implement, test, and debug. The lockless page cache patches to the Linux kernel are an example of a wait-free system.
In a situation where a system handles dozens of concurrent transactions and has soft latency requirements, lock-free systems are a good compromise between development complexity and high concurrency requirements. A database server for a website is a good candidate for a lock-free design. While any given transaction might block, there are always more transactions to process in the meantime, so the CPUs will never stay idle. The challenge is to build a transaction scheduler that maintains a good mean latency, and a well bounded standard deviation.

In a scenario where a system has roughly as many concurrent transactions as CPU cores, or has hard real-time requirements, the developers need to spend the extra time to build wait-free systems. In these cases blocking a single transaction isn’t acceptable - either because there are no other transactions for the CPUs to handle, minimizing the throughput, or a given transaction needs to complete with a well defined non-probabilistic time period. Nuclear reactor control software is a good candidate for wait-free systems.

For example, RethinkDB is a lock-free system. On a machine with N CPU cores, under most common workloads, we can gurantee that no core will stay idle and no IO pipeline capacity is wasted as long as there are roughly N * 4 concurrent transactions. For example, on an eight core system, no piece of hardware will sit idle if RethinkDB is handling roughly 32 concurrent transactions or more. If there are fewer than 32 transactions, you’ve likely overpaid for some of the cores. (Of course if you only have 32 concurrent transactions, you don’t need an eight-core machine).