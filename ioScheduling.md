# 📘 CPU Scheduling & I/O Scheduling – Complete GATE Notes (Operating Systems)

---

# 🔷 PART 1: CPU SCHEDULING

---

# 📌 1. What is CPU Scheduling?

**CPU Scheduling** is the process of selecting one process from the ready queue and allocating the CPU to it.

Goal:
✔ Maximize CPU utilization  
✔ Minimize waiting time  
✔ Minimize turnaround time  
✔ Minimize response time  
✔ Maximize throughput  

---

# 📌 2. Important Terminologies (Very Important for GATE)

### 🔹 Arrival Time (AT)
Time at which process enters ready queue.

### 🔹 Burst Time (BT)
Total CPU time required by process.

### 🔹 Completion Time (CT)
Time at which process finishes execution.

### 🔹 Turnaround Time (TAT)
```
TAT = CT - AT
```

### 🔹 Waiting Time (WT)
```
WT = TAT - BT
```

### 🔹 Response Time (RT)
```
RT = First CPU allocation time - Arrival time
```

---

# 📌 3. Types of Schedulers

1️⃣ Long-term Scheduler (Job Scheduler)  
2️⃣ Short-term Scheduler (CPU Scheduler)  
3️⃣ Medium-term Scheduler  

---

# 📌 4. Preemptive vs Non-Preemptive Scheduling

| Feature | Preemptive | Non-Preemptive |
|----------|------------|----------------|
| CPU Taken Away | Yes | No |
| Response Time | Better | Slower |
| Complexity | High | Low |
| Example | Round Robin | FCFS |

---

# 📌 5. CPU Scheduling Algorithms (GATE Favorite)

---

# 🔹 1. FCFS (First Come First Serve)

- Non-preemptive
- Process with smallest arrival time executes first

✔ Simple  
❌ Convoy effect  
❌ Poor average waiting time  

---

# 🔹 2. SJF (Shortest Job First)

- Process with smallest burst time executes first
- Non-preemptive

✔ Optimal average waiting time  
❌ Requires burst time prediction  

---

# 🔹 3. SRTF (Shortest Remaining Time First)

- Preemptive version of SJF
- Process with smallest remaining time runs

✔ Better than SJF  
❌ Starvation possible  

---

# 🔹 4. Priority Scheduling

- Each process assigned priority
- Highest priority executes first

✔ Important tasks handled first  
❌ Starvation possible  

---

## ⭐ Aging

Solution to starvation:
Gradually increase priority of waiting processes.

---

# 🔹 5. Round Robin (RR)

- Time quantum (q) given
- Each process gets q time
- Preemptive

✔ Good for time-sharing systems  
✔ Fair scheduling  
❌ High context switching if q too small  

---

# 📌 6. Comparison of CPU Algorithms

| Algorithm | Preemptive | Starvation | Avg WT |
|------------|------------|------------|--------|
| FCFS | No | No | High |
| SJF | No | Yes | Minimum |
| SRTF | Yes | Yes | Very Low |
| Priority | Yes/No | Yes | Medium |
| RR | Yes | No | Medium |

---

# 📌 7. Important GATE Points (CPU Scheduling)

✔ Calculate WT, TAT, RT  
✔ Draw Gantt chart  
✔ Compare average waiting time  
✔ Starvation concept  
✔ Convoy effect  
✔ Effect of time quantum  

---

---

# 🔷 PART 2: I/O (DISK) SCHEDULING

---

# 📌 8. What is Disk Scheduling?

Disk scheduling decides the order in which disk I/O requests are serviced.

Goal:
✔ Minimize seek time  
✔ Maximize throughput  
✔ Reduce response time  

---

## 🔹 Seek Time
Time taken to move disk arm to required track.

---

# 📌 9. Disk Scheduling Algorithms (Very Important)

---

# 🔹 1. FCFS (Disk)

- Requests served in arrival order
- Fair but high seek time

---

# 🔹 2. SSTF (Shortest Seek Time First)

- Select request closest to current head position

✔ Reduced seek time  
❌ Starvation possible  

---

# 🔹 3. SCAN (Elevator Algorithm)

- Head moves in one direction
- Services requests
- Reverses at end

✔ Better performance  
✔ No starvation  

---

# 🔹 4. C-SCAN (Circular SCAN)

- Head moves in one direction only
- After reaching end, jumps to beginning

✔ Uniform waiting time  

---

# 🔹 5. LOOK

- Like SCAN
- Stops at last request (not physical end)

---

# 🔹 6. C-LOOK

- Like C-SCAN
- Jumps to first request after last request

---

# 📌 10. Comparison of Disk Scheduling

| Algorithm | Starvation | Seek Time | Fairness |
|------------|------------|-----------|----------|
| FCFS | No | High | High |
| SSTF | Yes | Low | Low |
| SCAN | No | Medium | Medium |
| C-SCAN | No | Medium | High |
| LOOK | No | Better than SCAN | Medium |

---

# 📌 11. Important GATE Tricks (Disk Scheduling)

✔ Always calculate total head movement  
✔ Draw number line  
✔ Check initial head position  
✔ Direction matters in SCAN & C-SCAN  

---

# 📌 12. CPU Scheduling vs Disk Scheduling

| Feature | CPU Scheduling | Disk Scheduling |
|----------|----------------|-----------------|
| Focus | CPU allocation | Disk head movement |
| Metric | WT, TAT, RT | Seek time |
| Algorithms | SJF, RR | SSTF, SCAN |

---

# 📌 13. Quick Revision Summary

CPU Scheduling:
- Selects process from ready queue
- SJF gives minimum average waiting time
- RR good for time-sharing
- Starvation possible in SJF & Priority

Disk Scheduling:
- Minimizes seek time
- SSTF fastest but may starve
- SCAN = Elevator
- C-SCAN gives uniform waiting time

---


