### 1️⃣ O(n^2) approach
```c++
#include <bits/stdc++.h>
using namespace std;


int main() 
{
    int n = 4;
    vector<int>  ct(n), tat(n), wt(n);
    vector<int> at{0, 2, 4, 5};
    vector<int> bt{7, 4, 1, 4};


    vector<bool> done(n, false);
    int completed = 0, currentTime = 0;

    while (completed < n) {
        int idx = -1;
        int minBT = INT_MAX;

        for (int i = 0; i < n; i++) {
            if (!done[i] && at[i] <= currentTime && bt[i] < minBT) {
                minBT = bt[i];
                idx = i;
            }
        }
        

        if (idx == -1) {
            currentTime++;  // CPU idle
            continue;
        }

        currentTime += bt[idx];
        ct[idx] = currentTime;
        tat[idx] = ct[idx] - at[idx];
        wt[idx] = tat[idx] - bt[idx];
        done[idx] = true;
        completed++;
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
Output
```
Process	AT	BT	CT	TAT	WT
P1		0	7	7	7	0
P2		2	4	12	10	6
P3		4	1	8	4	3
P4		5	4	16	11	7
```

### 2️⃣ O(n log n) approach (priority_queue)
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
