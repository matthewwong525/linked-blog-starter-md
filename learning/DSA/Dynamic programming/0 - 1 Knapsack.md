## Implementation
### Recursive code :
```c++
int ks(int [] val, int [] wt, int w, int n){
	if(n == 0 || w == 0){
		return 0;
	}

	if(wt[n-1] <= w){
		return max(
			val[n-1] + ks(val, wt, w-wt[n-1], n-1),
			ks(val, wt, w, n-1) 
		);
	}
	else{
		return ks(val, wt, w, n-1);
	}
}
```

### Memoization
```c++
int t[n+1][w+1];
memset(t, -1, t.size());
for(int i=0; i<n+1; i++){
	for(int j=0; j++){
		if(i==0 || j==0)
			t[i][j] = 0;
	}
}

int ks(int [] val, int [] wt, int w, int n){
	if(n == 0 || w == 0){
		return 0;
	}

	if(t[n][w] != -1){
		return t[n][w]
	}
	
	if(wt[n-1] <= w){
		t[n][w] = max(
			val[n-1] + ks(val, wt, w-wt[n-1], n-1),
			ks(val, wt, w, n-1) 
		);
	}
	else{
		t[n][w] = ks(val, wt, w, n-1);
	}
	return t[n][w];
}
```

### Tabulation
```cpp
for(int i=0; i<n+1; i++){
	for(int j=1; j<w+1; j++){
		if(wt[i-1] <= j){
			t[i][j] = max(
				val[i-1] + t[i-1][j-wt[i-1]],
				t[i-1][j]
			);
		}
		else{
			t[i][j] = t[i-1][j]; 
		}	
	}
}
```

## Similar problems
### Subset sum problem
Given an `array` and a `target`, return true if there is a subset in the array whose sum equals to the `target`.
```c++
// target is w, array is wt array
// t is a table of n+1 by w+1 size of type boolean
for(int i=1; i<n+1; i++){
	for(int j=1; j<target + 1; j++){
		if(wt[i-1] <= j){
			t[i][j] = t[i-1][j] || t[i-1][j - array[i-1]]
		}else{
			t[i][j] = t[i-1][j]
		}
	}
}
```
### Equal sum partition problem
```c++

```
### Count of subsets of given sum
### Maximize subset sum difference
### Count of number of subsets of given difference
### Target sum problem