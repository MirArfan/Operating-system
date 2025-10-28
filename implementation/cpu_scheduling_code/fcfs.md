```c++
#include <bits/stdc++.h>
using namespace std;


struct cmp {
    bool operator()(pair<int,int>& a, pair<int,int>& b) {
        if (a.first == b.first)
            return a.second > b.second; 
        return a.first > b.first; 
    }
};

int main() 
{
    int n = 4;
    vector<int> at{0, 1, 2, 3};
    vector<int> bt{5, 3, 8, 6};

    priority_queue<pair<int,int>, vector<pair<int,int>>, cmp> pq;

    for (int i = 0; i < n; i++) 
        pq.push({at[i], i});
   
    vector<int> ct(n), tat(n), wt(n);
    
    int prev = 0;
    while(!pq.empty())
    {
        int x = pq.top().first;
        int i = pq.top().second;
        pq.pop();

        prev += bt[i];
        ct[i] = prev;
        //cout << "(" << x << "," << i << ") "<<endl;
    }

    for(int i = 0; i < n; i++) {
        tat[i] = ct[i] - at[i];
        wt[i] = tat[i] - bt[i];
    }

    cout << "PID\tAT\tBT\tCT\tTAT\tWT\n";
    for (int i = 0; i < n; i++) {
        cout << "P" << i+1 << "\t" << at[i] << "\t" << bt[i] << "\t"
             << ct[i] << "\t" << tat[i] << "\t" << wt[i] << "\n";
    }

    return 0;
}
```

 output
 ```
 PID	AT	BT	CT	TAT	WT
 P1	0	5	5	5	0
 P2	1	3	8	7	4
 P3	2	8	16	14	6
 P4	3	6	22	19	13
```