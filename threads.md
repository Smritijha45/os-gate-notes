# 📘 Threads – Complete GATE Notes (Operating Systems)

---

## 📌 1. What is a Thread?

A **Thread** is the smallest unit of CPU execution.

👉 A process can have multiple threads.  
👉 Threads inside a process share the same memory space.

A thread is also called a **lightweight process (LWP)**.

---

## 📌 2. Process vs Thread

| Feature | Process | Thread |
|----------|----------|----------|
| Definition | Program in execution | Smallest execution unit |
| Memory | Separate memory space | Shared memory |
| Overhead | High | Low |
| Context Switch | Expensive | Faster |
| Communication | IPC needed | Easy (shared memory) |

---

## 📌 3. Thread Memory Structure

In a multi-threaded process:

### Shared Among Threads:
- Code (Text segment)
- Data segment
- Heap
- Files

### Separate for Each Thread:
- Thread ID
- Program counter
- Registers
- Stack

---

## 📌 4. Why Use Threads?

✔ Improve responsiveness  
✔ Better CPU utilization  
✔ Parallelism  
✔ Faster context switching  
✔ Efficient communication  

---

## 📌 5. Benefits of Multithreading

### 🔹 1. Responsiveness
Application continues running even if part is blocked.

### 🔹 2. Resource Sharing
Threads share memory and resources.

### 🔹 3. Economy
Thread creation is cheaper than process creation.

### 🔹 4. Scalability
Takes advantage of multi-core processors.

---

## 📌 6. Types of Threads

### 1️⃣ User-Level Threads (ULT)

- Managed by user-level library
- Kernel unaware of threads
- Fast switching
- If one thread blocks → Entire process blocks

---

### 2️⃣ Kernel-Level Threads (KLT)

- Managed by OS kernel
- Kernel schedules each thread
- If one thread blocks → Others can run
- Slower than ULT

---

## 📌 7. Thread Models (Very Important for GATE)

### 🔹 1. Many-to-One Model

Many user threads → One kernel thread

✔ Fast  
❌ Blocking problem  
❌ No parallelism  

---

### 🔹 2. One-to-One Model

One user thread → One kernel thread

✔ True parallelism  
✔ No blocking issue  
❌ High overhead  

---

### 🔹 3. Many-to-Many Model

Many user threads → Many kernel threads

✔ Flexible  
✔ Good concurrency  
✔ Efficient  

---

## 📌 8. Thread Creation in C (POSIX Threads)

```c
#include <pthread.h>
#include <stdio.h>

void* function(void* arg) {
    printf("Thread Running\n");
    return NULL;
}

int main() {
    pthread_t t1;
    pthread_create(&t1, NULL, function, NULL);
    pthread_join(t1, NULL);
    return 0;
}
```

---

## 📌 9. Multithreading Issues (Very Important)

### 🔹 1. Race Condition

When multiple threads access shared data and result depends on execution order.

Example:
```
x = x + 1
```

Two threads executing simultaneously → Incorrect result.

---

### 🔹 2. Critical Section

Part of program where shared resource is accessed.

Only one thread should execute critical section at a time.

---

## 📌 10. Synchronization Tools

### 🔹 1. Mutex

- Mutual exclusion lock
- Only one thread allowed

---

### 🔹 2. Semaphore

Two types:
- Binary semaphore
- Counting semaphore

Used for synchronization.

---

### 🔹 3. Monitor

High-level synchronization construct.

---

## 📌 11. Thread States

1. New  
2. Ready  
3. Running  
4. Blocked  
5. Terminated  

Similar to process states.

---

## 📌 12. Context Switching in Threads

### Thread Context Switch:
- Save registers
- Switch stack pointer
- Load new thread state

👉 Faster than process context switch  
👉 No memory mapping change

---

## 📌 13. Thread vs Process Context Switch

| Feature | Process Switch | Thread Switch |
|----------|----------------|---------------|
| Memory Switch | Yes | No |
| PCB Switch | Yes | No |
| Overhead | High | Low |
| Speed | Slower | Faster |

---

## 📌 14. Multicore and Threads

- Threads can run in parallel on different cores.
- Improves performance in multi-core systems.

Example:
- Web server handling multiple clients simultaneously.

---

## 📌 15. GATE Important Points

✔ Thread models (Many-One, One-One, Many-Many)  
✔ Race condition concept  
✔ Critical section  
✔ Synchronization tools  
✔ Thread vs Process comparison  
✔ Context switch difference  

---

## 📌 16. Quick Revision Summary

- Thread = Smallest execution unit
- Threads share memory
- Faster than processes
- Types: User-level & Kernel-level
- Race condition occurs without synchronization
- Mutex & Semaphore prevent data inconsistency

---


