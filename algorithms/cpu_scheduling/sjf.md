## ⚙️ SJF – Shortest Job First CPU Scheduling


### 🧠 Introduction

Shortest Job First (SJF) is a **non-preemptive CPU scheduling algorithm** where the process with the shortest burst time is selected next for execution.  
In simple terms, the process that requires less CPU time gets executed first.


Shortest Job First (SJF) একটি **non-preemptive CPU scheduling algorithm**,  
যেখানে সেই প্রসেসটি আগে চলবে যার **burst time সবচেয়ে ছোট**।  
অর্থাৎ, যে প্রসেসের কাজ শেষ করতে কম সময় লাগে, সেটিই CPU আগে পায়।



### ⚙️ How SJF Works (কাজ করার নিয়ম)

1. All processes are arranged in the **ready queue** based on their burst time (shortest first).  
2. The CPU selects the process with the **lowest burst time** and executes it until completion.  
3. Once it finishes, the next shortest job is chosen.  
4. This continues until all processes are completed.



### 📘 Advantages & Disadvantages

#### ✅ Advantages:
- Minimizes **average waiting time**.
- Improves **throughput** for short processes.

#### ❌ Disadvantages:
- Requires **prior knowledge of burst time**.
- Causes **starvation** for long processes.
- Not suitable for **real-time systems**.



### 🧩 Example

| Process | Arrival Time (AT) | Burst Time (BT) |
|---------|------------------|----------------|
| P1      | 0                | 7              |
| P2      | 2                | 4              |
| P3      | 4                | 1              |
| P4      | 5                | 4              |



### 🔹 Step 1: Scheduling Order

SJF selects the **available process with the shortest burst time** at any given time.  

**Execution order (with arrival time considered):**  
1. At time 0 → only P1 has arrived → execute P1  
2. At time 7 → P2 (AT=2), P3 (AT=4), P4 (AT=5) have arrived → P3 has shortest BT=1 → execute P3  
3. At time 8 → P2 (BT=4), P4 (BT=4) → tie, choose earlier arrival → P2  
4. At time 12 → only P4 remains → execute P4

<br>


### 🔹 Step 2: Calculate CT, TAT, WT

| Process | AT | BT | CT | TAT = CT−AT | WT = TAT−BT |
|---------|----|----|----|-------------|--------------|
| P1      | 0  | 7  | 7  | 7−0=7       | 7−7=0        |
| P2      | 2  | 4  | 12 | 12−2=10     | 10−4=6       |
| P3      | 4  | 1  | 8  | 8−4=4       | 4−1=3        |
| P4      | 5  | 4  | 16 | 16−5=11     | 11−4=7       |

<br>

### 🔹 Step 3: Gantt Chart
```
| P1 | P3 | P2 | P4 |
0    7    8    12   16
```


### 🔹 Step 4: Average Times

- Average TAT = (7 + 10 + 4 + 11) / 4 = 8  
- Average WT  = (0 + 6 + 3 + 7) / 4 = 4  

---


### 🧩 Example 2: Different Arrival Times

| Process | Arrival Time (AT) | Burst Time (BT) |
|---------|------------------|----------------|
| P1      | 2                | 6              |
| P2      | 5                | 2              |
| P3      | 1                | 8              |
| P4      | 0                | 3              |



### 🧮 Step-by-Step Execution

| Time | Arrived Processes | Shortest Job | Process Running |
|------|-----------------|--------------|----------------|
| 0    | P4              | P4           | P4             |
| 3    | P3, P1          | P1           | P1             |
| 9    | P2, P3          | P2           | P2             |
| 11   | P3              | P3           | P3             |

**Execution Order →** P4 → P1 → P2 → P3
### 🧭 Gantt Chart
```
|---P4---|------P1------|--P2--|---------P3---------|
0        3              9      11                  19
```




### 📊 Calculations

| Process | AT | BT | CT | TAT = CT - AT | WT = TAT - BT |
|---------|----|----|----|---------------|----------------|
| P4      | 0  | 3  | 3  | 3 - 0 = 3     | 3 - 3 = 0      |
| P1      | 2  | 6  | 9  | 9 - 2 = 7     | 7 - 6 = 1      |
| P2      | 5  | 2  | 11 | 11 - 5 = 6    | 6 - 2 = 4      |
| P3      | 1  | 8  | 19 | 19 - 1 = 18   | 18 - 8 = 10    |

**Average Turnaround Time** = (3 + 7 + 6 + 18) / 4 = 8.5  
**Average Waiting Time** = (0 + 1 + 4 + 10) / 4 = 3.75

---



### ✅ O(n log n) approach (priority_queue)
```c++

#include <bits/stdc++.h>
using namespace std;

int main() {
    

    int n = 4;
    vector<int>  ct(n), tat(n), wt(n);
    vector<int> at{0, 2, 4, 5};
    vector<int> bt{7, 4, 1, 4};

    vector<pair<int,int>> process; // {AT, index}
    for (int i = 0; i < n; i++) process.push_back({at[i], i});
    sort(process.begin(), process.end());

    priority_queue<pair<int,int>, vector<pair<int,int>>, greater<>> pq; // {BT, index}

    int time = 0, i = 0;
    while (!pq.empty() || i < n) {
        while (i < n && process[i].first <= time) {
            int idx = process[i].second;
            pq.push({bt[idx], idx});
            i++;
        }

        if (pq.empty()) {
            time = process[i].first; // CPU idle
            continue;
        }

        int b=pq.top().first;
        int idx=pq.top().second;
        // auto [b, idx] = pq.top(); 
        pq.pop();
        time += b;
        ct[idx] = time;
    }

    for (int i = 0; i < n; i++) {
        tat[i] = ct[i] - at[i];
        wt[i] = tat[i] - bt[i];
    }

    cout << "\nProcess\tAT\tBT\tCT\tTAT\tWT\n";
    for (int i = 0; i < n; i++) {
        cout << "P" << i+1 << "\t\t" 
             << at[i] << "\t" 
             << bt[i] << "\t" 
             << ct[i] << "\t" 
             << tat[i] << "\t" 
             << wt[i] << "\n";
    }
}
```
