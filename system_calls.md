📘 System Calls – GATE Notes
🔹 1. What is a System Call?

A System Call is a mechanism that allows a user-level process to request services from the Operating System (Kernel).

It acts as an interface between:

🧑‍💻 User Mode

🖥️ Kernel Mode

When a process needs OS services (like file access, memory allocation, process creation), it uses system calls.

🔹 2. Why System Calls Are Needed?

User programs cannot directly access hardware because:

It would compromise security

It may corrupt system data

It can crash the OS

So the OS provides controlled access through system calls.

🔹 3. User Mode vs Kernel Mode
Feature	User Mode	Kernel Mode
Privilege Level	Low	High
Access Hardware	❌ No	✅ Yes
Can Execute System Calls	Yes	Already in Kernel
Crash Impact	Affects Process	Affects Entire System

👉 When a system call is invoked:

CPU switches from User Mode → Kernel Mode

OS executes service

CPU switches back to User Mode

🔹 4. How System Calls Work
Steps:

User program calls library function (e.g., printf())

Library function prepares system call

Trap/Interrupt instruction executed

Control transferred to kernel

Kernel performs task

Returns result to user program

🔹 5. Types of System Calls (Important for GATE)
1️⃣ Process Control

Used for managing processes.

Examples:

fork() → Create new process

exec() → Load new program

exit() → Terminate process

wait() → Wait for child process

2️⃣ File Management

Used for file operations.

Examples:

open()

read()

write()

close()

lseek()

3️⃣ Device Management

Used to request and release devices.

Examples:

ioctl()

read()

write()

4️⃣ Information Maintenance

Used to get/set system data.

Examples:

getpid()

alarm()

sleep()

time()

5️⃣ Communication

Used for Inter Process Communication (IPC)

Examples:

pipe()

shmget() (Shared Memory)

msgget() (Message Queue)

socket()

🔹 6. System Call vs Function Call
Feature	Function Call	System Call
Mode Switch	❌ No	✅ Yes
Speed	Faster	Slower
Access Hardware	❌ No	✅ Yes
Example	printf()	write()

👉 System calls are slower due to context switch overhead.

🔹 7. Important GATE Concepts
🔸 Trap

Software interrupt used to enter kernel mode.

🔸 Context Switch

Saving current process state and loading another.

🔸 Fork Example (Important)
int pid = fork();

if(pid == 0)
    printf("Child Process");
else
    printf("Parent Process");


After fork():

Parent and child execute independently

Both continue from next instruction

🔹 8. Fork() Behavior Table (GATE Favorite)
Return Value	Meaning
0	In Child Process
>0	In Parent (Child PID)
<0	Error
🔹 9. Exec Family (Very Important)

exec() replaces current process image with new program.

Example:

execl("/bin/ls", "ls", NULL);


👉 After exec(), old code is replaced.
👉 If successful, it does NOT return.

🔹 10. Performance Insight

System call overhead includes:

Mode switch

Parameter validation

Security check

Context saving/restoring

🔹 11. GATE Exam Tips 🎯

✅ Difference between fork() and exec() is frequently asked
✅ Return values of system calls are important
✅ Mode switching concept is very important
✅ Process tree questions based on fork()
✅ Count number of processes after multiple forks

🔹 12. Quick Revision Summary

System call = Interface between user & OS

Causes user → kernel mode switch

5 main types:

Process Control

File Management

Device Management

Information Maintenance

Communication

fork() duplicates process

exec() replaces process

Slower than function call