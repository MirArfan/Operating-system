# ⏱️ FCFS – First Come First Serve CPU Scheduling

## Definition

First Come, First Serve (FCFS) is a **non-preemptive CPU scheduling algorithm**. Processes are executed in the order they **arrive in the ready queue**, like customers lining up at a grocery store.

  
**FCFS** হলো একটি **Non-Preemptive CPU Scheduling Algorithm**, যেখানে প্রসেসগুলো ready queue-এ আসার ক্রম অনুযায়ী CPU পায়, যেমন গ্রোসারি শপে লাইনে দাঁড়িয়ে ক্রেতারা।  

**Non-preemptive মানে:**  
একবার কোনো প্রসেস CPU পেলে, তা শেষ না হওয়া পর্যন্ত থামানো যাবে না, সাধারণত প্রসেস শেষ বা I/O করলে।  



### How FCFS Works ?

1. **Arrival:** প্রসেসগুলো সিস্টেমে আসে এবং ready queue-তে তাদের arrival order অনুযায়ী রাখা হয়।  
2. **Execution:** CPU queue-র প্রথম প্রসেসটি নেয় এবং সম্পূর্ণ execution করে।  
3. **Repeat:** CPU পরবর্তী প্রসেস নেবে এবং একইভাবে চালাবে।  
4. **Finish:** Queue শেষ না হওয়া পর্যন্ত চলতে থাকে।  

---

## Scenario 1: Processes with Same Arrival Time

| Process | Arrival Time (AT) | Burst Time (BT) |
|---------|-----------------|----------------|
| P1      | 0               | 5              |
| P2      | 0               | 3              |
| P3      | 0               | 8              |



### Step-by-Step Execution

| Step | Ready Queue Before CPU | CPU Execution | Ready Queue After CPU |
|------|-----------------------|---------------|---------------------|
| 1    | P1, P2, P3            | P1 (0 → 5)    | P2, P3              |
| 2    | P2, P3                | P2 (5 → 8)    | P3                  |
| 3    | P3                    | P3 (8 → 16)   | -                   |




### Gantt Chart
```
 | P1 | P2 | P3 |
 0    5    8    16
```
### FCFS CPU Scheduling – Complete Table

| Process | Arrival Time (AT) | Burst Time (BT) | Completion Time (CT) | Turnaround Time (TAT = CT - AT) | Waiting Time (WT = TAT - BT) |
|---------|-----------------|----------------|--------------------|-------------------------------|-----------------------------|
| P1      | 0               | 5              | 5                  | 5                             | 0                           |
| P2      | 0               | 3              | 8                  | 8                             | 5                           |
| P3      | 0               | 8              | 16                 | 16                            | 8                           |

**Average Turnaround Time (TAT):**  
\((5 + 8 + 16)/3 = 9.67\)  

**Average Waiting Time (WT):**  
\((0 + 5 + 8)/3 = 4.33\)



---
### Scenario 2: Processes with Different Arrival Times

| Process | Arrival Time (AT) | Burst Time (BT) |
|---------|-----------------|----------------|
| P1      | 2               | 5              |
| P2      | 0               | 3              |
| P3      | 4               | 4              |

### Step-by-Step Execution

| Step | Ready Queue Before CPU | CPU Execution | Ready Queue After CPU |
|------|-----------------------|---------------|---------------------|
| 1    | P2                    | P2 (0 → 3)    | P1                  |
| 2    | P1                    | P1 (3 → 8)    | P3                  |
| 3    | P3                    | P3 (8 → 12)   | -                   |

### Gantt Chart
```
| P2 | P1 | P3 |
0    3    8    12
```


### FCFS CPU Scheduling – Complete Table

| Process | Arrival Time (AT) | Burst Time (BT) | Completion Time (CT) | Turnaround Time (TAT = CT - AT) | Waiting Time (WT = TAT - BT) |
|---------|-----------------|----------------|--------------------|-------------------------------|-----------------------------|
| P2      | 0               | 3              | 3                  | 3                             | 0                           |
| P1      | 2               | 5              | 8                  | 6                             | 1                           |
| P3      | 4               | 4              | 12                 | 8                             | 4                           |

**Average Turnaround Time (TAT):**  
\((3 + 6 + 8)/3 = 5.67\)  

**Average Waiting Time (WT):**  
\((0 + 1 + 4)/3 = 1.67\)

---

### FCFS CPU Scheduling – Example with Different Arrival Times

### Processes Table

| Process | Arrival Time (AT) | Burst Time (BT) |
|---------|-----------------|----------------|
| P1      | 0               | 5              |
| P2      | 1               | 3              |
| P3      | 2               | 8              |
| P4      | 3               | 6              |

---

### Step-by-Step Execution (Ready Queue & CPU)

| Step | Ready Queue Before CPU | CPU Execution      | Ready Queue After CPU |
|------|-----------------------|-----------------|---------------------|
| 1    | P1       | P1 (0 → 5)       | P2, P3, P4          |
| 2    | P2, P3, P4            | P2 (5 → 8)       | P3, P4               |
| 3    | P3, P4                 | P3 (8 → 16)      | P4                   |
| 4    | P4                     | P4 (16 → 22)     | -                     |



### Gantt Chart
```
| P1 | P2 | P3 | P4 |
0    5    8    16   22
```


### FCFS – Complete Table (CT, TAT, WT)

| Process | AT  | BT  | CT  | TAT = CT - AT | WT = TAT - BT |
|---------|-----|-----|-----|---------------|---------------|
| P1      | 0   | 5   | 5   | 5 - 0 = 5     | 5 - 5 = 0     |
| P2      | 1   | 3   | 8   | 8 - 1 = 7     | 7 - 3 = 4     |
| P3      | 2   | 8   | 16  | 16 - 2 = 14   | 14 - 8 = 6    |
| P4      | 3   | 6   | 22  | 22 - 3 = 19   | 19 - 6 = 13   |



**Average Turnaround Time (TAT):**  
\((5 + 7 + 14 + 19)/4 = 11.25\)  

**Average Waiting Time (WT):**  
\((0 + 4 + 6 + 13)/4 = 5.75\)

---


### Advantages & Disadvantages of FCFS CPU Scheduling

### Advantages of FCFS

- **Simple and Basic Algorithm:**  
  The simplest form of CPU scheduling, easy to understand and implement.

- **Fair Execution:**  
  Every process gets a chance to execute in the order of its arrival, ensuring no process is arbitrarily prioritized.

- **Easy Implementation:**  
  Does not require complex data structures or calculations.

- **No Starvation:**  
  Since processes are executed in the order they arrive, there’s no risk of starvation.

- **Good for Batch Systems:**  
  Well suited for batch systems where longer processing times are acceptable.

#### সুবিধা (Bangla)

- সহজ এবং বেসিক Scheduling Algorithm।  
- Arrival order অনুসারে প্রতিটি প্রসেস CPU পায় → কোনো process starve হয় না।  
- Implementation সহজ, complex data structures লাগে না।  
- Batch systems-এ ভালো কাজ করে।  

---

### Disadvantages of FCFS

- **Convoy Effect:**  
  As a non-preemptive algorithm, long processes can block shorter ones, leading to inefficient execution.

- **High Average Waiting Time:**  
  Average waiting time is often much higher compared to other scheduling algorithms.

- **Poor Performance in Mixed Workloads:**  
  Short jobs may have to wait a long time if they arrive after longer tasks.

- **Not Suitable for Time-Sharing Systems:**  
  Since it processes tasks in arrival order, it does not ensure equal CPU time for all processes.

- **Late Processes Wait Longer:**  
  Processes at the end of the queue experience longer waiting times.

#### অসুবিধা (Bangla)

- **Convoy Effect**: যদি দীর্ঘ প্রসেস আগে আসে, ছোট প্রসেসগুলোকে অনেক সময় অপেক্ষা করতে হয় → inefficient execution।  
- Average waiting time অনেক বেশি হতে পারে।  
- Time-sharing systems-এর জন্য উপযুক্ত নয়।  
- Short jobs অপেক্ষা করতে থাকে → mixed workloads-এ poor performance।  
- Queue-এর শেষে থাকা processes অনেকক্ষণ অপেক্ষা করতে হয়।



### 🧩 Program 1: FCFS | Same Arrival Time

🧠 এখানে সব process একই সময়ে আসে (AT = 0)।
যেহেতু সবাই একসাথে এসেছে, CPU তাদের Burst Time (BT)-এর ক্রমে একটার পর একটা execute করে।

✅ Code:
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cout << "Enter number of processes: ";
    cin >> n;

    vector<int> bt(n), ct(n), tat(n), wt(n);
    cout << "Enter Burst Time for each process:\n";
    for (int i = 0; i < n; i++) {
        cout << "P" << i + 1 << ": ";
        cin >> bt[i];
    }

    // First process completion time = its burst time
    ct[0] = bt[0];

    // Next processes completion = previous completion + burst time
    for (int i = 1; i < n; i++) {
        ct[i] = ct[i - 1] + bt[i];
    }

    // Since all AT = 0, TAT = CT - AT = CT, and WT = TAT - BT
    for (int i = 0; i < n; i++) {
        tat[i] = ct[i];
        wt[i] = tat[i] - bt[i];
    }

    cout << "\nProcess\tBT\tCT\tTAT\tWT\n";
    for (int i = 0; i < n; i++) {
        cout << "P" << i + 1 << "\t" 
             << bt[i] << "\t" 
             << ct[i] << "\t" 
             << tat[i] << "\t" 
             << wt[i] << "\n";
    }

    return 0;
}
```

🧮 Example:

Input:
```
3
BT = [5, 9, 6]
```

Output:
```
Process	BT	CT	TAT	WT
P1	    5	5	5	0
P2	    9	14	14	5
P3	    6	20	20	14
```
📘 Formula:
Term	Formula
CT	CT[i] = CT[i-1] + BT[i]
TAT	TAT[i] = CT[i] - AT[i] → CT[i] (since AT=0)
WT	WT[i] = TAT[i] - BT[i]

---

### 🧩 Program 2: FCFS | Different Arrival Times

🧠 এখানে process গুলোর arrival time আলাদা।
CPU process গুলোকে তাদের arrival time অনুযায়ী serve করে।

✅ Code:
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cout << "Enter number of processes: ";
    cin >> n;

    vector<int> at(n), bt(n), ct(n), tat(n), wt(n);

    cout << "Enter Arrival Time and Burst Time for each process:\n";
    for (int i = 0; i < n; i++) {
        cout << "P" << i + 1 << " (AT BT): ";
        cin >> at[i] >> bt[i];
    }

    // Sort processes by arrival time (FCFS order)
    vector<pair<int, int>> process;
    for (int i = 0; i < n; i++) process.push_back({at[i], i});
    sort(process.begin(), process.end());

    // Compute completion times
    ct[process[0].second] = at[process[0].second] + bt[process[0].second];

    for (int i = 1; i < n; i++) {
        int idx = process[i].second;
        int prev_idx = process[i - 1].second;

        // If next process arrives after CPU is idle
        if (at[idx] > ct[prev_idx])
            ct[idx] = at[idx] + bt[idx];
        else
            ct[idx] = ct[prev_idx] + bt[idx];
    }

    // Compute TAT and WT
    for (int i = 0; i < n; i++) {
        tat[i] = ct[i] - at[i];
        wt[i] = tat[i] - bt[i];
    }

    cout << "\nProcess\tAT\tBT\tCT\tTAT\tWT\n";
    for (int i = 0; i < n; i++) {
        cout << "P" << i + 1 << "\t"
             << at[i] << "\t"
             << bt[i] << "\t"
             << ct[i] << "\t"
             << tat[i] << "\t"
             << wt[i] << "\n";
    }

    return 0;
}
```

🧮 Example:

Input:
```
4
AT = [0, 1, 2, 3]
BT = [5, 3, 8, 6]
```

Output:
```
Process	AT	BT	CT	TAT	WT
P1	    0	5	5	5	0
P2	    1	3	8	7	4
P3	    2	8	16	14	6
P4	    3	6	22	19	13
```