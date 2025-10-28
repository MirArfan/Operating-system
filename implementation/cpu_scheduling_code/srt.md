### 1️⃣ O(n log n) approach, Using min-heap
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