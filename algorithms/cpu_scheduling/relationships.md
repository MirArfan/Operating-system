# 🔗 Relationship Between CPU Scheduling Algorithms

### 🧩 Overview
বেশিরভাগ CPU Scheduling Algorithm-এর মধ্যে কিছু মিল (similarity) ও পার্থক্য (difference) আছে।  
এরা একে অপরের **extended** বা **modified** version হিসেবে কাজ করে।



### ⚖️ 1. FCFS (First Come First Serve)
**Nature:** Non-preemptive  
**Idea:** যে process আগে আসে, CPU আগে পায়।  
**Relation:**
- Round Robin (RR) basically **extends FCFS** by adding a **time quantum** (preemption).
- When **RR time quantum → ∞**, RR behaves exactly like FCFS.
- **SJF (Shortest Job First)** can be seen as an **optimized form** of FCFS (instead of arrival time, SJF uses burst time).

🪶 **Summary:**  
FCFS → oldest & simplest → forms the base for many other algorithms.

---

### ⏱️ 2. SJF (Shortest Job First)
**Nature:** Non-preemptive (but has a preemptive version SRTF)  
**Idea:** The process with the smallest burst time is executed first.  
**Relation:**
- **SRTF (Shortest Remaining Time First)** is the **preemptive version** of SJF.
- **SJF** is efficient in minimizing average waiting time but can cause **starvation** (long jobs wait).
- FCFS can be seen as a **special case of SJF** when all burst times are equal.

🪶 **Summary:**  
SJF → Focus on efficiency, not fairness.

---

### ⚡ 3. SRTF (Shortest Remaining Time First)
**Nature:** Preemptive version of SJF  
**Idea:** Process with the least remaining CPU time gets CPU next.  
**Relation:**
- **SRTF → preemptive SJF**
- If **no new process arrives**, SRTF behaves like **SJF**.
- If burst time knowledge unavailable, it can’t be implemented — same limitation as SJF.

🪶 **Summary:**  
SRTF = Preemptive SJF (better response time, more overhead)

---

### 👑 4. Priority Scheduling
**Nature:** Can be Preemptive or Non-preemptive  
**Idea:** Process with **highest priority (smallest number)** runs first.  
**Relation:**
- **SJF is a special case of Priority Scheduling**, where **priority = 1 / burst time.**
- **Round Robin** removes starvation problem of Priority Scheduling.
- **FCFS** can also be treated as Priority Scheduling if we assign **priority = arrival order.**

🪶 **Summary:**  
Priority = importance-based scheduling;  
SJF is basically Priority Scheduling with burst-time-based priority.

---

### 🔁 5. Round Robin (RR)
**Nature:** Preemptive  
**Idea:** Each process gets equal CPU time slice (quantum) in circular order.  
**Relation:**
- RR = **Preemptive version of FCFS** with time quantum.
- When **quantum → large**, RR ≈ FCFS.
- When **quantum → small**, RR ≈ SRTF (frequent switching).
- Fixes starvation problem of **Priority Scheduling** and **SJF**.
- Often used **inside Multilevel Queue Scheduling**.

🪶 **Summary:**  
RR focuses on fairness and response time — combines features of several algorithms.

---

### 🧮 Summary Table

| Algorithm | Type | Based On | Related / Derived From | Similar Behavior |
|------------|------|-----------|-------------------------|------------------|
| **FCFS** | Non-preemptive | Arrival Time | Base Algorithm | RR (when large quantum) |
| **SJF** | Non-preemptive | Shortest Burst | FCFS (optimized) | Priority (if priority = 1/BT) |
| **SRTF** | Preemptive | Remaining Burst | SJF | RR (if quantum very small) |
| **Priority** | Both | Priority Value | Generalized Form | SJF (special case) |
| **Round Robin** | Preemptive | Time Quantum | FCFS (extended) | SRTF (if quantum small) |

---

### 🧠 Key Insights (Bangla Summary)
- **FCFS →** মূল ভিত্তি algorithm, সবচেয়ে simple।
- **SJF →** efficiency বাড়ায়, কিন্তু starvation ঘটায়।
- **SRTF →** SJF-এর preemptive সংস্করণ।
- **Priority →** importance ভিত্তিক scheduling, কিন্তু starvation prone।
- **RR →** fairness নিশ্চিত করে, starvation দূর করে, FCFS ও Priority-এর মাঝামাঝি nature।

---

✅ **In short:**
> 🔸 RR behaves like FCFS when time quantum → large.  
> 🔸 RR behaves like SRTF when time quantum → very small.  
> 🔸 SJF is a special case of Priority Scheduling.  
> 🔸 SRTF is the preemptive version of SJF.  
> 🔸 All of them evolve from FCFS — the simplest scheduling algorithm.
