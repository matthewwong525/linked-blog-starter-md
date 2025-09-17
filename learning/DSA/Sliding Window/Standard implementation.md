Q. https://leetcode.com/problems/longest-repeating-character-replacement/

Solution: 

```c++
int l=0;
for(r=0; r<size; r++){
	m[arr[r]] ++;
	while(condition is false){
		m[arr[l]]--;
		l++;
	}
	res = max(res, r - l + 1);
}
```
