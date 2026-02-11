# 📘 Processes – Complete GATE Notes (Operating Systems)

---

## 📌 1. What is a Process?

A **Process** is a program in execution.

👉 A program is a passive entity (stored on disk).  
👉 A process is an active entity (running in memory).

When a program is loaded into memory and begins execution, it becomes a **process**.

---

## 📌 2. Process vs Program

| Feature | Program | Process |
|----------|----------|----------|
| Nature | Passive | Active |
| Stored In | Disk | Main Memory |
| Contains | Instructions | Instructions + State |
| Execution | Not executing | Executing |

---

## 📌 3. Process Memory Layout

A process in memory is divided into:

```
-------------------------
|        Stack          |
-------------------------
|        Heap           |
-------------------------
|        Data Segment   |
-------------------------
|        Text Segment   |
-------------------------
```

### 🔹 Text Segment
- Contains program code
- Read-only

### 🔹 Data Segment
- Global and static variables

### 🔹 Heap
- Dynamic memory allocation
- Grows upward

### 🔹 Stack
- Function calls
- Local variables
- Grows downward

---

## 📌 4. Process States (Very Important for GATE)

### 🔄 Basic 5-State Model

1. **New** → Process is being created  
2. **Ready** → Waiting for CPU  
3. **Running** → Currently executing  
4. **Waiting (Blocked)** → Waiting for I/O  
5. **Terminated** → Finished execution  

---

### 📊 State Transition Diagram

```
New → Ready → Running → Terminated
               ↓
            Waiting
               ↑
               └──── I/O Complete
```

---

## 📌 5. Process Control Block (PCB) – Very Important

Each process has a **PCB** maintained by the OS.

PCB contains:

- Process ID (PID)
- Process state
- Program counter
- CPU registers
- Scheduling information
- Memory management info
- Accounting information
- I/O status info

👉 PCB is stored in kernel space.

---

## 📌 6. Context Switching

### 🔁 What is Context Switch?

When CPU switches from one process to another:

1. Save current process state into PCB
2. Load next process state from PCB

This is called **Context Switching**.

### ⚠ Overhead
- No useful work done
- Purely overhead
- Important in GATE numericals

---

## 📌 7. Types of Processes

### 1️⃣ Foreground Process
- Requires user interaction

### 2️⃣ Background Process
- Runs without user interaction

### 3️⃣ CPU-Bound Process
- Spends more time on computation
- Few I/O operations

### 4️⃣ I/O-Bound Process
- Spends more time on I/O
- Short CPU bursts

👉 Important for scheduling questions.

---

## 📌 8. Process Creation

In UNIX-based systems:

```c
fork();
```

### 🔹 fork()

- Creates a new child process
- Child is exact copy of parent
- Returns:
  - 0 → Child
  - >0 → Parent
  - <0 → Error

---

### Example:

```c
#include <stdio.h>
#include <unistd.h>

int main() {
    fork();
    printf("Hello\n");
    return 0;
}
```

Output:
```
Hello
Hello
```

👉 Because both parent and child execute `printf()`.

---

## 📌 9. Process Termination

Process terminates when:

- It calls `exit()`
- Parent terminates
- Fatal error occurs

### Zombie Process

- Child terminates
- Parent does NOT call `wait()`
- PCB still exists

### Orphan Process

- Parent terminates before child
- Child adopted by `init` process

---

## 📌 10. Inter Process Communication (IPC)

Processes need communication for coordination.

### Two Main Models:

1. **Shared Memory**
2. **Message Passing**

---

### Shared Memory

- Faster
- Processes share common memory
- Requires synchronization

---

### Message Passing

- Send/Receive messages
- Easier to implement
- Slower than shared memory

---

## 📌 11. Scheduling Queues

### Types of Queues

- Job Queue
- Ready Queue
- Device Queue

Processes move between these queues.

---

## 📌 12. Multiprogramming vs Multitasking

| Feature | Multiprogramming | Multitasking |
|----------|------------------|--------------|
| Focus | CPU Utilization | User Interaction |
| Used In | Batch Systems | Interactive Systems |
| Goal | Keep CPU Busy | Quick Response |

---

## 📌 13. Important GATE Concepts

✔ Count number of processes after multiple `fork()`  
✔ Context switch time calculation  
✔ State transition diagram  
✔ PCB contents  
✔ Zombie vs Orphan difference  

---

## 📌 14. fork() Process Count Trick

If `fork()` is called n times:

Total processes = 2ⁿ

Example:

```c
fork();
fork();
```

Total processes = 2² = 4

---

## 📌 15. Quick Revision Summary

- Process = Program in execution
- 5 basic states
- PCB stores process info
- Context switching causes overhead
- fork() duplicates process
- Zombie → Dead but PCB alive
- Orphan → Parent dead

---


