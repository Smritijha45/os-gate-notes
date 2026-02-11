# 📘 Inter-Process Communication (IPC) – Complete GATE Notes (Operating Systems)

---

## 📌 1. What is Inter-Process Communication (IPC)?

**Inter-Process Communication (IPC)** is a mechanism that allows processes to communicate and synchronize with each other.

👉 Processes are isolated by default.  
👉 IPC enables data sharing and coordination.

IPC is required when:
- Processes share data
- Processes cooperate
- Client-server communication is needed

---

## 📌 2. Why IPC is Needed?

✔ Data sharing  
✔ Modularity  
✔ Computation speedup  
✔ Event notification  
✔ Resource sharing  

---

## 📌 3. Two Main IPC Models (Very Important for GATE)

1️⃣ **Shared Memory Model**  
2️⃣ **Message Passing Model**

---

# 🔹 4. Shared Memory Model

In this model:

- A memory region is shared between processes.
- Processes read/write directly to shared memory.
- Requires synchronization.

---

## 📌 Working of Shared Memory

1. Process creates shared memory segment.
2. Other processes attach to it.
3. Data is read/written.
4. Memory is detached and deleted.

---

## 📌 Advantages

✔ Fast (no kernel intervention after setup)  
✔ Suitable for large data  

---

## 📌 Disadvantages

❌ Requires synchronization  
❌ Race conditions possible  

---

## 📌 Shared Memory Example (Conceptual)

```c
shmget();
shmat();
shmdt();
shmctl();
```

---

# 🔹 5. Message Passing Model

Processes communicate by sending and receiving messages.

Two operations:
- `send(message)`
- `receive(message)`

No shared memory required.

---

## 📌 Types of Message Passing

### 1️⃣ Direct Communication

- Processes must name each other.
- Example:
```
send(P, message)
receive(Q, message)
```

---

### 2️⃣ Indirect Communication

- Messages sent via mailbox or port.
- Processes do not directly name each other.

---

## 📌 Advantages

✔ No shared variables  
✔ Easier to implement  
✔ Safe communication  

---

## 📌 Disadvantages

❌ Slower than shared memory  
❌ Kernel intervention required  

---

# 🔹 6. Blocking vs Non-Blocking Communication

## Blocking (Synchronous)

- Sender waits until message is received.
- Receiver waits until message arrives.

---

## Non-Blocking (Asynchronous)

- Sender sends and continues.
- Receiver checks for message.

---

## 📌 Comparison Table

| Feature | Blocking | Non-Blocking |
|----------|----------|--------------|
| Sender Waits | Yes | No |
| Receiver Waits | Yes | No |
| Speed | Slower | Faster |
| Complexity | Simple | Complex |

---

# 🔹 7. Important IPC Mechanisms (GATE Focus)

---

## 1️⃣ Pipe

- Used for communication between related processes.
- Unidirectional.
- Works like a producer-consumer model.

Example:
```c
pipe(fd);
```

---

## 2️⃣ Named Pipe (FIFO)

- Works between unrelated processes.
- Has a name in filesystem.

---

## 3️⃣ Message Queue

- Messages stored in queue.
- Managed by OS.
- Messages have priority.

Functions:
```c
msgget();
msgsnd();
msgrcv();
msgctl();
```

---

## 4️⃣ Shared Memory

Fastest IPC mechanism.

Functions:
```c
shmget();
shmat();
shmdt();
shmctl();
```

---

## 5️⃣ Socket

Used for communication over network.

- Client-Server model
- Can be local or remote

Functions:
```c
socket();
bind();
listen();
accept();
connect();
```

---

# 🔹 8. Shared Memory vs Message Passing

| Feature | Shared Memory | Message Passing |
|----------|---------------|-----------------|
| Speed | Fast | Slower |
| Synchronization | Required | Not Required |
| Kernel Involvement | Minimal | High |
| Suitable For | Large Data | Small Data |

---

# 🔹 9. Race Condition (Important Concept)

Occurs when:

- Multiple processes access shared data
- Final result depends on execution order

Example:
```
x = x + 1
```

Without synchronization → Incorrect result.

---

# 🔹 10. Critical Section

Part of program where shared resource is accessed.

Must ensure:

✔ Mutual Exclusion  
✔ Progress  
✔ Bounded Waiting  

---

# 🔹 11. Synchronization Tools Used in IPC

- Mutex
- Semaphore
- Monitor
- Spinlock

Used to prevent race conditions.

---

# 🔹 12. Producer-Consumer Problem (Classic GATE Topic)

Two processes:

- Producer → Produces data
- Consumer → Consumes data

Uses:
- Shared buffer
- Semaphore for synchronization

---

# 🔹 13. Client-Server Communication

Client:
- Sends request

Server:
- Processes request
- Sends response

Implemented using:
- Sockets
- Message passing

---

# 🔹 14. Important GATE Points

✔ Difference between Shared Memory & Message Passing  
✔ Blocking vs Non-blocking communication  
✔ Race condition concept  
✔ Producer-Consumer problem  
✔ Pipe vs Named Pipe difference  
✔ Socket basics  

---

# 🔹 15. Quick Revision Summary

- IPC = Communication between processes
- Two models: Shared Memory & Message Passing
- Shared memory is fastest
- Message passing is safer
- Synchronization prevents race condition
- Pipes work for related processes
- Named pipes work for unrelated processes

---


