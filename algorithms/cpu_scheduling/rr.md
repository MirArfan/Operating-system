## ⚙️ Round Robin (RR) CPU Scheduling



### 🧠 Introduction 


Round Robin (RR) is a **preemptive CPU scheduling algorithm** designed especially for **time-sharing systems**.  
Each process is given a fixed **time quantum (time slice)**.  
If a process doesn’t finish within its time quantum, it goes back to the **end of the ready queue**.  
CPU then picks the next process in the ready queue.

### 🔹 
Round Robin (RR) হলো একটি **preemptive CPU scheduling algorithm**,  
বিশেষ করে **time-sharing systems** এর জন্য।  
প্রতিটি প্রসেসকে দেওয়া হয় একটি নির্দিষ্ট **time quantum**।  
যদি প্রসেস তার time quantum এ শেষ না হয়, এটি **ready queue-এর শেষে চলে যায়**।  
CPU তখন ready queue-র পরবর্তী প্রসেস চালায়।



### ⚙️ How RR Works (কাজের নিয়ম)

1. OS সব প্রসেস **ready queue-তে** রাখে **arrival order** অনুযায়ী।  
2. CPU ready queue-এর প্রথম প্রসেস নেয়।  
3. Process **time quantum** পর্যন্ত চলে।  
4. যদি process শেষ না হয় → queue-এর **শেষে ফিরে যায়**।  
5. Ready queue empty না হওয়া পর্যন্ত **repeat**।




### 🧩Example : 1 Processes Table

| Process ID | Arrival Time (AT) | Burst Time (BT) |
|------------|------------------|----------------|
| P1         | 0                | 5              |
| P2         | 1                | 6              |
| P3         | 2                | 3              |
| P4         | 3                | 1              |
| P5         | 4                | 5              |
| P6         | 6                | 4              |

**Time Quantum (TQ) = 4 units**

### 🧮 Step-by-Step Execution (Ready Queue Timeline with Back-to-Queue Logic)

1. **Time 0-4 (P1 Executes)**  
   - P1 starts execution as it arrives at 0 ms.  
   - Runs for 4 units → remaining burst = 5 - 4 = 1  
   - **New arrivals:** P2(1), P3(2), P4(3), P5(4)  
   - **Back to queue:** P1 (remaining 1) is added to the **end of ready queue**  
   - **Ready Queue:** [P2, P3, P4, P5, P1]  

2. **Time 4-8 (P2 Executes)**  
   - P2 runs for 4 units → remaining = 6 - 4 = 2  
   - **New arrivals:** P6(6)  
   - **Back to queue:** P2 (remaining 2) is added to the **end of ready queue**  
   - **Ready Queue:** [P3, P4, P5, P1, P6, P2]  

3. **Time 8-11 (P3 Executes)**  
   - P3 runs for 3 units → finishes → removed  
   - **Back to queue:** None (finished)  
   - **Ready Queue:** [P4, P5, P1, P6, P2]  

4. **Time 11-12 (P4 Executes)**  
   - P4 runs for 1 unit → finishes → removed  
   - **Back to queue:** None (finished)  
   - **Ready Queue:** [P5, P1, P6, P2]  

5. **Time 12-16 (P5 Executes)**  
   - P5 runs for 4 units → remaining = 5 - 4 = 1  
   - **Back to queue:** P5 (remaining 1) is added to the **end of ready queue**  
   - **Ready Queue:** [P1, P6, P2, P5]  

6. **Time 16-17 (P1 Executes)**  
   - P1 runs remaining 1 unit → finishes → removed  
   - **Back to queue:** None (finished)  
   - **Ready Queue:** [P6, P2, P5]  

7. **Time 17-21 (P6 Executes)**  
   - P6 runs 4 units → finishes → removed  
   - **Back to queue:** None (finished)  
   - **Ready Queue:** [P2, P5]  

8. **Time 21-23 (P2 Executes)**  
   - P2 runs remaining 2 units → finishes → removed  
   - **Back to queue:** None (finished)  
   - **Ready Queue:** [P5]  

9. **Time 23-24 (P5 Executes)**  
   - P5 runs remaining 1 unit → finishes → removed  
   - **Back to queue:** None (finished)  
   - **Ready Queue:** []


**Execution Order →** P1 → P2 → P3 → P4 → P5 → P1 → P6 → P2 → P5


### 🧭 Gantt Chart
```
| P1 | P2 | P3 | P4 | P5 | P1 | P6 | P2 | P5 |
0    4    8    11   12   16   17   21   23   24
```

### 📊 Calculations

| Process | AT | BT | CT | TAT = CT - AT | WT = TAT - BT |
|---------|----|----|----|---------------|----------------|
| P1      | 0  | 5  | 17 | 17 - 0 = 17  | 17 - 5 = 12   |
| P2      | 1  | 6  | 22 | 22 - 1 = 21  | 21 - 6 = 15   |
| P3      | 2  | 3  | 9  | 9 - 2 = 7    | 7 - 3 = 4     |
| P4      | 3  | 1  | 9  | 9 - 3 = 6    | 6 - 1 = 5     |
| P5      | 4  | 5  | 24 | 24 - 4 = 20  | 20 - 5 = 15   |
| P6      | 6  | 4  | 21 | 21 - 6 = 15  | 15 - 4 = 11   |

**Average Turnaround Time (TAT)** = (17 + 21 + 7 + 6 + 20 + 15)/6 ≈ 14.33 units  
**Average Waiting Time (WT)** = (12 + 15 + 4 + 5 + 15 + 11)/6 ≈ 10.33 units

### 🧮 Ready Queue Timeline (Time Quantum Wise with Entry & Exit)

| Time | Ready Queue (Before) | Running Process | Notes |
|------|--------------------|----------------|-------|
| 0-4  | [P1]               | P1             | Runs 4 → remaining 1 → back to end |
| 4-8  | [P2,P3,P4,P5,P1]   | P2             | Runs 4 → remaining 2 → back to end; P6 arrives |
| 8-11 | [P3,P4,P5,P1,P6,P2]| P3             | Runs 3 → finishes → removed |
| 11-12| [P4,P5,P1,P6,P2]   | P4             | Runs 1 → finishes → removed |
| 12-16| [P5,P1,P6,P2]      | P5             | Runs 4 → remaining 1 → back to end |
| 16-17| [P1,P6,P2,P5]      | P1             | Runs 1 → finishes → removed |
| 17-21| [P6,P2,P5]         | P6             | Runs 4 → finishes → removed |
| 21-23| [P2,P5]            | P2             | Runs 2 → finishes → removed |
| 23-24| [P5]               | P5             | Runs 1 → finishes → removed |



---


###  🧩 Example : 2



| Process | Burst Time (BT) | Arrival Time (AT) |
|---------|----------------|------------------|
| P1      | 5 ms           | 0 ms             |
| P2      | 2 ms           | 4 ms             |
| P3      | 4 ms           | 5 ms             |

**Time Quantum (TQ) = 2 units**

### 🧭 Gantt Chart
```
| P1 | P1 | P2 | P1 | P3 | P3 |
0    2    4    6    7    9    11
```

### 🧮 Step-by-Step Execution (Ready Queue Timeline & Execution)

1. **Time 0-2 (P1 Executes)**  
   - P1 starts execution as it arrives at 0 ms.  
   - Runs for 2 ms → remaining burst time = 5 - 2 = 3 ms.  
   - **Ready Queue:** [P1]  

2. **Time 2-4 (P1 Executes Again)**  
   - P1 continues execution as no other process has arrived yet.  
   - Runs for 2 ms → remaining burst time = 3 - 2 = 1 ms.  
   - **P2 arrives at 4 ms**  
   - **Ready Queue:** [P2, P1]  

3. **Time 4-6 (P2 Executes)**  
   - P2 starts execution as it arrives at 4 ms.  
   - Runs for 2 ms → remaining burst time = 2 - 2 = 0 ms.  
   - **P3 arrives at 5 ms**  
   - **Ready Queue:** [P1, P3]  

4. **Time 6-7 (P1 Executes)**  
   - P1 resumes execution.  
   - Runs for 1 ms → remaining burst time = 1 - 1 = 0 ms.  
   - **Ready Queue:** [P3]  

5. **Time 7-9 (P3 Executes)**  
   - P3 starts execution.  
   - Runs for 2 ms → remaining burst time = 4 - 2 = 2 ms.  
   - **Ready Queue:** [P3]  

6. **Time 9-11 (P3 Executes Again)**  
   - P3 resumes execution and completes its remaining 2 ms.  
   - Remaining burst time = 2 - 2 = 0 ms.  
   - **Ready Queue:** []  

**Execution Order →** P1 → P1 → P2 → P1 → P3 → P3



### 📊 Calculations

| Process | CT  | TAT = CT - AT | WT = TAT - BT |
|---------|-----|---------------|----------------|
| P1      | 7 ms | 7 - 0 = 7     | 7 - 5 = 2      |
| P2      | 6 ms | 6 - 4 = 2     | 2 - 2 = 0      |
| P3      | 11 ms| 11 - 5 = 6    | 6 - 4 = 2      |

**Average Turnaround Time** = (7 + 2 + 6)/3 = 15/3 = 5 ms  
**Average Waiting Time** = (2 + 0 + 2)/3 = 4/3 ≈ 1.33 ms

---

