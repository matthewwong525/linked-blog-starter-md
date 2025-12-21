Note that [[Data Structures Unit 1]] was made purely from my own notes, whereas this Unit 2 has been made with assistance from claude.ai to summarise chapters.

### Growth functions
A #Growth-function mathematically describes how completion time or space grows with the size of the problem (n, think of like #Big-O-Notation).
$$T(n) = n^2 + 3n + 100$$
E.g.,
An inefficient dishwasher that gets all the dry dishes wet.
Let's say it takes 40 seconds to wash one dish,
		 it takes 30 seconds to dry one dish, but also has to dry all the previously washed dishes
the total time for (n) dishes is:
$$T(n) = 40n + 30(1 + 2 + 3... + n) = 15n^2 + 55n$$
With coding in mind, growth functions come from our operations. Operations vary by problem, such as comparisons in sorting being more proficient than swaps as comparisons happen regardless of the order of the data.
E.g.,
$$ T(n) = n^2 + 3n + 100$$
As n grows larger and larger, the only dominant term (AKA the part that grows fastest) matters. For example, in
$$ T(n) = 15n^2 + 55n$$
```java
public void showLots()
{
	for(Lot lot : lots)
	{
		System.out.println(lot);
	}	
}
```
The number of times ==System.out.println(lot)== is run is determined by the size of ==lots==. However the for-loop always runs irrespective of the size of ==lots==. As ==lots== grows in size, ==System.out.println(lot)== runs more. From this information we can form the following equation:
$$T(n) \approx 2n + 1$$
###### The squiggly equals sign is an approximate equals sign. "n" is the number of elements in ==lots==.

## Growth Functions & Asymptotic Complexity

We don't need exact growth functions to compare algorithms, only how it grows as n increases AKA the asymptotic complexity of the growth function.
The dominant term is the part that increases fastest, e.g., in T(n) = 15n<sup>2</sup> + 55n, the term 15n<sup>2</sup> is dominant because it grows much faster as n increases.
$$ T(n) = 15n^2 + 55n -> O(n2)$$
$$ T(n) = 200 + 3n -< O(n)$$
$$ T(n) = 37 -> O(1)$$
We can use #Big-O-Notation to capture the dominant term.
The n<sup>2</sup> term dominates because it grows so much faster.
#Big-O-Notation ignores constants and lower-order terms, capturing only the dominant term's growth rate.

## Common Orders of Complexity

Listed from most to least efficient: 
O(1) ≺ O(log n) ≺ O(n) ≺ O(n log n) ≺ O(n²) ≺ O(n³) ≺ O(2ⁿ)

| Notation   | Name        | Example                         |
| ---------- | ----------- | ------------------------------- |
| O(1)       | Constant    | Determining if a number is even |
| O(log n)   | Logarithmic | Binary search                   |
| O(n)       | Linear      | Linear search                   |
| O(n log n) | Log-linear  | Quick sort, heap sort           |
| O(n²)      | Quadratic   | Insertion sort, selection sort  |
| O(n³)      | Cubic       | Floyd-Warshall algorithm        |
| O(2ⁿ)      | Exponential | Traveling salesman problem      |
## Asymptotic Analysis
#Asymptotic-Analysis focuses on limiting behaviour as n grows, ignoring constant factors that differ between different implementations. A typical binary search could run twice as slow compared to an efficient one, but both are O(log n). The constant factor is called a #hidden-constant and is considered unimportant when n grows arbitrarily large, so Big-O helps us find how scalable the algorithms are at that level of n.

However if you want to distinguish between two algorithms that both have the same Big O (e.g., both insertion sort and bubble sort are O(n<sup>2</sup>)), use tilde notation which retains the constant.
$$Insertion-sort: C(n) \sim (1/4)n^2 comparisons$$
$$Bubble-sort: C(n) \sim (1/2)n^2 comparisons$$
Bubble sort is consistently x2 slower, but both are vastly inferior to O(n log n) sorts, which handle large datasets far better.

## Analysing Time Complexity of Algorithms

Statement types and their complexity:
- Assignment, return, conditional statements: O(1)
- Simple loop: O(n)
- Nested loop: O(n²)
- Triple nested loop: O(n³)
```java
for (int i = 0; i < n; i++)
    x += i;                    // O(1)
```
The above for-loop is running n times with an O(1) body, making it O(n).
A while-loop where a variable doubles each iteration until reaching n runs O(log n), 
as "2<sup>x</sup> ≥ n" means "x ≥ log₂(n)".

A nested for-loop would run n times, as well as the loop its nested in, so the total is O(n<sup>2</sup>). 
```java
int x = 0;
int y = 0;

for (int i=0; i<n; i++)
{
	x = x + 1;
	for (int j=0; j<n; j++)
		{
		y = y - 1;
	}
}
```
Then three-nested loop would be O(n<sup>3</sup>). It just goes on and on!
However if a loop runs a fixed number of times, not depending on n, it's O(1).
```java
for (int i=0; i<n; i++)
{
	x = x + 1;
	for (int j=0; j<10; j++)
	{
		y = y - 1;
	}
}
```

## Comparing Growth Functions
A faster processor doesn't solve complexity. A 10x processor speedup would give us:
- O(n) algorithm can handle 10x more data
- O(2<sum>n</sum>) algorithm can handle only ~3.3x more data
For large datasets using an efficient algorithm is what matters, not processor speed. Inefficient algorithms can lead to memory overflow and failure to solve larger problems.

## Average Case VS. Worst Case Analysis

Some algorithms perform differently on different inputs:
Quick sort example:
- Average case: O(n log n) on random data
- Worst case: O(n²) when data is already sorted or reverse-sorted
Although the worst case is rare in random data, it's common in practice (re-sorting after modifications, sorting in reverse, etc.). If worst cases occur frequently in your application, you need to account for them.

## Software Engineering & Data Structures

As software grows more complex, efficient algorithms and data structures become essential for handling large problems. Understanding the characteristics of each data structure enables you to make appropriate engineering choices during development.