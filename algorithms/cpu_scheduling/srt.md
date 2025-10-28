## ⚙️ SRTF – Shortest Remaining Time First CPU Scheduling



### 🧠 Introduction 

SRTF (Shortest Remaining Time First) is a **preemptive CPU scheduling algorithm**.  
CPU always executes the process with the **shortest remaining burst time**.  
If a new process arrives with a shorter burst time than the currently running process, CPU **preempts** the current process.

### 🔹
SRTF (Shortest Remaining Time First) হলো **preemptive CPU scheduling algorithm**।  
CPU সবসময় সেই প্রসেসটি executes করে যার **remaining burst time সবচেয়ে কম**।  
যদি নতুন প্রসেস আসে এবং তার burst time কম হয় বর্তমান প্রসেসের বাকি সময়ের চেয়ে, তাহলে CPU current process থামিয়ে নতুন প্রসেস চালায়।



### ⚙️ How SRTF Works (কাজ করার নিয়ম)

1. CPU সবসময় **ready queue-তে থাকা process-গুলোর মধ্যে shortest remaining time**-ওয়ালা process নেবে।  
2. Arrival time অনুযায়ী নতুন process আসে কিনা চেক করবে।  
3. যদি নতুন processের burst time কম হয় → CPU **preempt করবে**।  
4. Process শেষ হলে, next shortest remaining time process execution শুরু করবে।




### 🧩 Example: Preemptive SJF / SRTF

| Process | Arrival Time (AT) | Burst Time (BT) |
|---------|------------------|----------------|
| P1      | 0                | 7              |
| P2      | 2                | 4              |
| P3      | 4                | 1              |
| P4      | 5                | 4              |



### 🧮 Step-by-Step Execution

**Timeline & Ready Queue**

| Time | Ready Queue                | Running Process |
|------|----------------------------|----------------|
| 0-2  | P1                         | P1             |
| 2-4  | P1(5), P2(4)               | P2             |
| 4-5  | P1(5), P2(2), P3(1)        | P3             |
| 5-7  | P1(5), P4(4)               | P2             |
| 7-11 | P1(5)                      | P4             |
| 11-16| -                          | P1             |

**Execution Order →** P1 → P2 → P3 → P2 → P4 → P1


### 🧭 Gantt Chart

```
| P1 | P2 | P3 | P2 | P4 | P1 |
0    2    4    5    7    11   16
```



### 📊 Calculations

| Process | AT | BT | CT | TAT = CT - AT | WT = TAT - BT |
|---------|----|----|----|---------------|----------------|
| P1      | 0  | 7  | 16 | 16 - 0 = 16   | 16 - 7 = 9     |
| P2      | 2  | 4  | 7  | 7 - 2 = 5     | 5 - 4 = 1      |
| P3      | 4  | 1  | 5  | 5 - 4 = 1     | 1 - 1 = 0      |
| P4      | 5  | 4  | 11 | 11 - 5 = 6    | 6 - 4 = 2      |


**Average Turnaround Time** = (16 + 5 + 1 + 6) / 4 = 7.0  
**Average Waiting Time** = (9 + 1 + 0 + 2) / 4 = 3.0

---


### 🧩 Example 2: Different Arrival Times

| Process | Burst Time (BT) | Arrival Time (AT) |
|---------|----------------|------------------|
| P1      | 6 ms           | 0 ms             |
| P2      | 3 ms           | 1 ms             |
| P3      | 7 ms           | 2 ms             |

### 🧮 Step-by-Step Execution (Timeline & Ready Queue)

| Time       | Running Process | Notes |
|------------|----------------|-------|
| 0 - 1      | P1             | P1 runs for 1 ms (remaining 5 ms) |
| 1 - 4      | P2             | P2 runs for 3 ms (remaining 0 ms) – shortest remaining |
| 4 - 9      | P1             | P1 runs for 5 ms (remaining 0 ms) |
| 9 - 16     | P3             | P3 runs for 7 ms (remaining 0 ms) |

**Execution Order →** P1 → P2 → P1 → P3



### 🧭 Gantt Chart
```
| P1 | P2 | P1 | P3 |
0    1    4    9    16
```


### 📊 Calculations

| Process | AT | BT | CT | TAT = CT - AT | WT = TAT - BT |
|---------|----|----|----|---------------|----------------|
| P1      | 0  | 6  | 9  | 9 - 0 = 9     | 9 - 6 = 3      |
| P2      | 1  | 3  | 4  | 4 - 1 = 3     | 3 - 3 = 0      |
| P3      | 2  | 7  | 16 | 16 - 2 = 14   | 14 - 7 = 7     |

**Average Turnaround Time** = (9 + 3 + 14)/3 = 26/3 ≈ 8.67 ms  
**Average Waiting Time** = (3 + 0 + 7)/3 = 10/3 ≈ 3.33 ms

---
### ✅ O(n log n) approach, Using min-heap
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
    

    int n = 4;
    vector<int>  ct(n, 0), tat(n), wt(n), rt(n);
    vector<int> at{0, 2, 4, 5};
    vector<int> bt{7, 4, 1, 4};
    rt=bt;

    vector<pair<int,int>> process; // {AT, index}
    for (int i = 0; i < n; i++) process.push_back({at[i], i});
    sort(process.begin(), process.end());

    priority_queue<pair<int,int>, vector<pair<int,int>>, greater<>> pq; // {BT, index}

    int time = 0, completed = 0, i = 0;
    while (completed < n) {
        while (i < n && process[i].first <= time) {
            int idx = process[i].second;
            pq.push({rt[idx], idx});
            i++;
        }
        cout<<" i : "<<i<<endl;
        if (pq.empty()) {
            time = process[i].first; // CPU idle
            continue;
        }

        int rem=pq.top().first;
        int idx=pq.top().second;
        cout<<"time : "<<time<<", rem : "<<rem<<", idx : "<<idx<<endl;
        pq.pop();
        rt[idx]--;
        time++;

      
        if (rt[idx] == 0) {
            completed++;
            ct[idx] = time;
        } else {
            pq.push({rt[idx], idx}); 
        }
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
Output:
```
Process	AT	BT	CT	TAT	WT
P1		0	7	16	16	9
P2		2	4	7	5	1
P3		4	1	5	1	0
P4		5	4	11	6	2
```