# 📘 System Calls – Complete GATE Notes

---

## 📌 1. What is a System Call?

A **System Call** is a mechanism that allows a **user-level process** to request services from the **Operating System (Kernel)**.

It acts as an interface between:

- 👤 User Mode  
- 🖥️ Kernel Mode  

Whenever a program needs to:
- Access files
- Create processes
- Allocate memory
- Communicate with devices  

It must use a **system call**.

---

## 📌 2. Why Do We Need System Calls?

User programs cannot directly access hardware because:

- ❌ It violates security
- ❌ It may corrupt memory
- ❌ It can crash the OS

Therefore, the OS provides controlled access through system calls.

---

## 📌 3. User Mode vs Kernel Mode

| Feature | User Mode | Kernel Mode |
|----------|------------|-------------|
| Privilege Level | Low | High |
| Hardware Access | ❌ No | ✅ Yes |
| Memory Access | Restricted | Full |
| Crash Impact | Affects Process | Affects Whole System |

### 🔁 Mode Switching

When a system call is invoked:

1. CPU switches from **User Mode → Kernel Mode**
2. OS executes requested service
3. CPU switches back to **User Mode**

This switch is called a **Mode Switch**.

---

## 📌 4. How a System Call Works

### 🔄 Steps Involved

1. User program calls a library function (e.g., `printf()`).
2. Library function prepares system call parameters.
3. A **trap instruction** is executed.
4. CPU switches to Kernel Mode.
5. OS performs requested operation.
6. Result is returned to user program.

---

## 📌 5. Types of System Calls (Very Important for GATE)

### 1️⃣ Process Control

Used for creating and managing processes.

Examples:
- `fork()` → Create new process
- `exec()` → Load new program
- `exit()` → Terminate process
- `wait()` → Wait for child process

---

### 2️⃣ File Management

Used for file operations.

Examples:
- `open()`
- `read()`
- `write()`
- `close()`
- `lseek()`

---

### 3️⃣ Device Management

Used to request and release devices.

Examples:
- `ioctl()`
- `read()`
- `write()`

---

### 4️⃣ Information Maintenance

Used to get or set system data.

Examples:
- `getpid()`
- `alarm()`
- `sleep()`
- `time()`

---

### 5️⃣ Communication (IPC – Inter Process Communication)

Examples:
- `pipe()`
- `shmget()` (Shared Memory)
- `msgget()` (Message Queue)
- `socket()`

---

## 📌 6. System Call vs Function Call

| Feature | Function Call | System Call |
|----------|---------------|-------------|
| Mode Switch | ❌ No | ✅ Yes |
| Speed | Faster | Slower |
| Access Hardware | ❌ No | ✅ Yes |
| Example | `printf()` | `write()` |

> ⚠️ System calls are slower because of context switching overhead.

---

## 📌 7. Important GATE Concepts

### 🔹 Trap

A **software interrupt** used to transfer control from user mode to kernel mode.

---

### 🔹 Context Switch

Saving the state of current process and loading another process.

Occurs during:
- Scheduling
- System calls
- Interrupt handling

---

## 📌 8. fork() – Very Important for GATE

```c
#include <stdio.h>
#include <unistd.h>

int main() {
    int pid = fork();

    if (pid == 0)
        printf("Child Process\n");
    else
        printf("Parent Process\n");

    return 0;
}
```

### 🔎 Behavior of fork()

- Creates a new child process.
- Child gets a copy of parent's memory.
- Both execute independently.

---

### 📊 fork() Return Values

| Return Value | Meaning |
|--------------|----------|
| 0 | In Child Process |
| > 0 | In Parent (Child PID) |
| < 0 | Error |

---

## 📌 9. exec() – Important Concept

The `exec()` system call:

- Replaces the current process image with a new program.
- Does NOT create a new process.
- If successful, it does **NOT return**.

### Example:

```c
#include <unistd.h>

int main() {
    execl("/bin/ls", "ls", NULL);
    return 0;
}
```

After `exec()`:
- Old program code is completely replaced.

---

## 📌 10. fork() vs exec()

| Feature | fork() | exec() |
|----------|---------|---------|
| Creates New Process | ✅ Yes | ❌ No |
| Replaces Process Image | ❌ No | ✅ Yes |
| Returns on Success | ✅ Yes | ❌ No |

---

## 📌 11. Performance Overhead in System Calls

System call overhead includes:

- Mode switching
- Parameter validation
- Security checks
- Context saving & restoring

This makes system calls slower than normal function calls.

---

## 📌 12. Important GATE Practice Areas

✔ Process tree problems using `fork()`  
✔ Count number of processes after multiple forks  
✔ Difference between `fork()` and `exec()`  
✔ Mode switching concept  
✔ Return values of system calls  

---

## 📌 13. Quick Revision Summary

- System call = Interface between user & OS
- Causes User Mode → Kernel Mode switch
- 5 major types of system calls
- `fork()` duplicates process
- `exec()` replaces process


---


