## ⚙️ Priority Scheduling (Preemptive)


### Definition (সংজ্ঞা)

#### 🔹 English:
In Preemptive Priority Scheduling, the CPU always executes the process with the highest priority (smaller number = higher priority).  
If a new process arrives with a higher priority than the currently running process, the CPU preempts the running process and executes the new one.

#### 🔹 
Preemptive Priority Scheduling-এ CPU সবসময় ready queue-তে থাকা highest priority process-কে চালায়।  
যদি নতুন কোনো process আসে যার priority চলমান process-এর থেকে বেশি হয়, CPU current process থামিয়ে নতুন process চালু করে।

### ⚙️ How it Works (কাজের ধাপ)
- Ready Queue-তে সব process আসে arrival order অনুযায়ী।  
- CPU সবসময় ready queue থেকে highest priority process নেয়।  
- Arrival সময় অনুযায়ী নতুন process এলেও, যদি তার priority বেশি হয়, তখন preemption হয়।  
- Process শেষ হলে, ready queue থেকে পরবর্তী highest priority process নেয়া হয়।  
- সব process শেষ না হওয়া পর্যন্ত repeat।

### ✅ Advantages of Preemptive Priority / সুবিধা
- High priority processes দ্রুত execute হয়।  
- Interactive systems-এ short & important tasks দ্রুত সম্পন্ন হয়।  
- Average waiting time অনেক কমে, তুলনা করলে Non-Preemptive এর চেয়ে।

### ❌ Disadvantages / অসুবিধা
- Low priority processes starvation-এ পড়তে পারে।  
- Frequent context switching → overhead বাড়ে।  
- Burst time & priority knowledge প্রয়োজন।


### 🧠 Problem-01

Consider the set of 5 processes whose arrival time, burst time, and priority are given below 👇  

| Process ID | Arrival Time (AT) | Burst Time (BT) | Priority |
|-------------|------------------|----------------|-----------|
| P1 | 0 | 4 | 2 |
| P2 | 1 | 3 | 3 |
| P3 | 2 | 1 | 4 |
| P4 | 3 | 5 | 5 |
| P5 | 4 | 2 | 5 |

> **Note:** Higher number represents **higher priority**.



### ⚙️ CPU Scheduling Policy  
**Type:** Priority (Preemptive)  

In **Preemptive Priority Scheduling**, whenever a new process arrives with a **higher priority**, it immediately **preempts** (interrupts) the currently running process and takes over the CPU.



### 🧩 Step-by-Step Explanation

1. **At time 0:**  
   - Only **P1** is available → starts execution.  
   - **Ready Queue:** [P1]  

2. **At time 1:**  
   - **P2** arrives (Priority 3 > P1’s 2) → **P2 preempts P1**.  
   - **Ready Queue:** [P2, P1]  

3. **At time 2:**  
   - **P3** arrives (Priority 4 > P2’s 3) → **P3 preempts P2**.  
   - **Ready Queue:** [P3, P2, P1]  

4. **At time 3:**  
   - **P3** finishes (1 unit).  
   - **P4** arrives (Priority 5 → highest).  
   - **P4** starts execution.  
   - **Ready Queue:** [P4, P2, P1]  

5. **At time 4:**  
   - **P5** arrives (Priority 5, same as P4) → follows **FCFS** → waits.  
   - **Ready Queue:** [P4, P5, P2, P1]  

6. **At time 8:**  
   - **P4** finishes.  
   - Next highest priority = **P5 (5)** → runs next.  
   - **Ready Queue:** [P5, P2, P1]  

7. **At time 10:**  
   - **P5** finishes.  
   - Next highest = **P2 (3)** → runs next.  
   - **Ready Queue:** [P2, P1]  

8. **At time 12:**  
   - **P2** finishes.  
   - Only **P1** remains → resumes and finishes at **t = 15**.  


### 🧭 Gantt Chart
```
| P1 | P2 | P3 | P4 | P5 | P2 | P1 |
0    1    2    3    8    10   12   15 
```

### 📊 Calculations

| Process ID | AT | BT | CT | TAT = CT - AT | WT = TAT - BT |
|-------------|----|----|----|----------------|----------------|
| P1 | 0 | 4 | 15 | 15 - 0 = 15 | 15 - 4 = 11 |
| P2 | 1 | 3 | 12 | 12 - 1 = 11 | 11 - 3 = 8 |
| P3 | 2 | 1 | 3  | 3 - 2 = 1  | 1 - 1 = 0 |
| P4 | 3 | 5 | 8  | 8 - 3 = 5  | 5 - 5 = 0 |
| P5 | 4 | 2 | 10 | 10 - 4 = 6 | 6 - 2 = 4 |



### 🧮 Averages

**Average Turnaround Time (TAT)** = (15 + 11 + 1 + 5 + 6) / 5 = **7.6 units**  
**Average Waiting Time (WT)** = (11 + 8 + 0 + 0 + 4) / 5 = **4.6 units**


### ✅ Summary

- **Preemptive Priority Scheduling** allows higher-priority processes to interrupt lower ones.  
- Helps reduce waiting time for high-priority processes.  
- However, **frequent preemption** may cause **context-switch overhead** and **starvation** of lower-priority processes.

---


### 🧮 Preemptive Priority Scheduling Example 2

### Given:
In preemptive priority scheduling, if a process arrives that has **higher priority** than the executing process, it **pre-empts** the lower priority process.

| Process | Arrival Time (AT) | CPU Burst Time (BT) | Priority |
|---------|------------------|-------------------|----------|
| P1      | 0                | 8                 | 3        |
| P2      | 4                | 10                | 2        |
| P3      | 4                | 3                 | 3        |
| P4      | 10               | 4                 | 1        |

>**Note:** Lower priority number = higher priority.

```
|  p1  |  p2   |    p4   |     p2   |     p1   |    p3   |
0      4       10        14         18         22        25
p1=8   p1=4    p1        p1         p1         p3
       p2=10   p2=4      p2         p3
       p3=3    p3        p3
               p4
```

### ⚙️ Step-by-Step Execution

1. **Time 0-4ms (P1 Executes)**  
   - Only `P1` is available → starts execution.  
   - **Remaining burst:** 8 - 4 = 4 ms.  

2. **Time 4ms:**  
   - `P2` and `P3` arrive.  
   - `P2` has higher priority than `P1` → **P2 preempts P1**.  
   - **Ready Queue:** [P1 (remaining=4), P3 (3)]  

3. **Time 4-10ms (P2 Executes)**  
   - `P2` executes.  
   - **Remaining burst:** 10 - 6 = 4 ms.  

4. **Time 10ms:**  
   - `P4` arrives with **highest priority (1)** → **preempts P2**.  

5. **Time 10-14ms (P4 Executes)**  
   - `P4` executes completely → **finished**.  
   - **Ready Queue:** [P1 (4), P2 (4), P3 (3)]  

6. **Time 14-18ms (P2 Resumes)**  
   - `P2` executes remaining 4 ms → **finished**.  
   - **Ready Queue:** [P1 (4), P3 (3)]  

7. **Time 18-22ms (P1 Resumes)**  
   - `P1` executes remaining 4 ms → **finished**.  
   - **Ready Queue:** [P3 (3)]  

8. **Time 22-25ms (P3 Executes)**  
   - `P3` executes → **finished**.  


### 🧭 Gantt Chart
```
| P1 | P2 | P4 | P2 | P1 | P3 |
0    4    10   14   18   22   25
```

**Execution Order:** P1 → P2 → P4 → P2 → P1 → P3


### 📊 Calculations

### Turnaround Time (TAT)
> TAT = Completion Time − Arrival Time

| Process |AT|BT | CT | TAT |  WT |
|---------|---|--|---------------------|-----|-----|
| P1     |0|     8     | 22                         | 22 - 0 = 22 ms | 22 - 8 = 14 ms 
| P2     |4|     10      | 18                         | 18 - 4 = 14 ms | 14 - 10 = 4 ms 
| P3     | 4|    3     | 25                         | 25 - 4 = 21 ms | 21 - 3 = 18 ms 
| P4    |  10|   4   | 14                      | 14 - 10 = 4 ms | 4 - 4 = 0 ms

**Average Turnaround Time (ATT)**  
= (22 + 14 + 21 + 4) / 4 = **15.25 ms**



**Average Waiting Time (AWT)**  
= (14 + 4 + 18 + 0) / 4 = **7 ms**


### ✅ Final Results

| Metric | Average Time |
|--------|---------------|
| **Average Turnaround Time (ATT)** | 15.25 ms |
| **Average Waiting Time (AWT)**    | 7 ms |

---

### 2 Preemptive Priority Scheduling (C++)

ধারণা: CPU সবসময় ready queue-এ থাকা highest priority প্রসেস চালায়; নতুন উচ্চতর priority আসলে current process preempt হয়।

এখানে per-time unit simulation করা হয়েছে (time advances by 1 unit per iteration) — ফলে সুস্পষ্টভাবে preemption দেখা যায়।

```c++
// preemptive_priority.cpp
// Preemptive Priority Scheduling (lower number => higher priority)
// Compile: g++ preemptive_priority.cpp -o p_priority
// Run: ./p_priority

#include <bits/stdc++.h>
using namespace std;

int main() {

    int n;
    cout << "Number of processes: ";
    cin >> n;

    vector<int> pid(n), at(n), bt(n), pr(n);
    for (int i = 0; i < n; ++i) pid[i] = i + 1;

    cout << "Enter Arrival Time, Burst Time and Priority (smaller number = higher priority) for each process:\n";
    for (int i = 0; i < n; ++i) {
        cout << "P" << pid[i] << " AT BT PR: ";
        cin >> at[i] >> bt[i] >> pr[i];
    }

    vector<int> rem = bt;
    vector<int> ct(n, 0), tat(n, 0), wt(n, 0);
    vector<bool> done(n, false);

    int completed = 0;
    int time = 0;
    int minAT = *min_element(at.begin(), at.end());
    time = minAT;

    while (completed < n) {
        int idx = -1;
        int bestPriority = INT_MAX;
        int earliestArrivalForTie = INT_MAX;

        // select among arrived (AT <= time) and not done the one with smallest priority
        for (int i = 0; i < n; ++i) {
            if (!done[i] && at[i] <= time) {
                // choose smallest priority; tie-breaker: earliest arrival then smaller PID
                if (pr[i] < bestPriority || (pr[i] == bestPriority && at[i] < earliestArrivalForTie)) {
                    bestPriority = pr[i];
                    earliestArrivalForTie = at[i];
                    idx = i;
                }
            }
        }

        if (idx == -1) {
            time++;
            continue;
        }

        // execute 1 unit time
        rem[idx]--;
        time++;

        if (rem[idx] == 0) {
            done[idx] = true;
            completed++;
            ct[idx] = time;
            tat[idx] = ct[idx] - at[idx];
            wt[idx] = tat[idx] - bt[idx];
        }
    }

    double avgTAT = 0, avgWT = 0;
    cout << "\nP\tAT\tBT\tPR\tCT\tTAT\tWT\n";
    for (int i = 0; i < n; ++i) {
        cout << "P" << pid[i] << "\t" << at[i] << "\t" << bt[i] << "\t" << pr[i]
             << "\t" << ct[i] << "\t" << tat[i] << "\t" << wt[i] << "\n";
        avgTAT += tat[i]; avgWT += wt[i];
    }
    avgTAT /= n; avgWT /= n;
    cout << "\nAverage Turnaround Time = " << avgTAT << "\n";
    cout << "Average Waiting Time = " << avgWT << "\n";

    return 0;
}
```

```c++
#include <bits/stdc++.h>
using namespace std;


int main() 
{
    int n = 4;
    vector<int> ct(n, 0), tat(n, 0), wt(n,0);
    vector<int> at{0, 4, 4, 10};
    vector<int> bt{8, 10, 3, 4};
    vector<int> pr{3, 2, 3, 1};

    vector<int> rem = bt;
    // vector<int> ct(n, 0), tat(n, 0), wt(n, 0);
    vector<bool> done(n, false);

    int completed = 0;
    int time = 0;
    int minAT = *min_element(at.begin(), at.end());
    time = minAT;

    while (completed < n) {
        int idx = -1;
        int bestPriority = INT_MAX;
        int earliestArrivalForTie = INT_MAX;

        // select among arrived (AT <= time) and not done the one with smallest priority
        for (int i = 0; i < n; ++i) {
            if (!done[i] && at[i] <= time) {
                // choose smallest priority; tie-breaker: earliest arrival then smaller PID
                if (pr[i] < bestPriority || (pr[i] == bestPriority && at[i] < earliestArrivalForTie)) {
                    bestPriority = pr[i];
                    earliestArrivalForTie = at[i];
                    idx = i;
                }
            }
        }

        if (idx == -1) {
            time++;
            continue;
        }

        // execute 1 unit time
        rem[idx]--;
        time++;

        if (rem[idx] == 0) {
            done[idx] = true;
            completed++;
            ct[idx] = time;
            tat[idx] = ct[idx] - at[idx];
            wt[idx] = tat[idx] - bt[idx];
        }
    }

     double totalTAT = 0, totalWT = 0;

    // Output
    cout << "\nProcess\tAT\tBT\tPR\tCT\tTAT\tWT\n";
    for (int i = 0; i < n; i++) {
        cout << "P" << i+1 << "\t\t" 
             << at[i] << "\t" 
             << bt[i] << "\t" 
             << pr[i] << "\t" 
             << ct[i] << "\t" 
             << tat[i] << "\t" 
             << wt[i] << "\n";

        totalTAT += tat[i];
        totalWT += wt[i];
    }

    cout << fixed << setprecision(2);
    cout << "\nAverage Turnaround Time: " << totalTAT / n;
    cout << "\nAverage Waiting Time: " << totalWT / n << "\n";

}
```