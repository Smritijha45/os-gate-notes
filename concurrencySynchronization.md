# 📘 Concurrency & Synchronization – Complete GATE Notes (Operating Systems)

---

# 📌 1. What is Concurrency?

**Concurrency** is the ability of a system to execute multiple tasks simultaneously (logically overlapping in time).

👉 It does NOT always mean parallel execution.  
👉 On single CPU → Tasks interleave.  
👉 On multi-core → Tasks may run in parallel.

---

## 📌 Concurrency vs Parallelism

| Feature | Concurrency | Parallelism |
|----------|-------------|-------------|
| Meaning | Multiple tasks in progress | Multiple tasks executing simultaneously |
| CPU Required | Single or Multiple | Multiple cores |
| Example | Time sharing | Multi-core execution |

---

# 📌 2. Why Concurrency is Needed?

✔ Better CPU utilization  
✔ Faster program execution  
✔ Responsiveness  
✔ Resource sharing  
✔ Scalable systems  

---

# 📌 3. Problems in Concurrency

When multiple processes/threads access shared resources:

❌ Race Condition  
❌ Data inconsistency  
❌ Deadlock  
❌ Starvation  

---

# 📌 4. Race Condition (Very Important)

A **race condition** occurs when:

- Two or more processes access shared data
- At least one modifies the data
- Final result depends on execution order

---

## Example

```
x = 5

Process P1: x = x + 1
Process P2: x = x + 1
```

Expected result = 7  
Possible result = 6 (due to interleaving)

---

# 📌 5. Critical Section Problem

A **Critical Section** is a part of program where shared resource is accessed.

We must ensure:

1️⃣ Mutual Exclusion  
2️⃣ Progress  
3️⃣ Bounded Waiting  

---

## Structure of Process

```
do {
    Entry Section
    Critical Section
    Exit Section
    Remainder Section
} while(true);
```

---

# 📌 6. Requirements for Solution (GATE Favorite)

### 1️⃣ Mutual Exclusion
Only one process in critical section at a time.

### 2️⃣ Progress
If no process in critical section, decision must not be postponed indefinitely.

### 3️⃣ Bounded Waiting
A process should not wait forever.

---

# 📌 7. Software Solutions for Synchronization

---

## 🔹 1. Peterson’s Solution (Two Processes Only)

Uses:
- Two flags
- Turn variable

### Code:

```c
flag[i] = true;
turn = j;

while(flag[j] && turn == j);

Critical Section

flag[i] = false;
```

✔ Satisfies all three conditions  
❌ Works only for two processes  

---

## 🔹 2. Bakery Algorithm

- Works for multiple processes
- Based on ticket numbering system

Each process gets a number.  
Smallest number enters critical section first.

---

# 📌 8. Hardware Solutions

---

## 🔹 1. Test-and-Set Instruction

Atomic hardware instruction.

```c
while(TestAndSet(lock));
```

Ensures atomicity.

---

## 🔹 2. Compare-and-Swap

Atomically compares and swaps values.

---

# 📌 9. Synchronization Tools (Most Important Section)

---

## 🔹 1. Mutex (Mutual Exclusion Lock)

- Binary lock
- Only one thread allowed

Operations:
```
lock()
unlock()
```

---

## 🔹 2. Semaphore

A semaphore is an integer variable accessed through atomic operations.

### Types:

1️⃣ Binary Semaphore (0 or 1)  
2️⃣ Counting Semaphore  

---

### Semaphore Operations:

```
wait(S)   → S = S - 1
signal(S) → S = S + 1
```

---

### Semaphore Example:

```c
wait(mutex);
// Critical Section
signal(mutex);
```

---

# 📌 10. Producer-Consumer Problem

Two processes:

- Producer → Produces data
- Consumer → Consumes data

Uses:
- Buffer
- Full semaphore
- Empty semaphore
- Mutex

---

# 📌 11. Readers-Writers Problem

Two types of processes:

- Readers → Only read
- Writers → Modify data

Rules:
- Multiple readers allowed
- Only one writer allowed
- Writer gets exclusive access

---

# 📌 12. Dining Philosophers Problem

Classic synchronization problem.

Issues:
❌ Deadlock  
❌ Starvation  

Solution:
- Resource hierarchy
- At most 4 philosophers at table
- Use semaphores

---

# 📌 13. Deadlock (Brief Overview)

Deadlock occurs when processes wait indefinitely for resources.

### Necessary Conditions:

1️⃣ Mutual Exclusion  
2️⃣ Hold and Wait  
3️⃣ No Preemption  
4️⃣ Circular Wait  

---

# 📌 14. Spinlock vs Mutex

| Feature | Spinlock | Mutex |
|----------|----------|--------|
| Waiting | Busy waiting | Sleeps |
| CPU Usage | High | Low |
| Best For | Short wait | Long wait |

---

# 📌 15. Busy Waiting

Process continuously checks condition.

Waste of CPU cycles.

---

# 📌 16. Context Switch in Synchronization

When a process waits:
- State saved
- CPU given to another process
- Causes overhead

---

# 📌 17. Important GATE Points

✔ Race condition definition  
✔ Critical section requirements  
✔ Peterson’s solution  
✔ Semaphore operations  
✔ Producer-Consumer  
✔ Readers-Writers  
✔ Dining Philosophers  
✔ Deadlock conditions  

---

# 📌 18. Quick Revision Summary

- Concurrency = Multiple tasks in progress
- Race condition occurs without synchronization
- Critical section must satisfy 3 conditions
- Peterson works for 2 processes
- Semaphore prevents race condition
- Producer-Consumer is classic problem
- Deadlock requires 4 conditions

---

