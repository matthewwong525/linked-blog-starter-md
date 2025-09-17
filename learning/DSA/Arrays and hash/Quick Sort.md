- Divide and conquer algo
### Steps:
1. **Partition**: Choose a "pivot" element and rearrange the array so all smaller elements are on the left, all larger elements are on the right
2. **Conquer**: Recursively sort the left and right subarrays
3. **Combine**: No explicit combination needed - the array is sorted in-place

#### Time complexity
1. Avg: O(n log n)
2. Worst case: O(n^2)

#### Space Complexity
- **Best/Average Case**: O(log n) - due to recursion stack depth
- **Worst Case**: O(n) - when recursion depth equals array size

#### Key Advantages
1. **In-place sorting**: Only O(log n) extra space needed
2. **Cache-friendly**: Good locality of reference
3. **Practical performance**: Often faster than other O(n log n) algorithms
4. **Divide-and-conquer**: Naturally parallelizable

#### Key Disadvantages
1. **Unstable**: Doesn't preserve relative order of equal elements
2. **Worst-case O(n²)**: Poor performance on already sorted data
3. **Recursion overhead**: Deep recursion for worst-case inputs

