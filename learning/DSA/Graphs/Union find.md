
| Method           | Time Complexity                                                   | Space Complexity | Comments                                                                                                                           |
| ---------------- | ----------------------------------------------------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| Union/Find       | O(n)                                                              | O(n)             |                                                                                                                                    |
| Union by rank    | O(log n)                                                          | O(n)             | maintains 2 arrays -> rank and parent. rank keeps track of children of the root node and parent keeps track of parent of the node. |
| path compression | O(α(n)) for both find and union<br>α is inverse ackerman function | O(n)             | maintains 2 arrays -> rank and parent. rank keeps track of children of the root node and parent keeps track of parent of the node. |

*The inverse Ackermann function α(n) grows extremely slowly. For all practical purposes, α(n) ≤ 4 for any realistic value of n (even for n up to 10^600). This means that for all practical applications, the operations are **essentially constant time**.*


Union find with path compression:
```c++
// Find with path compression 
int find(int x) { 
	if (parent[x] != x) { // Path compression: set parent to the root directly 
		parent[x] = find(parent[x]); 
	} 
	return parent[x]; 
}
```

```c++
// Union by rank 
void unionSets(int x, int y) { 
	int rootX = find(x); 
	int rootY = find(y); 
	
	// If they're already in the same set 
	if (rootX == rootY) return;
	// Union by rank: attach the smaller rank tree under the higher rank tree 
	if (rank[rootX] < rank[rootY]) 
		parent[rootX] = rootY;
	else if (rank[rootX] > rank[rootY]) 
		parent[rootY] = rootX;
	else { 
	// If ranks are the same, make one as root and increment its rank 
		parent[rootY] = rootX; 
		rank[rootX]++; 
	}
```

