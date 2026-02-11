# 📘 Deadlock – Complete GATE Notes (Operating Systems)

---

# 📌 1. What is Deadlock?

A **Deadlock** is a situation where:

👉 A set of processes are permanently blocked  
👉 Each process is waiting for a resource held by another process  

None of them can proceed.

---

## 📌 Example

Process P1 holds Resource R1 and waits for R2  
Process P2 holds Resource R2 and waits for R1  

➡ Circular waiting occurs  
➡ System gets stuck  

---

# 📌 2. Necessary Conditions for Deadlock (Very Important – GATE Favorite)

All four conditions must hold simultaneously:

---

## 1️⃣ Mutual Exclusion
At least one resource must be non-shareable.

---

## 2️⃣ Hold and Wait
A process holding at least one resource is waiting for another.

---

## 3️⃣ No Preemption
Resources cannot be forcibly taken away.

---

## 4️⃣ Circular Wait
There exists a circular chain of processes.

Example:
```
P1 → P2 → P3 → P1
```

---

⚠ If ANY one condition is removed → Deadlock cannot occur.

---

# 📌 3. Resource Allocation Graph (RAG)

A directed graph used to represent deadlock.

### Nodes:
- Process nodes (Circle)
- Resource nodes (Square)

### Edges:
- Request edge → Process → Resource
- Assignment edge → Resource → Process

---

## 📌 Deadlock in RAG

✔ If graph has **NO cycle** → No deadlock  
✔ If graph has cycle:
   - Single instance per resource → Deadlock
   - Multiple instances → Possibly deadlock

---

# 📌 4. Methods for Handling Deadlock

There are 4 approaches:

1️⃣ Deadlock Prevention  
2️⃣ Deadlock Avoidance  
3️⃣ Deadlock Detection & Recovery  
4️⃣ Ignore (Ostrich Algorithm)

---

# 📌 5. Deadlock Prevention

Break at least one of the 4 necessary conditions.

---

## 🔹 1. Eliminate Mutual Exclusion

Make resources sharable (Not always possible).

---

## 🔹 2. Eliminate Hold and Wait

Process must request all resources at once.

❌ Low resource utilization

---

## 🔹 3. Eliminate No Preemption

Allow preemption of resources.

---

## 🔹 4. Eliminate Circular Wait

Impose resource ordering.

Example:
R1 < R2 < R3  
Processes must request in increasing order.

---

# 📌 6. Deadlock Avoidance

System checks before allocation to ensure safe state.

---

## 🔹 Safe State

A system is in safe state if:

There exists a sequence of processes such that  
each can complete execution.

---

## 🔹 Unsafe State

Unsafe ≠ Deadlock  
Unsafe means deadlock *may* occur.

---

# 📌 7. Banker’s Algorithm (Very Important for GATE)

Used for deadlock avoidance.

---

## 📌 Data Structures

For n processes and m resources:

- Available[m]
- Max[n][m]
- Allocation[n][m]
- Need[n][m] = Max - Allocation

---

## 📌 Safety Algorithm Steps

1. Find process whose Need ≤ Available
2. Assume it finishes
3. Release its resources
4. Repeat

If all processes finish → Safe state  
If not → Unsafe

---

# 📌 8. Banker’s Example (Conceptual)

If:
```
Available = [3 3 2]
Need of P1 = [1 2 2]
```

Since Need ≤ Available → P1 can execute safely.

---

# 📌 9. Deadlock Detection

Used when system does NOT prevent or avoid.

---

## 🔹 Single Instance Per Resource

If RAG contains cycle → Deadlock exists

---

## 🔹 Multiple Instances

Use detection algorithm similar to Banker’s.

---

# 📌 10. Deadlock Recovery

After detection:

---

## 🔹 1. Process Termination

- Abort all processes
- Abort one by one

---

## 🔹 2. Resource Preemption

- Select victim
- Rollback
- Restart process

---

# 📌 11. Ostrich Algorithm

Ignore deadlock problem.

Used in:
- UNIX
- Windows

Assumption:
Deadlock occurs rarely.

---

# 📌 12. Comparison Table

| Method | Guarantee | Overhead |
|--------|-----------|----------|
| Prevention | No Deadlock | High |
| Avoidance | No Deadlock | Moderate |
| Detection | Deadlock may occur | Moderate |
| Ignore | No handling | Low |

---

# 📌 13. Deadlock vs Starvation

| Feature | Deadlock | Starvation |
|----------|----------|------------|
| Waiting | Infinite | Infinite |
| Cause | Circular wait | Scheduling |
| Resolution | External action needed | Priority adjustment |

---

# 📌 14. Important GATE Points

✔ 4 necessary conditions  
✔ Resource Allocation Graph  
✔ Safe vs Unsafe state  
✔ Banker’s Algorithm numericals  
✔ Prevention techniques  
✔ Deadlock vs Starvation  

---

# 📌 15. Quick Revision Summary

- Deadlock = Circular waiting
- 4 necessary conditions must hold
- RAG used for detection
- Banker’s Algorithm used for avoidance
- Safe state ensures no deadlock
- Prevention breaks one condition
- Detection + Recovery possible

---


