# Asymptotic Bounds: A Comprehensive Study Guide

## Introduction to Asymptotic Analysis

### Description

Asymptotic analysis is a method of describing the limiting behavior of a function, particularly in the context of algorithm analysis. It focuses on the growth rate of functions as the input size approaches infinity, ignoring constant factors and smaller inputs. This approach allows us to compare the efficiency of different algorithms, especially when dealing with large datasets. (Page 13, 14, 15)

### Key Terms and Important Points

- **Asymptotic Efficiency:** Refers to how the running time of an algorithm increases with the size of the input as it approaches infinity. It's a way to characterize the algorithm's efficiency and compare it with alternative algorithms. (Page 14, 15)
    
- **Growth Rate:** Describes how the time or space resources required by an algorithm increase as the input size grows.
    
- **Dominant Term:** The term in a function that has the most significant impact on the growth rate as the input size increases. (Page 5)
    
- **Ignoring Constants:** Asymptotic analysis disregards constant factors because they become insignificant as the input size grows very large. (Page 13, 8)
    
- **Small Inputs:** Asymptotic analysis focuses on the behavior of algorithms with large inputs, so the performance on small inputs is generally ignored. (Page 13)
    

## Rate of Growth

### Description

The rate of growth of an algorithm describes how its runtime increases as the input size increases. Understanding the rate of growth is crucial for selecting the most efficient algorithm for a given task, especially when dealing with large datasets. The dominant term in the function representing the algorithm's runtime dictates its overall behavior. (Page 3, 4, 5, 6, 7, 8, 11, 12)

### Key Terms and Important Points

- **Dominant Term:** The term with the fastest growth rate in the function determines the algorithm's behavior. For example, in the expression $3n^3 + 2n^2 + 1$, the term $3n^3$ is dominant. (Page 5)
    
- **Polynomial Dominance:** A polynomial of degree _k_ dominates a polynomial of degree _m_ if and only if _k > m_. For example, $n^7 > n^6 > n^3 > n^2$. (Page 6)
    
- **Exponential Dominance:** Any exponential function of _n_ dominates any polynomial function of _n_. For example, $2^n > n^3$. (Page 5)
    
- **Polynomial vs. Logarithmic:** Any polynomial function of _n_ dominates any logarithmic function of _n_. For example, $n^3 > n \log_2 n > \log_2 n$. (Page 6)
    
- **Logarithmic vs. Constant:** Any logarithmic function of _n_ dominates a constant term. For example, $\log_2 n > c$. (Page 7)
    
- **Order of Growth:** The order of growth is a function of the dominant term of the running time. The coefficient of the dominant term is ignored. For example, $3n^3 + 2n^2 + 1$ has an order of growth of $n^3$. (Page 8)
    
- **Cheat Sheet:** A helpful order of growth hierarchy is: $1 < \log n < n < n \log n < n^2 < n^3 < ... < 2^n < 3^n < ... < n^n$. (Page 7)
    

### Examples of Growth Rate

- $T(n) = 60n^2 + 5n + 1$ grows like $60n^2$. (Page 4)
    
- If $T(n)$ is measured in seconds, then in minutes: $\frac{n^2}{60} + \frac{5n}{60} + \frac{1}{60}$. (Page 4)
    

### Practice Problems

Determine the growth rate corresponding to the following running times: (Page 12)

1. $3n + 5n - 2$
    
2. $6n^2 + 7n + 3$
    
3. $9n^3 + 6n^2 + n + 2$
    

## Growth-Rate Functions

### Description

Growth-rate functions provide a way to categorize algorithms based on how their runtime scales with the input size. These functions are expressed using Big O notation and help in comparing the efficiency of different algorithms. (Page 9, 10)

### Key Terms and Important Points

- **O(1) Constant:** The time requirement is independent of the problem's size. (Page 9)
    
- **$O(\log_2 n)$ Logarithmic:** The time requirement increases slowly as the problem size increases. (Page 9)
    
- **O(n) Linear:** The time requirement increases directly with the size of the problem. (Page 9)
    
- **$O(n \log_2 n)$ Linear-logarithmic:** The time requirement increases more rapidly than linear. (Page 9)
    
- **$O(n^2)$ Quadratic:** The time requirement increases rapidly with the size of the problem. (Page 10)
    
- **$O(n^3)$ Cubic:** The time requirement increases more rapidly than quadratic. (Page 10)
    
- **$O(2^n)$ Exponential:** The time requirement increases too rapidly to be practical for large inputs. (Page 10)
    

## Asymptotic Notations: Big-O, Big-Omega, and Big-Theta

### Description

Asymptotic notations are used to describe the upper, lower, and tight bounds of an algorithm's runtime complexity. These notations help in understanding how an algorithm's performance scales with the input size, especially as it approaches infinity. (Page 13, 15, 16, 28, 40)

### Key Terms and Important Points

- **Big-Oh (O-notation):** Characterizes an upper bound on the asymptotic behavior of a function. It describes the worst-case running time of an algorithm. A function grows no faster than a certain rate, based on the highest-order term. (Page 16, 17, 18, 19, 46, 47)
    
- **Big-Omega (Ω-notation):** Characterizes a lower bound on the asymptotic behavior of a function. It describes the best-case running time of an algorithm. A function grows at least as fast as a certain rate, based on the highest-order term. (Page 28, 29, 30, 66, 67)
    
- **Big-Theta (Θ-notation):** Characterizes a tight bound on the asymptotic behavior of a function. A function grows precisely at a certain rate, based on the highest-order term. It characterizes the rate of growth of a function to within a constant factor from above and below. (Page 40, 41, 42, 43)
    

### Big-Oh (O-notation)

- **Definition:** For a given function $g(n)$, $O(g(n))$ is the set of functions $O(g(n)) = \{f(n) \mid \text{there exist positive constants } c \text{ and } n_0 \text{ such that } 0 \leq f(n) \leq cg(n), \forall n \geq n_0\}$. (Page 48)
    
- **Usage:** Instead of writing $f(n) \in O(g(n))$, we usually write $f(n) = O(g(n))$ and say $f(n)$ is Big-Oh of $g(n)$. (Page 49)
    
- **Example:** Given a function $6n^3 + 2n^2 + 3n + 8$, we write $O(n^3)$. The function is also $O(n^4)$ and $O(n^6)$ because it grows no faster than $n^4$ and $n^6$. The function is $O(n^c)$ for $c \geq 3$. (Page 20, 21, 22, 23, 24, 25, 26, 27)
    

### Big-Omega (Ω-notation)

- **Definition:** For a given function $g(n)$, $\Omega(g(n))$ is the set of functions $\Omega(g(n)) = \{f(n) \mid \text{there exist positive constants } c \text{ and } n_0 \text{ such that } 0 \leq cg(n) \leq f(n), \forall n \geq n_0\}$. (Page 68)
    
- **Example:** The function $6n^3 + 2n^2 + 3n + 8$ grows at least as fast as $n^3$, thus this function is $\Omega(n^3)$. It is not $\Omega(n^4)$, but it is $\Omega(n^2)$ and $\Omega(n)$. The function is $\Omega(n^c)$ for $c \leq 3$. (Page 31, 32, 33, 34, 35, 36, 37, 38, 39)
    

### Big-Theta (Θ-notation)

- **Definition:** $\exists f(n) ((O(f(n)) \land \Omega(f(n))) \rightarrow \Theta(f(n)))$. (Page 44, 45)
    
- **Explanation:** Since the function $6n^3 + 2n^2 + 3n + 8$ is both $O(n^3)$ and $\Omega(n^3)$, then it is also $\Theta(n^3)$. (Page 45)
    

## Formal Definitions and Examples

### Description

Formal definitions of Big-Oh and Big-Omega notations are provided along with examples to illustrate how to determine the asymptotic bounds of functions. These examples demonstrate the process of finding constants _c_ and _n₀_ that satisfy the definitions. (Page 46, 66)

### Big-Oh Examples

- **Example 1:** Is $5n^2 + 150n + 750 = O(n^2)$? (Page 50)
    
    - **Solution:** Find positive constants _c_ and _n₀_ such that $5n^2 + 150n + 750 \leq cn^2, \forall n \geq n_0$. (Page 51, 52)
        
        1. Divide both sides by $n^2$: $5 + \frac{150}{n} + \frac{750}{n^2} \leq c$. (Page 53, 54)
            
        2. Is there a set of possible values for _c_ and _n₀_? Yes. (Page 55, 58)
            
        
        - The condition is satisfied for $n_0 = 1, c = 905$. (Page 56)
            
        - Possible answer: The condition is satisfied for $n_0 = 5, c = 65$. (Page 57)
            
        
    - **Answer:** Yes. (Page 59)
        
    
- **Example 2:** Is $n^3 - 250n^2 = O(n^2)$? (Page 60)
    
    - **Solution:** Find positive constants _c_ and _n₀_ such that $n^3 - 250n^2 \leq cn^2, \forall n \geq n_0$. (Page 61)
        
        1. $n - 250 \leq c$. (Page 62)
            
        2. There is no positive constant _c_ that satisfies the inequality as the LHS of the inequality grows infinitely. (Page 63)
            
        
    - **Answer:** No. (Page 64)
        
    

### Big-Omega Examples

- **Example 3:** Is $5n^2 + 150n + 750 = \Omega(n^2)$? (Page 69)
    
    - **Solution:** Find positive constants _c_ and _n₀_ such that $5n^2 + 150n + 750 \geq cn^2, \forall n \geq n_0$. (Page 70, 71)
        
        1. Divide both sides by $n^2$: $5 + \frac{150}{n} + \frac{750}{n^2} \geq c$. (Page 72, 73)
            
        2. Is there a set of possible values for _c_ and _n₀_? Yes. (Page 74, 76)
            
        
        - The condition is satisfied for $n_0 = 1, c = 5$. (Page 75)
            
        
    - **Answer:** Yes. (Page 77)
        
    
- **Example 4:** Is $n^3 - 250n^2 = \Omega(n^2)$? (Page 78)
    
    - **Solution:** Find positive constants _c_ and _n₀_ such that $n^3 - 250n^2 \geq cn^2, \forall n \geq n_0$. (Page 79)
        
        1. $n - 250 \geq c$. (Page 80)
            
        2. The condition is satisfied for $n_0 = 251, c = 1$. (Page 81)
            
        
    - **Answer:** Yes. (Page 82)
        
    

### Exercises

- **Big-Oh Exercise 1:** (Page 65)
    
    1. Is $n^3 + 20n + 5 = O(n^2)$?
        
    2. Is $n^3 + 20n + 5 = O(n^3)$?
        
    3. Is $n^3 + 20n + 5 = O(n^4)$?
        
    
- **Big-Omega Exercise 2:** (Page 83)
    
    1. Is $n^3 + 20n + 5 = \Omega(n^2)$?
        
    2. Is $n^3 + 20n + 5 = \Omega(n^3)$?
        
    3. Is $n^3 + 20n + 5 = \Omega(n^4)$?
        
    

## Worst, Best, and Average Case Complexities

### Description

The complexity of an algorithm can be analyzed in terms of its worst-case, best-case, and average-case scenarios. These analyses provide different perspectives on the algorithm's performance under various conditions. (Page 84)

### Key Terms and Important Points

- **Worst-Case Complexity:** The function defined by the maximum number of steps taken in any instance of size _n_. It is often associated with Big O notation. (Page 84)
    
- **Best-Case Complexity:** The function defined by the minimum number of steps taken in any instance of size _n_. It is often associated with Big Omega notation. (Page 84)
    
- **Average-Case Complexity:** The function defined by the average number of steps over all instances of size _n_. It is often associated with Big Theta notation. (Page 84)