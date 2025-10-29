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
| P2      | 1  | 6  | 23 | 22 - 1 = 22  | 22 - 6 = 16   |
| P3      | 2  | 3  | 11  | 11 - 2 = 9    | 9 - 3 = 6     |
| P4      | 3  | 1  | 12  | 12 - 3 = 9    | 9 - 1 = 8     |
| P5      | 4  | 5  | 24 | 24 - 4 = 20  | 20 - 5 = 15   |
| P6      | 6  | 4  | 21 | 21 - 6 = 15  | 15 - 4 = 11   |

**Average Turnaround Time (TAT)** = (17 + 22 + 9 + 9 + 20 + 15)/6 ≈ 15.33 units  
**Average Waiting Time (WT)** = (12 + 16 + 6 + 8 + 15 + 11)/6 ≈ 11.33 units

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
```
|---P1---|---P1---|---P2---|---P1---|---P3---|---P3---|
0        2        4        6        7        9        11
----------------------------------------------------------
p1       p1=3     p2       p1       p3       p3=2
                  p1=1     p3
         
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

### ⚖️ Comparison with FCFS (Round Robin vs FCFS)

Round Robin scheduling is **very sensitive to time quantum**.

- If the **time quantum is very small**, then **frequent context switching** occurs — the CPU keeps switching between processes too often, which increases overhead.
- If the **time quantum is very large**, then each process runs for a long time before switching — so **preemption rarely happens**, and the algorithm behaves **just like FCFS (First Come First Serve)**.

In short, when the time quantum becomes large enough, **Round Robin ≈ FCFS**.


### 🪶 ব্যাখ্যা

Round Robin মূলত FCFS-এর preemptive রূপ।  
তবে এর আচরণ অনেকটাই **time quantum**-এর উপর নির্ভর করে।

- যদি **time quantum ছোট হয়**, তাহলে **process বারবার switch হয়**, ফলে context switching বেড়ে যায়।
- আর যদি **time quantum বড় হয়**, তখন প্রতিটি process অনেক সময় ধরে চলে এবং preemption প্রায় হয় না।  
  তখন এটি কার্যত **FCFS-এর মতো আচরণ করে**।

অর্থাৎ,  
👉 ছোট quantum → বেশি context switch  
👉 বড় quantum → Round Robin ≈ FCFS

---

### ✅ Round Robin এর Simplified Code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n, quantum;
    cout << "Enter number of processes: ";
    cin >> n;
    cout << "Enter time quantum: ";
    cin >> quantum;

    vector<int> at(n), bt(n), rt(n), ct(n), tat(n), wt(n);
    for (int i = 0; i < n; i++) {
        cout << "P" << i+1 << " (AT BT): ";
        cin >> at[i] >> bt[i];
        rt[i] = bt[i];
    }

    queue<int> q;
    int time = 0, completed = 0;
    vector<bool> inQueue(n, false);

    while (completed < n) {
        // নতুন process আসলে queue তে দাও
        for (int i = 0; i < n; i++) {
            if (at[i] <= time && !inQueue[i] && rt[i] > 0) {
                q.push(i);
                inQueue[i] = true;
            }
        }

        if (q.empty()) {
            time++;
            continue;
        }

        int i = q.front();
        q.pop();

        int execTime = min(quantum, rt[i]);
        rt[i] -= execTime;
        time += execTime;

        // execution চলার সময় নতুন process আসলে enqueue করো
        for (int j = 0; j < n; j++) {
            if (at[j] <= time && !inQueue[j] && rt[j] > 0) {
                q.push(j);
                inQueue[j] = true;
            }
        }

        if (rt[i] == 0) {
            completed++;
            ct[i] = time;
        } else {
            q.push(i); // বাকি আছে, আবার queue তে পাঠাও
        }
    }

    // TAT & WT
    for (int i = 0; i < n; i++) {
        tat[i] = ct[i] - at[i];
        wt[i] = tat[i] - bt[i];
    }

    cout << "\nProcess\tAT\tBT\tCT\tTAT\tWT\n";
    for (int i = 0; i < n; i++) {
        cout << "P" << i+1 << "\t"
             << at[i] << "\t"
             << bt[i] << "\t"
             << ct[i] << "\t"
             << tat[i] << "\t"
             << wt[i] << "\n";
    }
}
```
Worst-case Time : 
O(n × (B / q))

B → Burst Time (BT), q → Time Quantum
