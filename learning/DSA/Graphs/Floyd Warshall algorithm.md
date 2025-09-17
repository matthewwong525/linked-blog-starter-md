- It is a Dynamic programming approach.
- It is used to find minimum distance between each pair of nodes in a graph.

```c++
for(int k; k<size; k++){
	for(int i=0; i<size; i++){
		for(int j=0; j<size; j++){
			A[i][j] = min(A[i][j], A[i][k] + A[k][j]);
		}
	}
}
```


time complexity: O(n^3)