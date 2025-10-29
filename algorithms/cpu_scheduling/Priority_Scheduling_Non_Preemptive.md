## ⚙️ Priority Scheduling (Non-Preemptive)


### 🧠 Definition 

In **Non-Preemptive Priority Scheduling**, each process is assigned a **priority number**.  
The **CPU** is allocated to the process with the **highest priority** (usually a smaller number means higher priority).  
Once the CPU starts executing a process, it **cannot be interrupted** until that process finishes.

### 🔹 
**Non-Preemptive Priority Scheduling**-এ প্রতিটি প্রসেসের সাথে একটি **priority number** থাকে।  
CPU সেই প্রসেসকেই আগে execute করে যার **priority সবচেয়ে বেশি** (সাধারণত সংখ্যা যত ছোট, প্রাধান্য তত বেশি)।  
একবার কোনো প্রসেস CPU পেলে, সেটা **শেষ না হওয়া পর্যন্ত বন্ধ হয় না**।


### 🧩 How it Works (কাজ করার ধাপ)

1. সব প্রসেস Ready Queue-তে আসে।  
2. Scheduler দেখে কোন process-এর **priority সবচেয়ে বেশি**।  
3. CPU সেই process-কে execute করে।  
4. Process শেষ হলে CPU **পরের highest priority** process নেয়।  
5. যদি একাধিক process-এর priority একই হয়, তাহলে **FCFS (First Come, First Serve)** ব্যবহার করা হয়।


### ⚡ Advantages and Disadvantages of Priority Scheduling

#### ✅ Advantages / সুবিধা
- Simple and effective when process priority is well-defined.  
  প্রসেসের priority ভালোভাবে নির্ধারিত থাকলে সহজ এবং কার্যকর।  
- Suitable for batch systems where certain tasks must be executed first.  
  ব্যাচ সিস্টেমের জন্য উপযুক্ত যেখানে কিছু নির্দিষ্ট কাজ প্রথমে সম্পন্ন করতে হবে।  

#### ❌ Disadvantages / অসুবিধা
- Low-priority processes may suffer **starvation** (never get CPU).  
  কম প্রাধান্যের প্রসেসগুলো **starvation**-এর শিকার হতে পারে (CPU পায় না)।  
- Doesn’t consider process length — short processes with low priority may wait long.  
  প্রসেসের দৈর্ঘ্য বিবেচনা করে না — ছোট কম priority প্রসেসগুলো অনেকক্ষণ অপেক্ষা করতে পারে।  
- Not suitable for **time-sharing systems**.  
  **Time-sharing systems**-এর জন্য উপযুক্ত নয়।



---

### 📋 Example
> **Note:** Lower number represents higher priority.


| Process | Arrival Time (AT) | Burst Time (BT) | Priority |
|----------|------------------|----------------|-----------|
| P1 | 0 | 4 | 2 |
| P2 | 1 | 2 | 1 |
| P3 | 2 | 6 | 3 |


### 🧮 Step-by-Step Execution

1. **Time 0-4 (P1 Executes)**  
   - Only **P1** has arrived at time 0.  
   - P1 starts and runs for 4 ms (non-preemptive → can’t be interrupted).  
   - **At time 4**, P1 finishes execution.  
   - **Ready Queue:** [P2, P3]  

2. **Time 4-6 (P2 Executes)**  
   - At time 4, both P2 and P3 are in the ready queue.  
   - P2 has **highest priority (1)** → selected next.  
   - Runs for 2 ms and finishes at time 6.  
   - **Ready Queue:** [P3]  

3. **Time 6-12 (P3 Executes)**  
   - Only P3 remains.  
   - Runs for 6 ms and finishes at time 12.  
   - **Ready Queue:** []  



### 🧭 Gantt Chart
```
| P1 | P2 | P3 |
0    4    6    12 
```


### 📊 Calculations

| Process | AT | BT | CT | TAT = CT - AT | WT = TAT - BT |
|----------|----|----|----|----------------|----------------|
| P1 | 0 | 4 | 4 | 4 - 0 = 4 | 4 - 4 = 0 |
| P2 | 1 | 2 | 6 | 6 - 1 = 5 | 5 - 2 = 3 |
| P3 | 2 | 6 | 12 | 12 - 2 = 10 | 10 - 6 = 4 |


### 🧮 Averages

**Average Turnaround Time (TAT)** = (4 + 5 + 10) / 3 = **6.33**  
**Average Waiting Time (WT)** = (0 + 3 + 4) / 3 = **2.33**

-----


### 🧩 Problem 02: Priority Scheduling (Non-Preemptive)



### 🧠 Given Data

| Process ID | Arrival Time (AT) | Burst Time (BT) | Priority |
|-------------|------------------|----------------|-----------|
| P1 | 0 | 4 | 2 |
| P2 | 1 | 3 | 3 |
| P3 | 2 | 1 | 4 |
| P4 | 3 | 5 | 5 |
| P5 | 4 | 2 | 5 |

> **Note:** Higher number represents **higher priority**.


### ⚙️ Scheduling Type

**Algorithm:** Priority Scheduling (Non-Preemptive)  
**Rule:**  
- CPU allocates to the **highest priority** process (largest priority number).  
- Once a process starts, it **cannot be interrupted** until completion.



### 🧮 Step-by-Step Execution

1. **At time 0:**  
   - Only **P1** has arrived → it starts execution.  
   - Runs from 0 → 4.  
   - **Completed:** P1  
   - **Ready Queue:** [P2, P3, P4, P5]  

2. **At time 4:**  
   - Available: P2 (3), P3 (4), P4 (5), P5 (5)  
   - Highest priority = 5 → **P4 and P5** both have same priority.  
   - **FCFS** rule → P4 arrived earlier → executes next.  
   - Runs from 4 → 9.  
   - **Completed:** P4  
   - **Ready Queue:** [P2, P3, P5]  

3. **At time 9:**  
   - Available: P2 (3), P3 (4), P5 (5)  
   - Highest priority = 5 → **P5 executes next.**  
   - Runs from 9 → 11.  
   - **Completed:** P5  
   - **Ready Queue:** [P2, P3]  

4. **At time 11:**  
   - Available: P2 (3), P3 (4)  
   - Highest priority = 4 → **P3 executes next.**  
   - Runs from 11 → 12.  
   - **Completed:** P3  
   - **Ready Queue:** [P2]  

5. **At time 12:**  
   - Only **P2** remains.  
   - Runs from 12 → 15.  
   - **Completed:** P2  


### 🧭 Gantt Chart
```
| P1 | P4 | P5 | P3 | P2 |
0    4    9    11   12   15 
```

### 📊 Calculations

| Process ID | AT | BT | CT (Exit Time) | TAT = CT - AT | WT = TAT - BT |
|-------------|----|----|----------------|----------------|----------------|
| P1 | 0 | 4 | 4 | 4 - 0 = 4 | 4 - 4 = 0 |
| P2 | 1 | 3 | 15 | 15 - 1 = 14 | 14 - 3 = 11 |
| P3 | 2 | 1 | 12 | 12 - 2 = 10 | 10 - 1 = 9 |
| P4 | 3 | 5 | 9 | 9 - 3 = 6 | 6 - 5 = 1 |
| P5 | 4 | 2 | 11 | 11 - 4 = 7 | 7 - 2 = 5 |



### 🧮 Averages

**Average Turnaround Time (TAT)** = (4 + 14 + 10 + 6 + 7) / 5 = **8.2 units**  
**Average Waiting Time (WT)** = (0 + 11 + 9 + 1 + 5) / 5 = **5.2 units**

---


### 🧮 Priority Scheduling (Non-Preemptive) - Example

### Given:
In this example, we consider a situation when the processes arrive at different times.

| Process | Arrival Time | CPU Burst Time | Priority |
|----------|---------------|----------------|-----------|
| P1 | 0 | 6 | 2 |
| P2 | 4 | 10 | 1 |
| P3 | 4 | 4 | 2 |
| P4 | 8 | 3 | 1 |

**Note:** Lower priority number represents **higher priority**.



### ⚙️ Step-by-Step Execution

- **At time 0ms:**  
  Only `P1` has arrived → `P1` starts execution.  
  `P1` completes at **6ms**.

- **At time 6ms:**  
  `P2` and `P3` have arrived.  
  `P2` has **higher priority (1)** → executes next.  
  `P2` runs till **16ms**.

- **At time 16ms:**  
  `P4` has arrived (priority 1) → executes next.  
  `P4` runs from **16ms to 19ms**.

- **At time 19ms:**  
  Only `P3` is left → executes last.  
  `P3` runs from **19ms to 23ms**.


### 🧠 Gantt Chart
```
| P1 | P2 | P4 | P3 |
0    6    16   19   23
```

**Order of Execution:** `P1 → P2 → P4 → P3`



### 📊 Calculation

### Turnaround Time (TAT)
> TAT = Completion Time − Arrival Time

| Process | Completion Time | Arrival Time | Turnaround Time (TAT) |
|----------|-----------------|---------------|------------------------|
| P1 | 6 | 0 | 6 − 0 = **6 ms** |
| P2 | 16 | 4 | 16 − 4 = **12 ms** |
| P3 | 23 | 4 | 23 − 4 = **19 ms** |
| P4 | 19 | 8 | 19 − 8 = **11 ms** |

**Average Turnaround Time (ATT)**  
= (6 + 12 + 19 + 11) / 4  
= **12 ms**


### Waiting Time (WT)
> WT = Turnaround Time − Burst Time

| Process | Turnaround Time (TAT) | Burst Time | Waiting Time (WT) |
|----------|------------------------|-------------|--------------------|
| P1 | 6 | 6 | 0 |
| P2 | 12 | 10 | 2 |
| P3 | 19 | 4 | 15 |
| P4 | 11 | 3 | 8 |

**Average Waiting Time (AWT)**  
= (0 + 2 + 15 + 8) / 4  
= **6.25 ms**


### ✅ Final Results

| Metric | Average Time |
|--------|---------------|
| **Average Turnaround Time (ATT)** | **12 ms** |
| **Average Waiting Time (AWT)** | **6.25 ms** |

---

### 1 : Non-Preemptive Priority Scheduling (C++)

ধারণা: প্রতিবার CPU ঐসব প্রসেস থেকে নেয় যেগুলো ইতিমধ্যেই এসেছে (AT ≤ current time) এবং যার priority সর্বোচ্চ (আমরা ধরেছি priority সংখ্যা যত ছোট, প্রাধান্য তত বেশি)।

একবার CPU পেলে প্রসেসটি শেষ না হওয়া পর্যন্ত চলবে (non-preemptive)।
```c++
// Non-Preemptive Priority Scheduling (lower number => higher priority)

#include <bits/stdc++.h>
using namespace std;


int main() 
{
    int n = 4;
    vector<int>  ct(n, 0), tat(n, 0), wt(n,0);
    vector<int> at{0, 4, 4, 8};
    vector<int> bt{6, 10, 4, 3};
    vector<int> pr{2, 1, 2, 1};

    vector<int> done(n, 0);
    int completed = 0, curr_time = 0;
    vector<int> gantt;

    while (completed < n) {
        int idx = -1;
        int highest_priority = INT_MAX;

        for (int i = 0; i < n; i++) {
            if (at[i] <= curr_time && done[i] == 0) {
                if (pr[i] < highest_priority) {
                    highest_priority = pr[i];
                    idx = i;
                }
                else if (pr[i] == highest_priority) {
                    if (at[i] < at[idx]) idx = i;
                }
            }
        }

        if (idx != -1) {
            curr_time += bt[idx];
            ct[idx] = curr_time;
            done[idx] = 1;
            gantt.push_back(pr[idx]);
            completed++;
        } 
        else {
            curr_time++;
        }
    }

    for(int idx=0; idx<n; idx++)
    {
        tat[idx] = ct[idx] - at[idx];
        wt[idx] = tat[idx] - bt[idx];
    }
    double totalTAT = 0, totalWT = 0;


    cout << "\nGantt Chart: ";
    for (int id : gantt) cout << " P" << id << " |";
    cout << endl;


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

### 📝 Note: When Higher Priority = Larger Number  

By default, in **Priority Scheduling**, a **smaller priority number** means **higher priority**.  
If you want to reverse it — so that a **larger priority number** means **higher priority**,  
you only need to change **two lines** in the code.  


### ⚙️ Code Modification

|Before | After |
|--------------------|------------------|
| `int highest_priority = INT_MAX;` | `int highest_priority = INT_MIN;` |
| `if (pr[i] < highest_priority)` | `if (pr[i] > highest_priority)` |
