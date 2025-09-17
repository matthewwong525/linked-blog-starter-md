ref. https://github.com/mission-peace/interview/blob/master/src/com/interview/tree/FenwickTree.java


```cpp
#include <bits/stdc++.h>
using namespace std;

class FenwickTree {
private:
    vector<int> tree;  // The Fenwick Tree array (1-based indexing)
    int n;             // Size of the underlying array

public:
    // Constructor: Initialize the tree with size 'size'
    FenwickTree(int size) {
        n = size;
        tree.assign(n + 1, 0);  // Initialize all elements to 0
    }

    // Update: Add 'val' to the element at index 'idx' (1-based)
    void update(int idx, int val) {
        while (idx <= n) {
            tree[idx] += val;   // Add value to current node
            idx += idx & -idx;  // Move to next responsible node
        }
    }

    // Query: Get the prefix sum from index 1 to 'idx' (1-based)
    int query(int idx) {
        int sum = 0;
        while (idx > 0) {
            sum += tree[idx];   // Add value from current node
            idx -= idx & -idx;  // Move to previous responsible node
        }
        return sum;
    }

    // Optional: Range sum query from 'left' to 'right' (inclusive)
    int rangeQuery(int left, int right) {
        return query(right) - query(left - 1);
    }
};

// Example usage
int main() {
    int size = 10;
    FenwickTree ft(size);

    // Update some values (like building from an array [3, 2, -1, 6, 5, 4, -3, 3, 7, 2])
    ft.update(1, 3);
    ft.update(2, 2);
    ft.update(3, -1);
    ft.update(4, 6);
    ft.update(5, 5);
    ft.update(6, 4);
    ft.update(7, -3);
    ft.update(8, 3);
    ft.update(9, 7);
    ft.update(10, 2);

    // Query prefix sum up to index 5 (should be 3+2-1+6+5 = 15)
    cout << "Prefix sum up to 5: " << ft.query(5) << endl;

    // Range sum from 2 to 6 (2 + -1 + 6 + 5 + 4 = 16)
    cout << "Range sum from 2 to 6: " << ft.rangeQuery(2, 6) << endl;

    // Update index 3 by adding 1 (changes -1 to 0)
    ft.update(3, 1);

    // New prefix sum up to 5 (3+2+0+6+5 = 16)
    cout << "Updated prefix sum up to 5: " << ft.query(5) << endl;

    return 0;
}

```


