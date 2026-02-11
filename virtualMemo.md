# 📘 Virtual Memory – Complete GATE Notes (Operating Systems)

---

# 📌 1. What is Virtual Memory?

**Virtual Memory** is a memory management technique that allows execution of processes 
that are not completely loaded into physical memory.

👉 Logical memory can be larger than physical memory.  
👉 Only required pages are loaded into RAM.

---

# 📌 2. Why Virtual Memory is Needed?

✔ Allows large programs to run  
✔ Increases degree of multiprogramming  
✔ Efficient memory utilization  
✔ Provides memory isolation  

---

# 📌 3. Concept of Virtual Address Space

Each process has its own:

```
Logical (Virtual) Address Space
```

This is mapped to:

```
Physical Memory (RAM)
```

Mapping is done using:
- Page table
- MMU (Memory Management Unit)

---

# 📌 4. Demand Paging (Very Important for GATE)

Pages are loaded into memory only when required.

---

## 🔹 Page Fault

Occurs when:

- CPU references a page
- Page is not in memory

---

## 🔹 Steps in Handling Page Fault

1. Trap to OS
2. Validate memory reference
3. Find free frame
4. Load page from disk
5. Update page table
6. Restart instruction

---

# 📌 5. Page Fault Types

1️⃣ Minor Page Fault → Page in memory but not mapped  
2️⃣ Major Page Fault → Page must be loaded from disk  

---

# 📌 6. Performance of Demand Paging

Let:

- p = page fault rate  
- ma = memory access time  
- pf = page fault service time  

---

## 🔹 Effective Access Time (EAT)

```
EAT = (1 - p) × ma + p × pf
```

Even small p increases EAT drastically.

---

# 📌 7. Page Replacement

When no free frame available, OS must replace a page.

---

# 📌 8. Page Replacement Algorithms (Very Important)

---

## 🔹 1. FIFO (First In First Out)

- Replace oldest page.

✔ Simple  
❌ Belady’s Anomaly possible  

---

## 🔹 2. Optimal

- Replace page not used for longest future time.

✔ Minimum page faults  
❌ Theoretical only  

---

## 🔹 3. LRU (Least Recently Used)

- Replace least recently used page.

✔ Close to optimal  
❌ Requires tracking usage  

---

## 🔹 4. Second Chance (Clock Algorithm)

- Improvement over FIFO  
- Uses reference bit  

If reference bit = 1 → give second chance  
If 0 → replace  

---

## 🔹 5. LFU (Least Frequently Used)

- Replace least frequently used page.

---

# 📌 9. Belady’s Anomaly

Increasing number of frames increases page faults.

Occurs in:
✔ FIFO  
❌ Not in LRU or Optimal  

---

# 📌 10. Frame Allocation

When multiple processes exist:

---

## 🔹 1. Equal Allocation
Each process gets equal frames.

---

## 🔹 2. Proportional Allocation
Frames allocated based on process size.

---

# 📌 11. Global vs Local Replacement

| Feature | Global | Local |
|----------|--------|--------|
| Replacement Scope | All processes | Only same process |
| Performance | Better overall | Predictable |
| Risk | May cause starvation | Less flexible |

---

# 📌 12. Thrashing (Very Important)

Thrashing occurs when:

- System spends more time handling page faults
- CPU utilization decreases

---

## 🔹 Causes

- Insufficient frames
- High degree of multiprogramming

---

## 🔹 Solution

✔ Reduce multiprogramming  
✔ Use Working Set Model  
✔ Page Fault Frequency control  

---

# 📌 13. Working Set Model

Working set = Pages used in last Δ time.

If working set > available frames → Thrashing occurs.

---

# 📌 14. Page Fault Frequency (PFF)

Controls page fault rate.

If p too high → Allocate more frames  
If p too low → Remove frames  

---

# 📌 15. Copy-On-Write (COW)

Used in:

- fork()

Child shares pages with parent until modification.

✔ Saves memory  
✔ Efficient process creation  

---

# 📌 16. Memory-Mapped Files

File contents mapped directly to memory.

Advantages:
✔ Faster I/O  
✔ Efficient file access  

---

# 📌 17. Demand Paging vs Pre-Paging

| Feature | Demand Paging | Pre-Paging |
|----------|---------------|------------|
| Load Pages | On demand | In advance |
| Page Faults | Higher initially | Lower |
| Memory Use | Efficient | May waste memory |

---

# 📌 18. Important GATE Points

✔ EAT calculation  
✔ Page fault handling steps  
✔ Belady’s anomaly  
✔ LRU vs FIFO comparison  
✔ Thrashing concept  
✔ Working set  
✔ Global vs Local replacement  

---

# 📌 19. Quick Revision Summary

- Virtual memory allows large programs to run
- Demand paging loads pages on request
- Page fault increases access time
- FIFO may cause Belady’s anomaly
- LRU better than FIFO
- Thrashing reduces CPU utilization
- Working set prevents thrashing
- Copy-on-write saves memory

---


