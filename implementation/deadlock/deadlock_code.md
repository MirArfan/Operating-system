```c++
#include <iostream>
#include <vector>
using namespace std;

bool isDeadlock(vector<vector<int>> &allocation, vector<vector<int>> &request, vector<int> &available) {
    int n = allocation.size(); // Number of processes
    int m = available.size();  // Number of resources

    vector<int> work = available;
    vector<bool> finish(n, false);
    
    bool done;
    do {
        done = false;
        for (int i = 0; i < n; i++) {
            if (!finish[i]) {
                bool canProceed = true;
                for (int j = 0; j < m; j++) {
                    if (request[i][j] > work[j]) {
                        canProceed = false;
                        break;
                    }
                }
                if (canProceed) {
                    for (int j = 0; j < m; j++) {
                        work[j] += allocation[i][j];
                    }
                    finish[i] = true;
                    done = true;
                }
            }
        }
    } while(done);

    // If any process is not finished, deadlock exists
    for (bool f : finish) {
        if (!f) return true;
    }
    return false;
}

int main() {
    // Example: 3 processes, 3 resource types
    vector<vector<int>> allocation = {
        {0, 1, 0},  // P0
        {2, 0, 0},  // P1
        {3, 0, 2}   // P2
    };

    vector<vector<int>> request = {
        {0, 0, 2},  // P0
        {2, 0, 0},  // P1
        {0, 0, 1}   // P2
    };

    vector<int> available = {1, 1, 0}; // Available resources

    if (isDeadlock(allocation, request, available))
        cout << "Deadlock detected!" << endl;
    else
        cout << "No deadlock." << endl;

    return 0;
}
```