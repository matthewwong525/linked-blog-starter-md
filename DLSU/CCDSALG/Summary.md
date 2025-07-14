- Every assignment statements equates to 1 regardless of how long it is.
- We don't calculate the exact time, we use math functions like asymptotic notations to compute for the frequency count so that later using the notation we know how fast the code is without checking the exact amount of time needed to be completed.
- All `if` statements are counted as 1.
- The larger statement count of blocks is the block that is only considered for counting

---
# Asymptotic Bounds

---
## Order of Growth
- Used to compare and characterize the algorithm’s efficiency.

## Growth Rate Functions
***CLLLQCE***
$O(1)$ - Constant
$O(\log_{2}{n})$ - Logarithmic
$O(n)$ - Linear
$O(n\log_{2}{n})$ - Linear-Logarithmic
$O(n^2)$ - Quadratic
$O(n^3)$ - Cubic
$O(2^n)$ - Exponential

## Asmptotic Notations
### $O$-notation
- Read as **Big-Oh**
- **Asymptotic Behavior** of a function is **Upper Bound**.
- function that **grows no faster than a certain rate $(\leq)$.**
- **FOR EXAMPLE**
	- $$6n^3+2n^2+3n+8\to O(n^3)$$
	- Is the **function** also $O(n^4)$ or $O(n^6)$?
		- Yes, since the function **grows no faster than $(\leq)$**  $n^4$ and $n^6$.
### $\omega$-notation
- Read as **Big-Omega**
- **Asymptotic Behavior** of a function is **Lower Bound**.
- function that **grows at least as fast as a certain rate $(\geq)$**.
- 
- **FOR EXAMPLE**
	- $$6n^3 + 2n^2 + 3n + 8\to O(n^3)$$
	- Is the function also $\Omega{(n^4)}$? **NO**
	- Is the function $\Omega{(n^2)}$ or $\Omega{(n)}$? **YES**
	- The function is $\Omega{(n^c)},c\leq 3$.
### $\Theta$-notation
- Read as **Big-Theta**
- **Asymptotic Behavior** of a function is **Tight Bound**.
- function that grows **precisely at a certain rate**.
- Since the function $6n^3 + 2n^2 + 3n + 8$ is both $O(n^3)$ and $\Omega{(n^3)}$, then it's also $\Theta{(n^3)}$.

## Exercises
1. Is $n^3+20n+5=O(n^2)?$
2. Is $n^3+20n+5=O(n^3)?$
3. Is $n^3+20n+5=O(n^4)?$


## Alternative Ways of Writing Big $O$ of $f(n)$
$$f(n)\text{ is }O(g(n))$$
$$f(n)\in O(g(n))$$
$$f(n) = O(g(n))$$

## General Notations

| Notations     | Name            |
| ------------- | --------------- |
| $n$           | Problem Size    |
| $f(n)$        | Frequency Count |
| $g(n)$        | Growth Rate     |
| $O()$         | Big O           |
| $c$ and $n_0$ | Constants       |


---
# Terms
- Asymptotic Bounds
- Order of Growth
- Growth Rate Functions
- Asymptotic Notations
- Asymptotic Behavior
